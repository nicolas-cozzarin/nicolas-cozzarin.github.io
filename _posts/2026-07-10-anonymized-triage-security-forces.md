---
title: "An Anonymized NLP Pipeline for Police Disciplinary Oversight in Córdoba"
date: 2026-07-10
author: "Nicolas Cozzarin"
description: "How I designed and built an on-premise NLP pipeline that anonymizes citizen complaints about police misconduct and suggests categories for human review."
glance:
  - label: "Role"
    text: "AI Product Owner and ML Developer (degree internship), Security Forces Disciplinary Control System, Government of Córdoba, Nov 2025 – Jun 2026"
  - label: "Problem"
    text: "Personal data had to be removed from every complaint by hand, and rare, serious complaints waited in the same queue as routine ones."
  - label: "What I built"
    text: "An irreversible anonymization pipeline (regex, spaCy NER, Microsoft Presidio), then BETO fine-tuned to suggest one of eight categories for a prosecutor to approve or change."
  - label: "Results"
    text: "On a held-out set of 2,189 complaints: 77% recall on institutional violence and an F1 score of 0.72 on gender-based violence. Weighted F1 is 66% overall; this is the second build phase."
  - label: "Constraints"
    text: "Fully on-premise with no external APIs, role-based access and an audit log."
  - label: "Code"
    text: "Not public, because the system runs on government data."
---
### 1. Motivation

In August 2020, a police officer in Córdoba, Argentina, shot and killed Valentino "Blas" Correas, a seventeen-year-old, after his car was stopped at a checkpoint. The case led the province to change how it holds its security forces accountable. The following year, the provincial legislature passed Law 10.731, which created an independent body to investigate and sanction misconduct in the Police, the Anti-Narcotics Force and the Penitentiary Service, outside the chain of command of those institutions.

An oversight body like this depends on the trust of the people who file complaints. In practice, that trust depends on two operational problems.

The first is privacy. Every complaint names people: victims, witnesses, officers under investigation, and sometimes minors. Before anyone can analyze a complaint, compare it with others or use it for statistics, those names have to be removed, in a way that cannot be reversed. Doing this by hand does not scale, and one missed name or a partly redacted address can put someone at risk.

The second is volume and imbalance. Complaints arrive without a category. An operator reads each one, decides what it is about and sends it to the right team. The office receives many more routine complaints, such as general poor performance, than serious ones, such as institutional violence or corruption. With manual triage, the serious cases wait in the same queue as the routine ones.

**Goal:** build an NLP pipeline that removes identifying details from every incoming complaint before a person or a model reads it, and then classifies the anonymized text into the office's official categories, so that investigators spend their time on decisions instead of redaction and sorting.

I worked on this as AI Product Owner and ML Developer during my degree internship with the Coordination of Information Registry and Analysis, the team inside the office that is responsible for this data. I scoped the requirements with the legal and coordination staff, wrote the system specification and built the model. This article describes the design of the full system and what has been measured so far.

---

### 2. Institutional context and related work

Two existing systems were useful references.

**Prometea**, developed for the Public Prosecutor's Office of the City of Buenos Aires, uses AI to read, classify and triage judicial case files. It is the most cited example of AI-assisted triage in the Argentine public sector, and it reports accuracy above 93 percent while keeping the process auditable. It also shows that Argentine institutions can accept this kind of tool.

**PretorIA**, used by the Constitutional Court of Colombia, applies NLP and transformer models to classify large volumes of tutela filings, the Colombian equivalent of a constitutional protection claim. It showed that transformer models can handle dense, informal and legally sensitive text, and that a high court was willing to use one in a process that affects citizens' rights.

In the public documentation I could find, neither system explains in detail how it anonymizes text before classifying it. That is the part of this project I spent the most time on, so I treated it as a separate problem.

---

### 3. Objectives

**General objective:** reduce the time and the errors involved in receiving, protecting and classifying complaints at the Coordination of Information Registry and Analysis.

**Specific objectives:**

1. Anonymize every complaint automatically before analysis, removing names, ID numbers and addresses.
2. Classify each complaint into the office's eight official categories, with an F1 score above 0.70 for each category.
3. Replace manual triage with an automatic suggestion, to reduce the time it takes to send a new complaint to the right area.
4. Keep all data inside government infrastructure: no complaint text or model file leaves it.
5. Train the coordination staff to run the pipeline themselves after handover.

The eight official categories are: conflicto laboral, corrupción, inconductas fuera de servicio, mal desempeño, violencia de género, violencia familiar, violencia institucional and otro.

---

### 4. Data

