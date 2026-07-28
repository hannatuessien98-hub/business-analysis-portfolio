# 11. UAT Test Cases & Results

[← Portfolio index](../README.md)

User acceptance testing validates that the delivered solution meets the business need — distinct from system testing, which validates that the software works as specified. A feature can pass system testing and still fail UAT if it satisfies the specification but not the need.

Cases were written from acceptance criteria, then executed against the [delivered application](https://hannatuessien98-hub.github.io/p2p-lending-platform/).

**Environment:** browser, fresh seed data. **Demo password:** `demo1234`

## Entry criteria

- All "Must" requirements built and system-tested
- UAT environment provisioned with test accounts for all three roles (TRN-03)
- Test data seeded (TRN-02)
- No open severity-1 defects

## Exit criteria

- 100% of "Must" requirement test cases passed
- No open severity-1 or severity-2 defects
- Business sign-off recorded

## Test cases

| # | Requirement | Title | Steps | Expected result | Result |
|---|---|---|---|---|---|
| TC-01 | FR-01 | Register new borrower | Create account, role borrower | Account created with status pending | ✅ Pass |
| TC-02 | FR-01 | Reject weak password | Register with 5-character password | Rejected: minimum 8 characters | ✅ Pass |
| TC-03 | FR-01 | Reject duplicate email | Register with an existing email | Rejected: account already exists | ✅ Pass |
| TC-04 | FR-02, BR-01 | Pending account cannot transact | Log in as unapproved user | Blocked: awaiting administrator approval | ✅ Pass |
| TC-05 | FR-01 | Login happy path | Log in as approved borrower | Borrower dashboard loads | ✅ Pass |
| TC-06 | NFR-03 | Wrong credentials rejected | Log in with wrong password | Generic failure message, no detail leaked | ✅ Pass |
| TC-07 | FR-05, FR-06 | Request loan with preview | Enter ₦200,000 / 12 months | Preview shown before submit; matches final terms; loan created as pending | ✅ Pass |
| TC-08 | BR-02 | Amount limits enforced | Request ₦5,000 | Rejected with permitted range stated | ✅ Pass |
| TC-09 | FR-07, STK-04 | Lender sees risk data | Open marketplace | Request visible with credit score, band, projected return | ✅ Pass |
| TC-10 | FR-08, FR-10 | Fund a loan | Approve and fund a pending request | Loan active; lender debited; borrower credited; both transactions recorded | ✅ Pass |
| TC-11 | BR-04 | Insufficient balance blocked | Fund a loan exceeding balance | Rejected; loan remains pending; no partial transfer | ✅ Pass |
| TC-12 | FR-09 | Decline keeps request open | Decline a pending request | Status declined; borrower not blocked from market | ✅ Pass |
| TC-13 | FR-11, BR-09 | Make a repayment | Pay one instalment | Exact amortised amount debited; progress advances; both sides recorded | ✅ Pass |
| TC-14 | FR-12, BR-10 | Final repayment closes loan | Repay to full term | Status repaid; credit score increases | ✅ Pass |
| TC-15 | FR-16, BR-11 | Transaction history accurate | Review history after funding and repayment | Both entries present, correct signs and amounts, newest first | ✅ Pass |
| TC-16 | FR-02 | Admin approves registration | Approve a pending user | Status approved; user can now log in | ✅ Pass |
| TC-17 | FR-14, BR-07 | Admin suspends user | Suspend an approved user | New activity blocked; existing loan unaffected | ✅ Pass |
| TC-18 | NFR-04 | Route guard, unauthenticated | Open dashboard URL while logged out | Redirected to login | ✅ Pass |
| TC-19 | NFR-04 | Role guard | Open admin URL as borrower | Access denied | ✅ Pass |
| TC-20 | NFR-07 | Data persists | Fund a loan, close and reopen | All records intact | ✅ Pass |
| TC-21 | TRN-02 | Reset demo data | Admin resets | Returns to seed state | ✅ Pass |
| TC-22 | NFR-02 | Responsive layout | View at 375px width | Single column, no horizontal scroll | ✅ Pass |

## Results summary

| Metric | Result |
|---|---|
| Cases executed | 22 |
| Passed | 22 |
| Failed | 0 |
| "Must" requirement coverage | 100% |
| Severity-1 / 2 defects open | 0 |

**Automated tests:** the amortisation calculation underpinning BR-09 has 7 automated unit tests covering the payment formula, the 0% edge case, totals, invalid inputs, credit bands, and risk-based rates. All passing.

## Observations from execution

**TC-11 was the case most worth writing.** It confirms that a failed funding attempt leaves *no* partial state — the lender is not debited, the borrower is not credited, and the loan stays available. This is the atomicity requirement NFR-05 and exception flow E4 in [UC-05](05-use-cases.md). Systems frequently pass the happy-path test and fail this one.

**TC-17 validates a business nuance, not just a function.** Suspension blocks new activity but leaves existing loans running. A test that only checked "suspended user cannot log in" would have missed the contractual point: suspending a user must not void obligations already owed to a lender.

## Sign-off

| Role | Decision | Basis |
|---|---|---|
| Business Analyst | Recommended for acceptance | All Must requirements traced and passed |
| Sponsor | *Pending* | Exit criteria met |
