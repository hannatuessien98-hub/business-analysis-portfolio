# 12. Lessons Learned

[← Portfolio index](../README.md)

An honest retrospective. A lessons-learned document that records only successes is worthless — the value is in what would be done differently.

## What worked

**Modelling before documenting.** Drawing the [AS-IS process](03-as-is-process.md) before writing requirements exposed that borrowers and lenders were two halves of the same information problem. That reframing — the platform sells trust, not money — shaped every requirement decision afterwards. Prose alone would not have surfaced it.

**Precise vocabulary resolved a stakeholder conflict.** Sales wanted instant approval; Compliance wanted manual review. The dispute existed because "approval" described two different decisions. Separating account approval from loan funding satisfied both without compromise. **Many apparent stakeholder conflicts are vocabulary problems wearing a disguise.**

**Asking what decision the data would inform.** A stakeholder asked for full financial disclosure to lenders. Asking *what decision are you making with that?* revealed the need was risk assessment — met by a credit score, at far lower data-protection exposure. The stated requirement would have created a compliance problem; the underlying need did not.

**Use cases caught what user stories missed.** Writing exception flows for [UC-05](05-use-cases.md) surfaced the concurrency risk of two lenders funding the same request (E2) and the atomicity requirement for transfers (E4). Neither appeared in the user story version of the same functionality.

## What I would do differently

**Validate assumption A-03 first.** The entire risk-based pricing model depends on obtaining credit bureau data. I documented that as an assumption and moved on. It should have been confirmed before design — if bureau access proves unavailable, FR-03, FR-04, and the lender's core need all need rethinking. **I treated the highest-risk assumption with the same weight as the routine ones.**

**Involve Compliance earlier still.** I engaged Compliance before solution design, which was right, but after elicitation. Some of the data-disclosure discussion could have been avoided entirely had Compliance been present when stakeholders first described what they wanted lenders to see.

**Decide the dual-role question rather than logging it.** Whether one person can be both borrower and lender (issue I-03) surfaced during data modelling and is still open. Open questions that touch the data model should be pushed to a decision quickly — they get more expensive to resolve as build progresses.

**Quantify the AS-IS pain points properly.** I recorded that borrowers abandon applications, evidenced by observation. Without a baseline number, the success measure in the [TO-BE model](04-to-be-process.md) ("under 20% abandonment") has nothing to be measured against. **Baselines are only obtainable before you change the process** — miss that window and the improvement becomes unprovable.

## What I would tell someone starting this

Requirements are not collected, they are *negotiated and discovered*. Stakeholders bring solutions, not problems, and the work is patiently converting one into the other. The most useful question in the toolkit is not "what do you want?" but **"what decision are you trying to make, and what would you do differently if you knew?"**

And model early. A diagram someone can point at and say "no, that's wrong" is worth ten pages of prose everyone nods along to.
