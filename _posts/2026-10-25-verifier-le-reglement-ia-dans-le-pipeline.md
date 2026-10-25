---
title: "Vérifier le Règlement européen sur l'IA dans le pipeline de déploiement : mon projet de fin d'études"
date: 2026-10-25
author: "Nicolas Cozzarin"
lang: fr
ref: ai-act-validator
description: "Un validateur qui vérifie cinq contrôles du Règlement européen sur l'IA sur chaque nouvelle version d'un modèle de crédit, mesure l'équité et bloque le déploiement quand une règle n'est pas respectée."
glance:
  - label: "Contexte"
    text: "Projet de fin d'études (prototype), licence en intelligence artificielle et robotique, Universidad Siglo XXI, 2026. J'ai travaillé seul et tenu les trois rôles de Scrum."
  - label: "Problème"
    text: "La conformité des modèles d'IA est vérifiée à la main, en fin de développement, et chaque nouvelle version repart de zéro."
  - label: "Ce que j'ai construit"
    text: "Un validateur qui tourne comme une étape du pipeline GitLab CI du client. Il transforme la fiche de chaque version du modèle en graphe RDF, mesure l'équité avec Fairlearn, vérifie cinq contrôles du Règlement avec des règles SHACL dans GraphDB et bloque le déploiement si l'un d'eux échoue."
  - label: "État"
    text: "Prototype fonctionnel. Lors d'une première exécution, la version 1 d'un modèle de crédit de test a passé les cinq règles et la version 2 a été bloquée par la règle d'équité. L'évaluation face à la revue manuelle a lieu en novembre 2026."
  - label: "Prototype"
    text: "Voir les trois écrans avec les données d'une exécution réelle (en espagnol)"
    url: "https://nicolas-cozzarin.github.io/validador-prototipo/"
---

### 1. Le problème

Le Règlement européen sur l'IA demande aux fournisseurs de systèmes à haut risque de documenter leurs modèles, de conserver des journaux d'événements, de prévoir un contrôle humain et d'examiner leurs données pour détecter les biais. Un modèle qui décide si une personne peut obtenir un crédit est à haut risque (annexe III, point 5, b). Pour les modèles de crédit, ces obligations s'appliquent à partir de décembre 2027.

Les modèles changent vite. Une équipe peut mettre une nouvelle version en production en quelques heures. Les contrôles de conformité ne suivent pas ce rythme : quelqu'un relit la documentation avec une checklist à la fin du développement, et toute la revue recommence à chaque nouvelle version. Deux auditeurs peuvent lire le même critère différemment, et plus tard il est difficile de savoir pourquoi une version a été validée.

Des outils existent. Les Model Cards, les Datasheets et les modèles TechOps donnent une structure à la documentation, mais on les remplit à la main et rien ne les vérifie. Les plateformes de gouvernance comme Credo AI ou OneTrust connaissent le Règlement, mais fonctionnent avec des questionnaires et une revue humaine. Open Policy Agent peut bloquer un déploiement, mais n'a pas de règles liées au Règlement sur l'IA. J'ai voulu réunir les deux : des contrôles du Règlement qui tournent seuls dans le pipeline et peuvent arrêter un déploiement.

Le cas est modélisé. ComplianceTech Europa est un cabinet de conseil fictif à Paris qui audite des modèles d'IA pour des banques, et Banco Aurora est un client fictif avec un modèle de crédit. Leurs détails sont mes hypothèses, et je le dis dans le projet.

---

### 2. Ce que fait le validateur

Quand la banque publie une nouvelle version de son modèle de crédit, son pipeline GitLab CI lance deux jobs avant le déploiement :

1. **fairness-measure** calcule avec Fairlearn l'écart entre les taux d'acceptation des hommes et des femmes (différence de parité démographique).
2. **compliance-check** envoie la fiche de la version et le résultat d'équité à GraphDB, qui les vérifie avec cinq règles SHACL.

Si les cinq règles sont respectées, le déploiement continue. Si l'une échoue, le job échoue, le déploiement ne se lance pas, et le rapport indique la règle en cause, la valeur trouvée, la valeur attendue et l'article du Règlement. Si GraphDB ne répond pas, le job échoue aussi, pour qu'aucune version ne parte sans être vérifiée.

Chaque exécution est enregistrée dans un historique, y compris celles qui ont été bloquées, avec sa date, le résultat de chaque règle et la décision de déploiement.

---

### 3. Les cinq règles

| Règle | Règlement sur l'IA | Ce qu'elle vérifie dans la fiche |
|---|---|---|
| R1 | Art. 6, § 2, et annexe III, 5, b | La catégorie de risque déclarée correspond à la finalité. Un modèle de solvabilité est à haut risque. |
| R2 | Art. 11 et annexe IV | Quatre champs sont remplis : finalité prévue, données d'entraînement, métriques de précision, limites connues. |
| R3 | Art. 12 | L'enregistrement automatique des événements est déclaré, avec le lieu de stockage des journaux. |
| R4 | Art. 14 | Une mesure de contrôle humain et une personne responsable sont déclarées. |
| R5 | Art. 10, § 2, f et g | La différence de parité démographique par sexe est inférieure ou égale à 0,10. |

Ces règles ne couvrent qu'une partie de chaque obligation, et je veux être clair sur leurs limites :

- R2, R3 et R4 vérifient ce que la fiche **déclare**. Elles ne vérifient pas que la documentation est bonne, que les journaux existent ou que quelqu'un supervise vraiment le modèle. Ces preuves restent du ressort des auditeurs.
- Le Règlement demande d'examiner et de corriger les biais, mais il ne dit pas comment les mesurer. La métrique et le seuil de 0,10 sont mon choix pour le cas, afin que tous les auditeurs mesurent de la même façon. Une valeur basse ne prouve pas qu'un modèle est équitable : Hardt et al. (2016) ont montré, sur des scores de crédit, que des taux d'acceptation égaux peuvent conduire à accepter dans un groupe des personnes qui ne rembourseront pas et à refuser dans un autre des personnes qui rembourseraient. R5 sert donc de signal d'alerte.

