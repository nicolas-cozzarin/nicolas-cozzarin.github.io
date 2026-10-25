---
title: "Checking the EU AI Act in the Deployment Pipeline: My Final Degree Project"
date: 2026-10-25
author: "Nicolas Cozzarin"
lang: en
ref: ai-act-validator
description: "A validator that checks five EU AI Act controls on every new version of a credit model, measures fairness, and blocks the deployment when a rule fails."
glance:
  - label: "Context"
    text: "Final degree project (prototype), BSc in Artificial Intelligence and Robotics, Universidad Siglo XXI, 2026. I worked alone and played the three Scrum roles."
  - label: "Problem"
    text: "AI models are checked for compliance by hand, at the end of development, and every new version repeats the whole review."
  - label: "What I built"
    text: "A validator that runs as a step of the client's GitLab CI pipeline. It turns the card of each model version into an RDF graph, measures fairness with Fairlearn, checks five EU AI Act controls with SHACL rules in GraphDB, and blocks the deployment if one fails."
  - label: "Status"
    text: "Working prototype. In a first run, version 1 of a test credit model passed the five rules and version 2 was blocked by the fairness rule. The evaluation against manual review takes place in November 2026."
  - label: "Prototype"
    text: "See the three screens with data from a real run (in Spanish)"
    url: "https://nicolas-cozzarin.github.io/validador-prototipo/"
---

### 1. The problem

The EU AI Act asks providers of high-risk AI systems to document their models, keep event logs, plan human oversight and examine their data for bias. A model that decides if a person can get credit is high-risk (Annex III, point 5(b)). For credit models, these obligations apply from December 2027.

Models change fast. A team can put a new version in production in a few hours. Compliance checks do not follow that pace: someone reviews the documentation with a checklist at the end of development, and the whole review starts again with each new version. Two auditors can read the same criterion differently, and later it is hard to know why a version was approved.

There are tools that help. Model Cards, Datasheets and the TechOps templates give a structure for the documentation, but people fill them in by hand and nothing checks them. Governance platforms such as Credo AI or OneTrust know the AI Act but work with questionnaires and human review. Open Policy Agent can block a deployment, but it has no AI Act rules. I wanted to put the two together: AI Act controls that run on their own in the pipeline and can stop a deployment.

The case is modelled. ComplianceTech Europa is a fictional consultancy in Paris that audits AI models for banks, and Banco Aurora is a fictional client with a credit model. Their details are my assumptions, and I say so in the project.

---

### 2. What the validator does

When the bank publishes a new version of its credit model, its GitLab CI pipeline runs two jobs before the deployment:

1. **fairness-measure** computes, with Fairlearn, the difference between the approval rates of men and women (demographic parity difference).
2. **compliance-check** sends the card of the version and the fairness result to GraphDB, which checks them against five SHACL rules.

If the five rules pass, the deployment continues. If one fails, the job fails, the deployment does not run, and the report says which rule failed, the value found, the value expected and the article of the AI Act. If GraphDB does not answer, the job also fails, so that no version goes out without being checked.

Every run is saved in a history, including the blocked ones, with its date, its result for each rule and the deployment decision.

---

### 3. The five rules

| Rule | AI Act | What it checks on the card |
|---|---|---|
| R1 | Art. 6(2) and Annex III, 5(b) | The declared risk category matches the purpose. A creditworthiness model is high-risk. |
| R2 | Art. 11 and Annex IV | Four fields are filled in: intended purpose, training data, accuracy metrics, known limitations. |
| R3 | Art. 12 | Automatic event logging is declared, with where the logs are stored. |
| R4 | Art. 14 | A human oversight measure and a responsible person are declared. |
| R5 | Art. 10(2)(f) and (g) | The demographic parity difference by sex is 0.10 or less. |

These rules cover only part of each obligation, and I want to be clear about where they stop:

- R2, R3 and R4 check what the card **declares**. They do not check that the documentation is good, that the logs exist or that someone really supervises the model. That evidence stays with the human auditors.
- The AI Act asks to examine and correct bias, but it does not say how to measure it. The metric and the 0.10 limit are my choice for the case, so that all auditors measure the same way. A low value does not prove that a model is fair: Hardt et al. (2016) showed with credit scores that equal approval rates can mean approving people who will not repay in one group and refusing people who would in another. So R5 works as a warning signal.