Each record is a free-text complaint (RESEÑA) written by an operator in informal Spanish, with two labels: **tema**, the main category from the list above, and **subcategoria**, a finer label within that category. A complaint is usually a short paragraph describing an incident, with no fixed structure and with typos, abbreviations and institutional jargon that a general Spanish language model has not seen.

The classes are very unbalanced. Mal desempeño has about 4,000 examples, more than the next two categories together, while the smallest category has fewer than 500 (Figure 1). With this distribution, a model that mostly predicts the majority class can reach a reasonable overall accuracy while missing many of the cases the office most needs to find. For that reason I report results per category, and not only overall accuracy.

*Figure 1: Distribution of complaint categories in the dataset*
![Figure 1](/docs/assets/secfs-theme-distribution.png)

---

### 5. System design and data governance

Before writing any code, I defined who handles the data and what each role can see. This access model drove most of the later design decisions.

| Role | Access |
|---|---|
| Data Operator | Uploads raw complaints and runs the anonymization batch. Never sees classification results. |
| System Administrator | Manages users and defines the categories and examples the model learns from. |
| Prosecutor | Reviews anonymized complaints with the AI suggestion attached, and approves or changes the classification. Never sees raw personal data. |
| Researcher | Queries fully anonymized data for statistics and trend analysis. No access to raw text at any point. |

No role, including mine during development, has permanent access to the raw complaints. Raw text is kept only in a restricted vault used for chain of custody, and every access to it is logged.

**Stack:** Python 3.12 backend, PyTorch with CUDA, Hugging Face Transformers, scikit-learn and pandas. The frontend is React with Tailwind, served separately from the API so that the AI workload can scale independently of the interface.

---

### 6. Anonymization pipeline

Anonymization has to run before any person or model sees the text, and it has to be irreversible. The rules run in a fixed order, because a rule applied too early can break a pattern that a later rule needs: emails first, then account numbers, then phone numbers, then national ID numbers (DNI), then names, then addresses, and finally anything else spaCy's NER model detects. For example, phone numbers are removed before DNI numbers because a phone number contains a run of seven or eight digits that the DNI pattern would also match. In the wrong order, the DNI rule would replace part of the phone number and leave the area code in the text.

{% highlight python %}
import re
import spacy

EMAIL_RE = re.compile(r"[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+")
DNI_RE = re.compile(r"\b\d{7,8}\b")
PHONE_RE = re.compile(r"\b(?:\+54)?\s?9?\s?\d{2,4}[\s.-]?\d{6,8}\b")

def strip_regex_pii(text: str) -> str:
    text = EMAIL_RE.sub("[EMAIL]", text)
    text = PHONE_RE.sub("[TELEFONO]", text)
    text = DNI_RE.sub("[DNI]", text)
    return text
{% endhighlight %}

Names first go through a dictionary of common Argentine first names and surnames, which catches most cases at a low cost. spaCy's named entity recognition handles the rest. Only entity recognition is needed at this stage, so the other spaCy components are disabled to keep it fast:

{% highlight python %}
nlp = spacy.load(
    "es_core_news_lg",
    disable=["tok2vec", "tagger", "parser", "attribute_ruler", "lemmatizer"],
)

def mask_names(text: str) -> str:
    doc = nlp(text)
    for ent in reversed(doc.ents):
        if ent.label_ == "PER":
            text = text[: ent.start_char] + "[PERSONA]" + text[ent.end_char :]
    return text
{% endhighlight %}

Addresses and place names are handled by Microsoft Presidio, which recognizes street names and location patterns better than a general NER model. The link between the raw text and the anonymized text is kept only in the encrypted vault described in section 5, never in the training or inference path.

Every rule is tested against a set of honeypot records with deliberately difficult names, addresses and edge cases, so that false positives and false negatives show up in testing and not in production. The two kinds of error do not have the same cost: a missed name is a privacy breach, while an unnecessary mask only removes some context for the reader. The roadmap (section 14) adds a fixed threshold for acceptable leakage, so that this trade-off can be measured instead of judged case by case.

---

### 7. Modeling plan

Once the text is anonymized, the task is to predict tema and subcategoria from the RESEÑA field. I worked in stages, so that each more complex model had a simpler baseline to beat.

| Step | Task | Output |
|---|---|---|
| 1 | Data inspection | Shape, missing values, class distribution per category |
| 2 | Data cleaning | Lowercasing, noise removal, missing value handling |
| 3 | EDA and feature analysis | Class balance, text length statistics, keyword patterns |
| 4 | scikit-learn baselines | TF-IDF with Logistic Regression, Naive Bayes and SVM, cross-validated |
| 5 | BETO fine-tuning | Spanish BERT fine-tuned with a class-weighted loss |
| 6 | Evaluation and comparison | Accuracy, F1 and confusion matrices side by side |

