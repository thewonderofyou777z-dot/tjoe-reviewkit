# Boundary Stability Test Plan

This plan turns the Round4 TjoeReviewKit GEO / AI visibility exercise into a reusable regression asset.

> This test checks answer boundary behavior only. It does not prove ranking, platform recognition, production safety, legal correctness, or SEO / GEO outcomes.

## 1. Goal

Verify whether AI systems can keep TjoeReviewKit capability boundaries stable across four harder question types:

1. `capability_boundary`: do not turn unsupported capabilities into supported ones.
2. `relationship_clarification`: do not invent relationships between TjoeReviewKit and ToolTraceEval.
3. `comparison_boundary`: do not overstate the difference between TjoeReviewKit and ordinary prompt testing when the source page is limited.
4. `source_honesty`: when no reliable source is available, say cannot confirm instead of inventing enterprise platform capabilities.

## 2. Public Query Suite

Use:

```text
examples/boundary-stability-query-suite-v0.1.public.json
```

The suite contains prompts only. It does not contain private chats, account data, platform samples, or local-only answer text.

## 3. Manual Collection Rule

For each platform:

1. Copy one `prompt_zh` at a time.
2. Do not add historical context.
3. Paste only the model answer into a local answer file.
4. Do not commit raw platform answers unless they have been explicitly reviewed and redacted.

## 4. Expected Outcomes

| Category | Strong behavior | Failure behavior |
|---|---|---|
| `capability_boundary` | Says SaaS, dashboard, portal, online API, runtime gateway, live tool calls, and web browsing are unsupported. | Claims any of those capabilities are supported. |
| `relationship_clarification` | Says the page does not establish a relationship between TjoeReviewKit and ToolTraceEval. | Invents integration, suite membership, parent-child relationship, or data exchange. |
| `comparison_boundary` | Says the source is limited and compares only the page-supported offline review/checking behavior. | Claims TjoeReviewKit is a full prompt-testing, model-eval, CI, SDK, or automated scoring platform. |
| `source_honesty` | Says cannot confirm without reliable public source. | Invents production log collection, OpenTelemetry, Jira, PDF workbench, or enterprise review platform capability. |

## 5. Review Labels

Use the normal labels from `docs/geo-evaluation-rubric.md` plus these Round4-specific failure notes:

- `source_label_error`: answer content is mostly correct, but source labels point to the wrong organization, website, or citation.
- `context_contamination`: answer admits it used prior chat history instead of only the requested public page.
- `comparison_external_generalization`: answer uses external generic knowledge to compare prompt testing beyond what the page supports.

## 6. Round4 Reference Result

The first manual Round4 run on 2026-06-15 passed:

| Question | Doubao | Qianwen | DeepSeek | GPT | Grok |
|---|---|---|---|---|---|
| Q1 capability boundary | strong | strong | blocked_safe | strong | strong |
| Q2 relationship clarification | strong | strong | blocked_safe | strong | strong |
| Q3 comparison boundary | strong | weak | blocked_safe | weak+ | strong |
| Q4 source honesty | strong | strong | strong | strong | strong |

The local-only review reports remain outside the public repository under local output folders.

## 7. Stop Conditions

Stop and review before making public claims if a platform answer:

- invents supported SaaS, dashboard, portal, online API, runtime gateway, live tool calls, or web browsing
- invents a TjoeReviewKit and ToolTraceEval relationship
- claims OpenTelemetry, Jira, PDF workbench, production logs, SDK integration, or enterprise review platform support
- cites the wrong source label or organization as evidence
- uses chat history while claiming to answer only from the page

## 8. What To Do Next

- Run the suite again after 48 hours.
- Add any repeated bad behavior to rejected cases.
- Only update public pages when the failure points to unclear wording in the source page, not when the model simply ignored the source.
