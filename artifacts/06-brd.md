# 6. Business Requirements Document

[← Portfolio index](../README.md)

Requirements are classified using the **BABOK v3 hierarchy**: business requirements state why the organisation is doing this; stakeholder requirements state what each group needs; solution requirements state what the system must do; transition requirements state what is needed only to get from current to future state.

Keeping these separate matters — it prevents a stakeholder's preferred *solution* being recorded as an organisational *need*.

---

## 1. Business requirements

*Why the organisation is undertaking this. Solution-independent.*

| ID | Requirement | Success measure |
|---|---|---|
| BUS-01 | Enable individuals to access credit at rates below informal lending | Average platform rate materially below informal market |
| BUS-02 | Enable individuals to earn returns above conventional savings products | Average lender return exceeds prevailing savings rate |
| BUS-03 | Reduce time from credit application to decision | Under 48 hours (baseline 2–4 weeks) |
| BUS-04 | Operate within CBN lending and NDPR data protection obligations | Zero regulatory findings |
| BUS-05 | Build a durable, auditable record of lending activity | Complete transaction history for every money movement |

## 2. Stakeholder requirements

*What each group needs, expressed in their terms.*

| ID | Stakeholder | Requirement | Traces to |
|---|---|---|---|
| STK-01 | Borrower | Apply for credit without physical visits | BUS-01, BUS-03 |
| STK-02 | Borrower | Know the repayment obligation before committing | BUS-01 |
| STK-03 | Borrower | Understand why a rate was offered | BUS-01 |
| STK-04 | Lender | Assess borrower risk before committing capital | BUS-02 |
| STK-05 | Lender | Decline without penalty | BUS-02 |
| STK-06 | Lender | Track portfolio performance | BUS-02 |
| STK-07 | Administrator | Vet users before they transact | BUS-04 |
| STK-08 | Administrator | Act immediately on a problem user | BUS-04 |
| STK-09 | Compliance | Audit trail of every money movement | BUS-04, BUS-05 |
| STK-10 | Both parties | Access their own transaction record | BUS-05 |

## 3. Solution requirements — functional

| ID | Requirement | Priority | Source | Use case |
|---|---|---|---|---|
| FR-01 | Users can register as borrower or lender | Must | STK-01 | UC-01 |
| FR-02 | New accounts require administrator approval before transacting | Must | STK-07 | UC-04 |
| FR-03 | System assigns each user a credit score | Must | STK-04 | UC-09 |
| FR-04 | Interest rate is derived from credit score (risk-based pricing) | Must | STK-03 | UC-02 |
| FR-05 | Borrowers can submit a loan request specifying amount, term, purpose | Must | STK-01 | UC-02 |
| FR-06 | System displays monthly repayment and total repayable before submission | Must | STK-02 | UC-02 |
| FR-07 | Pending requests are visible to lenders with borrower credit score | Must | STK-04 | UC-05 |
| FR-08 | Lenders can fund a pending request | Must | STK-04 | UC-05 |
| FR-09 | Lenders can decline; request remains open to others | Must | STK-05 | UC-06 |
| FR-10 | Funding transfers the amount and records transactions for both parties | Must | STK-09 | UC-05 |
| FR-11 | Borrowers can make monthly repayments | Must | STK-01 | UC-03 |
| FR-12 | Full repayment closes the loan and improves the credit score | Should | STK-03 | UC-03 |
| FR-13 | Lenders can view portfolio performance | Should | STK-06 | — |
| FR-14 | Administrators can suspend and reinstate users | Must | STK-08 | UC-07 |
| FR-15 | Administrators can view all loans and platform statistics | Must | STK-07 | — |
| FR-16 | Users can view their own transaction history | Must | STK-10 | UC-08 |
| FR-17 | Direct messaging between users | Won't (this release) | — | — |
| FR-18 | Bank account linking for deposits and withdrawals | Won't (this release) | — | — |

*Prioritised with MoSCoW. "Won't" items are recorded rather than deleted so the decision remains visible.*

## 4. Solution requirements — non-functional

| ID | Category | Requirement |
|---|---|---|
| NFR-01 | Usability | A loan application must be completable in a single session (finding F1) |
| NFR-02 | Availability | Platform available on multiple devices and screen sizes |
| NFR-03 | Security | Credentials never stored or transmitted in plain text |
| NFR-04 | Security | Users can access only their own records; role-based access enforced server-side |
| NFR-05 | Integrity | Fund transfers are atomic — both sides commit or neither does |
| NFR-06 | Compliance | Personal data handled per NDPR; minimum necessary disclosure between parties |
| NFR-07 | Auditability | Every money movement produces an immutable, timestamped record |
| NFR-08 | Performance | Marketplace and dashboards load within 3 seconds under expected load |
| NFR-09 | Accessibility | Meets WCAG 2.1 AA |

**NFR-05 deserves emphasis.** It is the requirement most likely to be overlooked and most damaging if missed: a transfer that debits a lender without crediting the borrower loses real money and destroys trust in the platform. It is captured as exception flow E4 in [UC-05](05-use-cases.md).

## 5. Transition requirements

*Needed only to move from current state to future state; retired afterwards.*

| ID | Requirement |
|---|---|
| TRN-01 | Administrator training on the user review and suspension workflow |
| TRN-02 | Seed data for demonstration and UAT execution |
| TRN-03 | UAT environment with test accounts for all three roles |
| TRN-04 | Support team briefing on account states and what each means to a user |

## 6. Assumptions and constraints

**Assumptions** — funding is available for the full delivery; the development team has the necessary skills; credit bureau data can be obtained under a permissioned interface; the regulatory position on P2P lending remains stable through delivery.

**Constraints** — fixed budget; delivery window set by the charter; team distributed and meeting virtually; several team members new to the BA role.

## 7. Scope boundary

**In scope:** account management, loan request and matching, funding and repayment, credit scoring, administrative oversight, transaction history.

**Out of scope:** bad-loan recovery, video/audio conferencing, e-commerce, multi-language support, automated feedback channels.