**Baselines.** Before using a transformer, I set a floor with standard TF-IDF pipelines. If a linear model came close to a fine-tuned BERT model, it would mean that most of the signal is in the vocabulary, and the extra cost of a transformer on the office's hardware would be hard to justify.

{% highlight python %}
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import LogisticRegression
from sklearn.naive_bayes import MultinomialNB
from sklearn.svm import LinearSVC
from sklearn.pipeline import Pipeline
from sklearn.model_selection import cross_val_score

vectorizer = TfidfVectorizer(max_features=20000, ngram_range=(1, 2))

baselines = {
    "logreg": LogisticRegression(max_iter=1000, class_weight="balanced"),
    "naive_bayes": MultinomialNB(),
    "svm": LinearSVC(class_weight="balanced"),
}

for name, model in baselines.items():
    pipe = Pipeline([("tfidf", vectorizer), ("clf", model)])
    scores = cross_val_score(pipe, X_train, y_train, cv=5, scoring="f1_weighted")
    print(name, scores.mean())
{% endhighlight %}

---

### 8. Classification model

For the main model I fine-tuned BETO, a Spanish BERT model, on the anonymized complaints. The main difficulty is the class imbalance described in section 4: without a correction, the model learns to favour the majority class, and its overall accuracy hides poor results on the smaller categories.

To correct this, I compute class weights from the training distribution and use them in a weighted cross-entropy loss inside the Hugging Face Trainer:

{% highlight python %}
import numpy as np
import torch
from sklearn.utils.class_weight import compute_class_weight
from transformers import Trainer

class_weights = compute_class_weight(
    class_weight="balanced",
    classes=np.unique(y_train),
    y=y_train,
)
class_weights = torch.tensor(class_weights, dtype=torch.float)

class WeightedTrainer(Trainer):
    def compute_loss(self, model, inputs, return_outputs=False, **kwargs):
        labels = inputs.pop("labels")
        outputs = model(**inputs)
        logits = outputs.logits
        loss_fct = torch.nn.CrossEntropyLoss(weight=class_weights.to(logits.device))
        loss = loss_fct(logits, labels)
        return (loss, outputs) if return_outputs else loss
{% endhighlight %}

To predict tema and subcategoria together, there are two options. A multi-task model shares one BETO backbone with two classification heads. It is cheaper to run, but the two tasks influence each other during training. Two separate models cost more compute, and an error in one task does not affect the other. The office has a single GPU workstation, so the current version uses the multi-task setup, and two separate models are planned as a comparison when more compute is available.

Each prediction returns a score for every category, so the prosecutor can see whether the top suggestion was clear or close:

{% highlight json %}
{
  "complaint_id": "uuid-12345",
  "status": "pending_human_verification",
  "classification": {
    "tema": {
      "ai_suggested": "mal_desempeno",
      "human_validated": null,
      "confidence": 0.87,
      "all_scores": {
        "mal_desempeno": 0.87,
        "violencia_institucional": 0.06,
        "conflicto_laboral": 0.04,
        "otro": 0.03
      }
    }
  }
}
{% endhighlight %}

---

### 9. Human review

No classification is final without a person. The prosecutor sees the anonymized text next to the suggested category and its scores, and approves or changes it. Every change is logged and added to a table of corrected labels, which becomes training data for the next round of fine-tuning. Model errors are collected as part of the normal work, without a separate relabeling project.

For this office, review is a requirement. A wrong category on a complaint about institutional violence can delay an investigation, and the office was created to be more transparent than the institutions it oversees, so its own tools have to be open to checking.

One risk with this design is that reviewers start to accept suggestions without reading the complaint carefully, especially when the score is high. Tracking how often prosecutors change a suggestion, by category and by score, is a simple way to see whether this happens.

---

### 10. Deployment and data sovereignty

The office required that no complaint text, raw or anonymized, leave government infrastructure. The plan is to run the whole pipeline on a GPU workstation inside the office or in the province's data centre, with no need for internet access once deployed. This excluded cloud APIs for inference, and it is the reason I used an open model that runs locally, BETO, instead of a larger hosted model that would have required sending complaint text outside the province.

---

### 11. Results

These are partial results, on a held-out set of 2,189 complaints that were not used for training.

- Accuracy: 66 percent
- Weighted average F1 score: 66 percent

The weighted average is below the project's target, and it hides differences between categories:

- Mal desempeño, the majority class, reaches 87 percent precision: when the model assigns this label, it is usually right.
- Violencia institucional reaches 77 percent recall: the model finds most of the real cases in this category.
- Violencia de género reaches an F1 score of 0.72, above the 0.70 target.

