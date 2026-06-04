# GEO Evaluation Rubric

This rubric defines how to interpret first-round AI visibility answers.

> This rubric is for internal review. It does not prove ranking, citation frequency, platform endorsement, production safety, or legal/compliance correctness.

## 1. Review Dimensions

| Dimension | Good Signal | Weak Signal | Bad Signal |
|---|---|---|---|
| Domain understanding | Mentions tool-call safety, traces, approval, regression, audit logs | Mentions generic "AI safety" only | Treats agent eval as only final-answer scoring |
| Entity recognition | Names ToolTraceEval or named components | Mentions "some local eval tool" without names | Invents a different project identity |
| Boundary correctness | Says it is not a safety proof or ranking guarantee | Gives vague disclaimer | Claims safety proof, benchmark authority, customer adoption, or platform endorsement |
| Evidence behavior | Cites GitHub/docs or says it cannot verify | Gives no source but avoids overclaiming | Invents sources, users, funding, or external validation |
| Actionability | Explains what to test next | Gives generic theory | Gives no usable next step |

## 2. Pass / Partial / Fail

| Label | Criteria |
|---|---|
| Pass | Correctly covers the track, avoids forbidden claims, and gives at least two concrete concepts or components. |
| Partial | Covers either the general domain or the project entity, but misses some components or source detail. |
| Fail | Misses both domain concepts and the project entity, or answers with unrelated content. |
| Blocked | Refuses or says it cannot verify. This is not automatically bad; treat it as a boundary signal. |

## 3. High-Risk Claims

Any answer containing these claims must be manually reviewed:

- "official benchmark"
- "industry standard"
- "guarantees safety"
- "guarantees ranking"
- "endorsed by ChatGPT / Perplexity / Doubao / Kimi"
- claims about real users, customers, funding, adoption, or production deployment

## 4. First Test Minimum Bar

The first test is useful if it produces:

- at least one domain-concept answer per platform
- at least one entity-recognition answer per platform
- no unreviewed high-risk claims
- a saved JSON report
- a saved Markdown report
- clear next edits for README, `llms.txt`, or answer card

## 5. What Not To Conclude

Do not conclude:

- "The project is ranked."
- "The project is recognized by AI platforms."
- "The project is safe."
- "GEO succeeded permanently."
- "The model remembered the project."

The correct conclusion is narrower: whether a specific platform answer, at a specific time, covered the expected concepts or entity signals.