---

### 4. Choix de conception

**Un graphe plutôt que des tables.** Les règles testent des relations entre les données. Par exemple, la finalité du modèle implique une catégorie de risque, et R1 la compare à celle que déclare la fiche. En RDF, c'est un chemin dans le graphe, et les règles SHACL s'appliquent directement dessus. J'ai adapté la structure de la fiche à partir des modèles TechOps.

**Garder les versions bloquées.** GraphDB peut valider SHACL tout seul, mais il refuse alors d'enregistrer les données non conformes. Les versions non conformes disparaîtraient de l'historique, alors que ce sont celles qu'un auditeur a le plus besoin de voir. La validation se fait donc dans une étape séparée, et l'historique est stocké dans un dépôt sans SHACL. C'est là que mes rôles de Product Owner et de développeur se sont croisés : la conception demandait quelque chose que l'outil ne faisait pas par défaut.

**Pas de données personnelles dans le graphe.** La mesure d'équité tourne dans le pipeline du client. Seul le résultat arrive dans le graphe : les taux par groupe et l'écart.

**Des règles versionnées.** Chaque rapport indique la version des règles utilisée. L'idée est que le cabinet publie de nouvelles règles quand la loi change, sans que le client touche à son pipeline.

---

### 5. Les écrans

J'ai conçu les écrans dans Figma et je les ai développés avec Streamlit. Il y en a trois :

- **Exécutions**, avec deux onglets. *Résultat* montre le modèle, la version, un tableau avec chaque règle (valeur trouvée, valeur attendue, base légale, résultat), les taux d'acceptation des hommes et des femmes, et un bouton pour télécharger le rapport SHACL. *Historique* montre une ligne par validation, avec la parité comparée au seuil, l'origine (pipeline ou manuelle) et la requête SPARQL qui construit le tableau.
- **Validation manuelle**, où un auditeur peut vérifier une fiche sans rien déployer.
- **Intégration**, avec les quatre étapes qu'un client suit pour connecter son pipeline.

**[Voir les écrans du prototype](https://nicolas-cozzarin.github.io/validador-prototipo/)** (en espagnol). C'est une vue statique avec les données d'une exécution réelle. Le prototype complet, avec la validation en direct, tourne dans Docker : GraphDB, Streamlit et Caddy pour le HTTPS.

---

### 6. Première exécution

Le 25 octobre 2026, j'ai lancé sur mon ordinateur les mêmes étapes que le pipeline de la banque, avec GraphDB 10.8 et deux versions d'un modèle de crédit de test entraînées avec scikit-learn :

- **Version 1** : elle accepte 91 % des hommes et 93 % des femmes. Écart : 0,01. Les cinq règles passent et le déploiement est autorisé.
- **Version 2** : entraînée exprès avec un biais. Elle accepte 96 % des hommes et 82 % des femmes. Écart : 0,15. R5 échoue, le déploiement est bloqué et le rapport renvoie à l'article 10.

Les données viennent du jeu public *Default of Credit Card Clients* (30 000 clients d'une banque de Taïwan, 2005). Il sert à tester le mécanisme, pas à tirer des conclusions sur le crédit en Europe.

---

### 7. Comment je vais l'évaluer

Cette première exécution montre que le mécanisme fonctionne. Elle ne montre pas que le validateur est fiable. Pour cela, j'ai préparé un test, qui a lieu en novembre 2026 :

- 20 fiches construites exprès : 10 qui respectent les cinq règles et 10 qui en enfreignent au moins une. Chaque règle est enfreinte au moins deux fois. Il y a des cas limites, comme des parités de 0,09, 0,10 et 0,12, et une fiche avec deux problèmes.
- Le résultat attendu de chaque fiche est noté dans un fichier séparé avant de lancer le validateur.
- Objectifs : aucune fiche non conforme acceptée parmi les 10 qui enfreignent une règle (c'est l'erreur grave, car elle laisse passer une infraction), et au plus un blocage à tort parmi les 10 conformes.
- Temps : je vérifie aussi les 20 fiches à la main avec une checklist et je compare la médiane de minutes par fiche. L'objectif est au moins 50 % de temps en moins, pour ces cinq contrôles seulement, pas pour un audit complet.

Les limites existent. L'organisation est modélisée, et c'est moi qui construis les fiches, écris les règles et chronomètre les deux revues, ce qui peut biaiser le résultat.

---

### 8. Ce que j'en retiens

Le plus difficile a été de séparer ce que dit la loi de ma lecture technique. Pour chaque règle, j'ai noté l'article, ce qu'elle vérifie dans la fiche et un exemple d'infraction, pour que chacun puisse remonter d'un déploiement bloqué jusqu'au texte.

Prochaines étapes après le diplôme : une version qui tourne sur les serveurs du client, la publication de nouvelles règles sans toucher au pipeline du client, et un rapport téléchargeable qui puisse servir de preuve. Les règles peuvent aussi s'étendre. J'ai commencé par les biais que la loi protège, parce qu'une erreur peut y entraîner une amende, mais d'autres biais, comme le spécisme dans les systèmes d'IA (Hagendorff et al., 2023), pourraient être ajoutés de la même façon.

**Technologies :** Python 3.12, RDF et Turtle, SHACL, rdflib, pySHACL, GraphDB 10.8, Fairlearn, scikit-learn, GitLab CI, Streamlit, Docker, Caddy, Figma.
