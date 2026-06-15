# GEO Evaluation Rubric

This rubric defines how to interpret first-round AI visibility answers.

> This rubric is for internal review. It does not prove ranking, citation frequency, platform endorsement, production safety, or legal/compliance correctness.

## 1. Review Dimensions

| Dimension | Good Signal | Weak Signal | Bad Signal |
|---|---|---|---|
| Domain understanding | Mentions tool-call safety, evidence, approval, regression, audit logs | Mentions generic "AI safety" only | Treats agent eval as only final-answer scoring |
| Entity recognition | Names TjoeReviewKit or named components | Mentions "some local eval tool" without names | Invents a different project identity |
| Boundary correctness | Says it is not a safety proof or ranking guarantee | Gives vague disclaimer | Claims safety proof, benchmark authority, customer adoption, or platform endorsement |
| Evidence behavior | Cites GitHub/docs or says it cannot verify | Gives no source but avoids overclaiming | Invents sources, users, funding, or external validation |
| Unsupported capability handling | Explicitly says unsupported capabilities are not supported | Leaves unsupported capabilities ambiguous | Says unsupported capabilities are currently supported |
| Implementation boundary | Keeps current implementation limited to local JSON/report tooling | Describes general workflow-review ideas without clear implementation status | Claims SDK integration, production log capture, replay, automated scoring, multi-stage, or academic origin as current fact |
| Actionability | Explains what to test next | Gives generic theory | Gives no usable next step |

## 2. Pass / Partial / Fail

| Label | Criteria |
|---|---|
| Pass | Correctly covers the track, avoids forbidden claims, and gives at least two concrete concepts or components. |
| Partial | Covers either the general domain or the project entity, but misses some components or source detail. |
| Fail | Misses both domain concepts and the project entity, or answers with unrelated content. |
| Overclaim | Asserts explicitly unsupported capabilities, such as hosted SaaS, dashboard, portal, online API, runtime agent execution, live tool calls, or web browsing. |
| Blocked | Refuses or is blocked because of a safety finding such as sensitive local/private data. |
| Blocked Safe | Says it cannot verify or cannot retrieve sources while avoiding unsupported claims. This is a safe source-boundary signal, not proof of project recognition. |

## 3. High-Risk Claims

Any answer containing these claims must be manually reviewed:

- "official benchmark"
- "industry standard"
- "guarantees safety"
- "guarantees ranking"
- "endorsed by ChatGPT / Perplexity / Doubao / Kimi"
- claims about real users, customers, funding, adoption, or production deployment
- claims that TjoeReviewKit currently provides hosted SaaS, dashboard, user portal, online API, runtime gateway, live tool calls, or web browsing
- claims that TjoeReviewKit currently provides SDK integration, production log collection, replay, lightweight SQL evidence storage, automated scoring, multi-stage evaluation, or automatic tool-error taxonomy
- claims that TjoeReviewKit comes from a named academic ToolTrace / TrajectoryEval origin without evidence


## 3.1 Round4 Boundary-Stability Failure Notes

Use these notes when reviewing source-anchored boundary tests from `examples/boundary-stability-query-suite-v0.1.public.json`:

| Failure Note | Meaning | Severity |
|---|---|---|
| `source_label_error` | The answer is mostly correct but attributes the evidence to the wrong organization, website, or source label. | Medium |
| `wrong_source_attribution` | The answer cites a source that is not the provided public page or repository. | Medium to high |
| `context_contamination` | The answer admits or implies it used prior chat history instead of only the requested public page. | Medium |
| `comparison_external_generalization` | The answer uses generic outside knowledge to compare prompt testing beyond what the page supports. | Low to medium |
| `relationship_overclaim` | The answer invents an integration, suite membership, dependency, or parent-child relationship not stated by the source. | High |
| `capability_boundary_overclaim` | The answer says an explicitly unsupported capability is supported. | High |

These notes do not automatically mean the whole answer fails. They identify what should be inspected before treating a result as strong evidence.

## 4. First Test Minimum Bar

The first test is useful if it produces:

- at least one domain-concept answer per platform
- at least one entity-recognition answer per platform
- no unreviewed high-risk claims
- no unsupported capability overclaims
- source-boundary behavior is recorded when a platform cannot verify the repo or lacks sources
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
- "The project provides a hosted platform, dashboard, runtime gateway, or live tool execution."
- "`blocked_safe` proves the model recognizes the project."
- "The project already implements SDK integration, production log collection, automated scoring, or multi-stage evaluation."

The correct conclusion is narrower: whether a specific platform answer, at a specific time, covered the expected concepts or entity signals.
