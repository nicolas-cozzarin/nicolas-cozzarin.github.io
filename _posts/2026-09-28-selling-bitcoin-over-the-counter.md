---
title: "Selling Bitcoin Over the Counter: Launching a Regulated Crypto Product in Swiss Branches"
date: 2026-09-28
author: "Nicolas Cozzarin"
lang: en
ref: crypto-branch-launch
description: "How I led the launch of crypto sales in the branches of a Swiss money transfer company: the partner, the product, the compliance work and what I would do differently."
glance:
  - label: "Role"
    text: "Product owner, Union of Financial Corners SA, Geneva"
  - label: "Product"
    text: "Clients buy Bitcoin or Ethereum with cash at the counter and receive it in their own wallet. They can also sell."
  - label: "What I did"
    text: "Requirements, choice of the crypto partner, backlog with the external developers, testing, branch procedures and staff training."
  - label: "Hardest part"
    text: "Recognising each client across branches and keeping every ID check and document ready for an audit."
  - label: "Results"
    text: "Live in all branches in Geneva, Lausanne, Bern and Zurich. Clients come back regularly to buy and sell, audits found the documents they asked for, and the service is being extended to partner kiosks across Switzerland."
---

### 1. Context

Union of Financial Corners is a money transfer and currency exchange company in Switzerland. Most of its business happens in physical branches: people come to the counter to send money abroad with Western Union or to change currency. It is a regulated business that works under FINMA rules and Swiss anti-money-laundering law.

Three things came together that made crypto a natural next product. Swiss law around crypto had changed, which made it possible to offer it in a clear legal frame. Clients were asking for it at the counter. And the company wanted a new source of revenue next to transfers and exchange.

My job was to turn that into a product that the staff could sell every day, in every branch, without creating a compliance risk.

---

### 2. How it works for the client

From the client's side, it is simple:

1. The client comes to the counter and pays in cash.
2. They show the QR code of their own wallet and prove the wallet is theirs.
3. The staff scan the QR code and the Bitcoin or Ethereum is sent to that wallet.

Clients can also do the opposite and sell crypto for cash.

Behind these three steps there is a lot more: identifying the client, checking the amount against the limits, deciding which level of KYC applies, saving the documents, and sending the order to the crypto provider. The whole point of the product design was to keep the counter experience short while making sure none of those checks could be skipped.

---

### 3. My role

I was the product owner on this launch. In practice that meant:

- writing the requirements, from the client flow at the counter to the compliance rules;
- choosing the partner, a Swiss crypto provider, and being their contact from the first calls until launch;
- running the backlog with the external developers who built the integration;
- testing the full flow before launch;
- writing the branch procedures;
- training the branch staff.

The project took about ten months from start to launch.

---

### 4. Working with the partner and the developers

The crypto itself came from a partner, a Swiss crypto provider, and our system had to work with theirs. Choosing that partner was one of my first tasks. After that I stayed their contact for the whole project and followed the integration and the tests with them.

The developers were external too. I wrote the user stories, kept the backlog in order and tested each delivery against the way a branch really works, with a client waiting at the counter.

---

### 5. Compliance built into the product

This was the core of the project. Before launch, the product had to show that FINMA rules and anti-money-laundering requirements were respected, and we needed FINMA's approval.

In practice, the product had to handle:

- identifying the client, with the level of KYC depending on the amount;
- amount limits;
- saving every ID check and document;
- the anti-money-laundering procedures for the staff;
- tracking each client across all branches.

The hardest part was the last one, together with the documents. A client can buy in Geneva one day and in Lausanne the next. If each branch only sees its own transactions, the limits and the KYC levels do not mean much. So we had to recognise the same client in any branch, and keep all their documents saved in a way that we could show them at any moment if there was an audit.

I was responsible for that tracking and for checking that it was done correctly, also beyond the normal case, for example with a client who comes back in another city.

---

### 6. Rolling out to the branches

We went live in all our branches in Geneva, Lausanne, Bern and Zurich. For each branch, the staff needed to know the new flow, the new procedures and, above all, why the compliance steps mattered.

Training is the part I would change. I explained the product the way I understood it, with all the details of the rules. For many agents it was too much at once. Next time I would start from the basics and explain in very simple words the few things that really matter: who the client is, whether the wallet is theirs, which limit applies, and which document must be saved. The rest can come later.

---

### 7. Results

I do not have exact numbers to share, but the signs were clear:

- Clients came back regularly to buy crypto, and also to sell it.
- When audits came, we had the documents they asked for.
- The service is still running today.
- It is now being extended to third-party partner kiosks across Switzerland.

For a regulated product, the audit part matters as much as the sales. A product that sells well but cannot show its documents is a risk for the whole company.

---

### 8. What I learned

- In a regulated business, compliance is part of the product. The tracking across branches was not a feature added at the end; it decided how the whole system worked.
- Training has to start simple. Explaining less, but explaining it well, would have saved time for the staff and for me.