---

### 4. Design choices

**A graph instead of tables.** The rules test relations between data. For example, the purpose of the model implies a risk category, and R1 compares it with the category the card declares. In RDF this is a path in the graph, and SHACL rules run directly on it. I adapted the structure of the card from the TechOps templates.

**Keep the blocked versions.** GraphDB can validate SHACL by itself, but then it refuses to store data that does not conform. That would remove the non-compliant versions from the history, and those are the ones an auditor most needs to see. So the validation runs as a separate step, and the history lives in a repository without SHACL. This is where my roles as product owner and developer met: the design needed something the tool did not do by default.

**No personal data in the graph.** The fairness measure runs inside the client's pipeline. Only the result reaches the graph: the rates by group and the difference.

**Rules with a version.** Each report says which version of the rules was used. The plan is that the consultancy publishes new rules when the law changes, without the client touching its pipeline.

---

### 5. The screens

I designed the screens in Figma and built them with Streamlit. There are three:

- **Executions**, with two tabs. *Result* shows the model, the version, a table with each rule (value found, value expected, legal basis, result), the approval rates of men and women, and a button to download the SHACL report. *History* shows one row per validation, with the parity value against the limit, the origin (pipeline or manual) and the SPARQL query that builds the table.
- **Manual validation**, where an auditor can check a card without deploying anything.
- **Integration**, with the four steps a client follows to connect its pipeline.

**[See the prototype screens](https://nicolas-cozzarin.github.io/validador-prototipo/)** (in Spanish). It is a static view with the data of a real run. The full prototype, with live validation, runs in Docker: GraphDB, Streamlit and Caddy for HTTPS.

---

### 6. First run

On 25 October 2026 I ran the same steps as the bank's pipeline on my computer, against GraphDB 10.8, with two versions of a test credit model trained with scikit-learn:

- **Version 1** approves 91% of men and 93% of women. Difference: 0.01. The five rules pass and the deployment is authorised.
- **Version 2** was trained with a bias on purpose. It approves 96% of men and 82% of women. Difference: 0.15. R5 fails, the deployment is blocked, and the report points to Article 10.

The data comes from the public *Default of Credit Card Clients* dataset (30,000 clients of a bank in Taiwan, 2005). It is used to test the mechanism, not to say anything about credit in Europe.

---

### 7. How I will evaluate it

This first run shows that the mechanism works. It does not show that the validator is reliable. For that I prepared a test, which runs in November 2026:

- 20 model cards built on purpose: 10 that pass the five rules and 10 that break at least one. Each rule is broken at least twice. There are edge cases, such as parity values of 0.09, 0.10 and 0.12, and a card with two problems.
- The expected result of each card is written in a separate file before running the validator.
- Goals: zero compliant verdicts for the 10 cards that break a rule (the serious error, because it lets a violation through), and at most one wrong block among the 10 that comply.
- Time: I also review the same 20 cards by hand with a checklist and compare the median minutes per card. The goal is at least 50% less time, for these five controls only, not for a full audit.

The limits are real. The organisation is modelled, and I build the cards, write the rules and time both reviews, which can bias the result.

---

### 8. What I take from it

The hardest part was separating what the law says from my technical reading of it. For each rule I wrote the article, what it checks on the card and an example of a violation, so that anyone can trace a blocked deployment back to the text.

Next steps after the degree: a version that runs on the client's own servers, publishing new rules without touching the client's pipeline, and a downloadable report that can serve as evidence. The rules can also grow. I started with biases the law protects, because an error there can lead to a fine, but other biases, such as speciesism in AI systems (Hagendorff et al., 2023), could be added the same way.

**Stack:** Python 3.12, RDF and Turtle, SHACL, rdflib, pySHACL, GraphDB 10.8, Fairlearn, scikit-learn, GitLab CI, Streamlit, Docker, Caddy, Figma.