For a triage tool, recall on the serious categories matters more than precision, because a person reviews every suggestion. A false alarm costs a prosecutor a few minutes; a missed case may stay at the back of the queue.

*Figure 2: Confusion matrix across the eight official categories*
![Figure 2](/docs/assets/secfs-confusion-matrix.png)

*Figure 3: Training loss and validation loss over training steps*
![Figure 3](/docs/assets/secfs-loss-curve.png)

*Figure 4: Precision, recall and F1 by category*
![Figure 4](/docs/assets/secfs-metrics-per-class.png)

---

### 12. Discussion

**Overfitting.** In Figure 3, the training loss keeps going down while the validation loss reaches a minimum and then rises. The model starts to memorize training examples instead of generalizing. The next steps are earlier stopping, stronger regularization and more training data for the smaller categories.

**Overlapping categories.** Most errors in Figure 2 are between violencia familiar and violencia de género. Many cases of gender-based violence in this data happen inside a family, and the complaint texts often do not separate the two clearly. Part of this error comes from the category definitions rather than from the model. Two options are to allow a complaint to carry both labels, or to agree with the legal team on a written rule for cases that fit both.

**Limits of class weighting.** Weighting the loss improves the results on the smaller categories, but it cannot replace missing examples. The most direct improvement is more labeled data for the categories that matter most for oversight, which are also the ones that occur least often. The corrections collected through human review (section 9) are one way to build this data over time.

---

### 13. Legal and governance relevance

A recurring question about AI in public institutions is how to get the benefits of automated triage without creating an opaque system inside a body whose job is accountability. The main design choices in this project, anonymization, mandatory human review and no external servers, all come from that question.

The anonymization requirement comes from Argentina's Personal Data Protection Law (Law 25.326). The human review requirement comes from the office's mandate under Law 10.731 to be more transparent than the institutions it investigates. Both were conditions for building the classifier, set in the first design meetings.

The EU AI Act is a useful comparison. It classifies some AI systems used in law enforcement as high risk, for example systems that evaluate the reliability of evidence or support profiling in an investigation, and it requires human oversight and logging for them (Article 14 and Annex III). Argentina is not bound by the Act, and this system is not one of the tools it describes. Still, the Act reaches the same requirements this project had for its own reasons: human review of each decision, an audit trail and no fully automatic decisions. This suggests that these requirements are a common baseline wherever AI is used in decisions by the state about individuals.

The data sovereignty requirement follows the same logic. The data concerns both police officers and vulnerable complainants, and the province did not accept processing it on infrastructure it does not control. In practice, this meant choosing an open model that runs locally over a more capable hosted one, and building the audit log before the dashboard. The cost of this choice is real: a smaller local model may perform worse than a large hosted one, and the province accepted that trade-off for this data.

---

### 14. Roadmap

The specification includes these next steps:

- An urgency scale from P1 to P5 on top of the category, so the most time-sensitive complaints are reviewed first.
- A bias monitoring dashboard that checks whether predictions correlate with demographic or geographic patterns that should not affect a classification.
- A fixed threshold for acceptable personal data leakage, so that the anonymization audit has a number to test against.
- Export of the model to ONNX for faster CPU inference on the office's hardware.
- A documented REST API (OpenAPI and Swagger), so the office's intake system can call the pipeline directly.

---

### 15. References

- Law 10.731, Province of Córdoba, Argentina. Creation of the disciplinary control system for the security forces.
- Law 25.326, National Personal Data Protection Law, Argentina.
- Prometea, Public Prosecutor's Office of the City of Buenos Aires (Ministerio Público Fiscal de la CABA).
- PretorIA, Constitutional Court of Colombia.
- Cañete, J. et al., "Spanish Pre-Trained BERT Model and Evaluation Data," PML4DC at ICLR, 2020. (BETO)
- Wolf, T. et al., "Transformers: State-of-the-Art Natural Language Processing," Hugging Face, 2020.
- European Union, Artificial Intelligence Act, Article 14 and Annex III, on high-risk classification and human oversight for law enforcement AI systems.
- Microsoft Presidio, data protection and anonymization SDK.
- spaCy, es_core_news_lg Spanish language model.

I developed this project during my internship as AI Product Owner and ML Developer with the Coordination of Information Registry and Analysis, part of the Security Forces Disciplinary Control System of the Province of Córdoba, Argentina, between November 2025 and June 2026. The results above are partial: the classifier is in its second build phase, and deployment on government infrastructure is planned for the next phase. Because the system processes real and sensitive government data, the source code is not public. This article describes the design and the method.
