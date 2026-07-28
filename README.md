# Business Analysis Portfolio — P2P Lending Platform

A complete set of business analysis artifacts produced from a real project charter for a peer-to-peer lending platform. Each document shows a different stage of the BA lifecycle, from understanding the business problem through to validating that the delivered solution meets it.

**The working software built from these requirements:** [p2p-lending-platform](https://github.com/hannatuessien98-hub/p2p-lending-platform) · [live demo](https://hannatuessien98-hub.github.io/p2p-lending-platform/)

---

## The business problem

Borrowers in Nigeria struggle to access affordable credit quickly; individual investors lack transparent, safe ways to earn a return on idle funds. Banks intermediate both sides and capture the spread. A peer-to-peer lending platform connects the two directly — borrowers get lower rates, investors get better returns, and the platform manages risk, matching, and settlement.

## Artifacts

| # | Artifact | What it demonstrates |
|---|---|---|
| 1 | [Stakeholder Analysis](artifacts/01-stakeholder-analysis.md) | Identifying who matters, their influence and interest, and how to engage each group |
| 2 | [Elicitation Plan & Findings](artifacts/02-elicitation-plan.md) | Choosing techniques deliberately and separating stated wants from underlying needs |
| 3 | [AS-IS Process Model](artifacts/03-as-is-process.md) | Mapping the current state honestly, including workarounds, with pain points quantified |
| 4 | [TO-BE Process Model](artifacts/04-to-be-process.md) | Designing the future state and tracing each change back to a specific pain point |
| 5 | [Use Case Diagram & Specifications](artifacts/05-use-cases.md) | Actor–goal modelling with full main, alternate, and exception flows |
| 6 | [Business Requirements Document](artifacts/06-brd.md) | The requirements hierarchy: business → stakeholder → solution → transition |
| 7 | [Business Rules Catalogue](artifacts/07-business-rules.md) | Separating rules from requirements so policy can change without redesign |
| 8 | [Data Model & Dictionary](artifacts/08-data-model.md) | Entity relationships and attribute-level definitions |
| 9 | [RAID Log](artifacts/09-raid-log.md) | Risks, assumptions, issues, dependencies with owners and mitigations |
| 10 | [Requirements Traceability Matrix](artifacts/10-traceability-matrix.md) | Proving every requirement is designed, built, and tested — nothing orphaned |
| 11 | [UAT Test Cases & Results](artifacts/11-uat-test-cases.md) | Validating the solution against the acceptance criteria |
| 12 | [Lessons Learned](artifacts/12-lessons-learned.md) | Honest retrospective on what worked and what I'd do differently |

## How to read this portfolio

If you have five minutes, read the [AS-IS](artifacts/03-as-is-process.md) and [TO-BE](artifacts/04-to-be-process.md) process models side by side — they show the analytical core of the work. If you have fifteen, add the [Use Cases](artifacts/05-use-cases.md) and [Traceability Matrix](artifacts/10-traceability-matrix.md).

## Method

Artifacts follow **BABOK v3** structure and **BPMN 2.0** notation for process models. Requirements are classified using the BABOK hierarchy (business, stakeholder, solution — functional and non-functional — and transition requirements). Diagrams are written in Mermaid so they render directly on GitHub.

## About

Produced by **Hannatu Essien** as a portfolio demonstration. The originating project charter was a team deliverable (Workstream 5, TCA Class of June 2022); the analysis, models, and documentation in this repository are my own work built from that charter.
