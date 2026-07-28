# 2. Elicitation Plan & Findings

[← Portfolio index](../README.md)

Technique selection is a deliberate decision, not a default to interviews. Each technique below was chosen because of what it is good at and what the alternatives would have missed.

## Technique selection

| Technique | Applied to | Why this technique | What it would miss alone |
|---|---|---|---|
| **Document analysis** | Project charter, CBN lending guidelines, competitor terms | Cheapest starting point; establishes vocabulary before consuming stakeholder time | Documents describe intent, not actual practice |
| **Semi-structured interviews** | Sponsor, Compliance, Administrators | Surfaces individual concerns people won't raise in a group | Individuals describe their slice, not the end-to-end flow |
| **Facilitated workshop** | Administrators + Support + Dev | Builds the cross-functional process map with everyone present; disagreements surface live | Dominant voices can crowd out quieter ones |
| **Contextual observation** | Watching borrowers apply for credit through existing channels | Reveals the workarounds people don't report — the gap between described and actual process | Small sample; not statistically representative |
| **Survey** | Prospective borrowers and lenders | Quantifies whether observed pain points generalise | Cannot probe an unexpected answer |
| **Prototyping** | Loan request and approval flows | Turns abstract debate into concrete reaction; people critique what they can see | Can anchor thinking on the first design shown |

## Question design

The interview questions were built to separate **stated want** from **underlying need**:

> *"You've said you want lenders to see the borrower's full financial history. What decision are you trying to make with that information?"*

The answer was risk assessment — which led to a credit score and risk band rather than raw financial disclosure. That satisfies the real need while significantly reducing data protection exposure under NDPR. **The stated requirement would have created a compliance problem; the underlying need did not.**

## Key findings

| # | Finding | Source | Implication |
|---|---|---|---|
| F1 | Borrowers abandon applications that take more than one sitting to complete | Observation | Application must be completable in a single session |
| F2 | Lenders will not fund without a comparable risk indicator | Interviews, survey | Credit score and risk band are mandatory, not optional |
| F3 | "Approve the borrower" and "approve the loan" were used interchangeably by different stakeholders | Workshop | Two distinct decisions — separated into admin account approval and lender loan approval |
| F4 | Administrators need to act on a problem user immediately, not wait for a batch process | Interviews | Suspend capability required in MVP |
| F5 | Compliance requires a durable record of every money movement | Compliance interview | Transaction history is a regulatory requirement, not a convenience feature |
| F6 | Borrowers assume repayment schedules before they commit | Observation, prototype | Repayment preview before submission |

## Conflict resolved

Sales-oriented stakeholders wanted **instant automatic approval** to maximise volume. Compliance required **manual review of new registrations**. Both positions were legitimate.

Resolution: separate the two decisions. Account registration requires administrator approval (satisfying Compliance); once approved, a borrower can request loans freely and lenders decide in real time (satisfying speed). **The conflict existed because a single word — "approval" — described two different things.** Precise vocabulary dissolved it.

This is recorded as finding F3 above and drove the split between [UC-01 and UC-04](05-use-cases.md).
