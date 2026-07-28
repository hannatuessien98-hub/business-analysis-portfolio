# 7. Business Rules Catalogue

[← Portfolio index](../README.md)

Business rules are separated from requirements deliberately. A requirement says *the system must apply a rate based on credit score*; the rule says *what those rates are*. When the business changes its rate card, the rule changes and the requirement does not — no redesign, no rebuild.

Confusing the two is a common and expensive mistake: rate thresholds buried inside code as requirements mean every policy tweak becomes a development request.

## Rules catalogue

| ID | Rule | Type | Owner | Volatility |
|---|---|---|---|---|
| **BR-01** | A new account cannot transact until an administrator approves it | Constraint | Compliance | Low |
| **BR-02** | A loan request must be between ₦10,000 and ₦10,000,000 | Constraint | Sponsor | **High** |
| **BR-03** | Permitted loan terms are 3, 6, 12, or 24 months | Constraint | Sponsor | Medium |
| **BR-04** | A lender cannot fund a loan exceeding their available balance | Constraint | Finance | Low |
| **BR-05** | A loan may be funded by exactly one lender (in this release) | Constraint | Sponsor | **High** |
| **BR-06** | Interest rate is derived from the borrower's credit score band | Computation | Risk | **High** |
| **BR-07** | A suspended user cannot initiate new activity, but existing loans continue | Constraint | Compliance | Low |
| **BR-08** | Only administrators may change a user's account status | Constraint | Compliance | Low |
| **BR-09** | Repayment amount is fixed for the life of the loan | Computation | Finance | Low |
| **BR-10** | Full repayment increases the borrower's credit score | Derivation | Risk | Medium |
| **BR-11** | Every money movement generates a transaction record for both parties | Constraint | Compliance | Low |

## BR-06: Risk-based pricing (decision table)

| Credit score | Band | Annual rate |
|---|---|---|
| 750–850 | Excellent | 12% |
| 670–749 | Good | 15% |
| 580–669 | Fair | 19% |
| Below 580 | Poor | 24% |

## BR-09: Repayment calculation

Standard amortisation:

```
payment = P × r / (1 − (1 + r)^−n)

P = principal    r = monthly rate (annual ÷ 12 ÷ 100)    n = term in months
```

Worked example: ₦500,000 at 15% over 12 months → **₦45,129.16 per month**, ₦541,549.92 total, ₦41,549.92 interest.

## BR-10: Credit score adjustment

| Event | Adjustment | Ceiling |
|---|---|---|
| Loan repaid in full | +15 | 850 |
| Missed payment | −20 *(deferred — requires arrears handling, out of scope)* | 300 floor |

## Volatility analysis

The three rules marked **high volatility** — BR-02, BR-05, BR-06 — are the ones most likely to change as the business learns. They should be **configurable values, not hard-coded logic**.

BR-05 in particular is a deliberate simplification: single-lender funding is easier to build, but the business will almost certainly want syndicated funding once loan sizes grow. Flagging it now means the data model accommodates it later rather than requiring restructuring. This is recorded as alternate flow A2 in [UC-05](05-use-cases.md).
