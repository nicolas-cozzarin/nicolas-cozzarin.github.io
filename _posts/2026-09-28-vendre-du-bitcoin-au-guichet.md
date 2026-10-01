---
title: "Vendre du Bitcoin au guichet : lancer un produit crypto réglementé dans des agences suisses"
date: 2026-09-28
author: "Nicolas Cozzarin"
lang: fr
ref: crypto-branch-launch
description: "Comment j'ai piloté le lancement de la vente de cryptomonnaies dans les agences d'une société suisse de transfert d'argent : le partenaire, le produit, la conformité et ce que je ferais autrement."
glance:
  - label: "Rôle"
    text: "Product Owner, Union of Financial Corners SA, Genève"
  - label: "Produit"
    text: "Les clients achètent du Bitcoin ou de l'Ethereum en espèces au guichet et le reçoivent sur leur propre wallet. Ils peuvent aussi en vendre."
  - label: "Mon travail"
    text: "Besoins, choix du partenaire crypto, backlog avec les développeurs externes, tests, procédures en agence et formation du personnel."
  - label: "Le plus difficile"
    text: "Reconnaître chaque client d'une agence à l'autre et garder chaque contrôle d'identité et chaque document prêts pour un audit."
  - label: "Résultats"
    text: "En service dans toutes les agences de Genève, Lausanne, Berne et Zurich. Les clients reviennent régulièrement pour acheter et vendre, les audits ont trouvé les documents demandés, et le service est en cours d'extension à des bornes partenaires dans toute la Suisse."
---

### 1. Contexte

Union of Financial Corners est une société de transfert d'argent et de change en Suisse. La plus grande partie de son activité se fait en agence : les gens viennent au guichet pour envoyer de l'argent à l'étranger avec Western Union ou pour changer des devises. C'est une activité réglementée, soumise aux règles de la FINMA et à la loi suisse sur le blanchiment d'argent.

Il y avait trois raisons d'ajouter la crypto. La loi suisse sur la crypto avait changé, ce qui permettait de la proposer dans un cadre légal clair. Les clients la demandaient au guichet. Et l'entreprise cherchait une nouvelle source de revenus, à côté des transferts et du change.

Mon travail était d'en faire un produit que le personnel puisse vendre tous les jours, dans chaque agence, sans créer de risque de conformité.

---

### 2. Comment ça marche pour le client

Du côté du client, c'est simple :

1. Le client vient au guichet et paie en espèces.
2. Il montre le QR code de son propre wallet et prouve que ce wallet lui appartient.
3. Le personnel scanne le QR code et le Bitcoin ou l'Ethereum est envoyé sur ce wallet.

Les clients peuvent aussi faire l'inverse et vendre de la crypto contre des espèces.

Derrière ces trois étapes, il y a beaucoup plus : identifier le client, vérifier le montant par rapport aux limites, décider quel niveau de KYC s'applique, enregistrer les documents et envoyer l'ordre au fournisseur crypto. L'objectif était de garder le passage au guichet court, sans permettre de sauter aucun de ces contrôles.

---

### 3. Mon rôle

J'étais le Product Owner de ce lancement. Concrètement, cela voulait dire :

- rédiger les besoins, du parcours client au guichet jusqu'aux règles de conformité ;
- choisir le partenaire, un fournisseur crypto suisse, et être son interlocuteur des premiers échanges jusqu'au lancement ;
- gérer le backlog avec les développeurs externes qui ont construit l'intégration ;
- tester le parcours complet avant le lancement ;
- rédiger les procédures pour les agences ;
- former le personnel des agences.

Le projet a duré environ dix mois, du début jusqu'au lancement.

---

### 4. Travailler avec le partenaire et les développeurs

La crypto elle-même venait d'un partenaire, un fournisseur crypto suisse, et notre système devait fonctionner avec le sien. Choisir ce partenaire a été l'une de mes premières tâches. Ensuite, je suis resté son interlocuteur pendant tout le projet et j'ai suivi avec lui l'intégration et les tests.

Les développeurs étaient eux aussi externes. J'écrivais les user stories, je tenais le backlog à jour et je testais chaque livraison en fonction de la réalité d'une agence, avec un client qui attend au guichet.

---

### 5. La conformité au cœur du produit

C'était le cœur du projet. Avant le lancement, le produit devait démontrer que les règles de la FINMA et les exigences de lutte contre le blanchiment étaient respectées, et il nous fallait l'approbation de la FINMA.

Concrètement, le produit devait gérer :

- l'identification du client, avec un niveau de KYC qui dépend du montant ;
- les limites de montant ;
- l'enregistrement de chaque contrôle d'identité et de chaque document ;
- les procédures anti-blanchiment pour le personnel ;
- le suivi de chaque client dans toutes les agences.

Le plus difficile était ce dernier point, avec les documents. Un client peut acheter à Genève un jour et à Lausanne le lendemain. Si chaque agence ne voit que ses propres transactions, les limites et les niveaux de KYC n'ont plus beaucoup de sens. Il fallait donc reconnaître le même client dans n'importe quelle agence, et garder tous ses documents enregistrés de façon à pouvoir les présenter à tout moment en cas d'audit.

J'étais responsable de ce suivi et de la vérification qu'il était fait correctement, y compris en dehors du cas normal, par exemple avec un client qui revient dans une autre ville.

---

### 6. Le déploiement dans les agences

Nous avons lancé le service dans toutes nos agences de Genève, Lausanne, Berne et Zurich. Dans chaque agence, le personnel devait connaître le nouveau parcours, les nouvelles procédures et surtout pourquoi les étapes de conformité étaient importantes.

C'est la formation que je changerais. J'ai expliqué le produit comme je le comprenais, avec tous les détails des règles. Pour beaucoup d'agents, c'était trop d'un coup. La prochaine fois, je partirais des bases et j'expliquerais avec des mots très simples les quelques points qui comptent vraiment : qui est le client, est-ce que le wallet est bien à lui, quelle limite s'applique et quel document doit être enregistré. Le reste peut venir ensuite.

---

### 7. Résultats

Je n'ai pas de chiffres exacts à partager, mais les signes étaient clairs :

- Les clients revenaient régulièrement pour acheter de la crypto, et aussi pour en vendre.
- Lors des audits, nous avions les documents demandés.
- Le service fonctionne toujours aujourd'hui.
- Il est en cours d'extension à des bornes de partenaires tiers dans toute la Suisse.

---

### 8. Ce que j'en retiens

- Dans une activité réglementée, les exigences de conformité font partie de la conception du produit. Dans ce projet, le plus difficile était une exigence de conformité : reconnaître chaque client dans toutes les agences et garder ses documents prêts pour un audit.
- La prochaine fois, je formerais le personnel en deux temps : d'abord les quelques points qui comptent au guichet, ensuite le détail des règles.
