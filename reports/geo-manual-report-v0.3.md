# GEO Manual Test Report

- Runner: `geo_visibility_eval_runner.py`
- Runner version: `0.2.5`
- Suite: `ai_visibility_query_suite_v0_3_public_geo_readiness`
- Created at: `2026-06-05T22:05:03`
- Query count: `10`
- Answer count: `40`
- Decision: `template_only`
- Ready for external claim: `False`

## Summary

- Answered count: `0`
- Average total score: `0`
- Grade counts: `{}`
- Safety blocked count: `0`
- Hallucination watch count: `0`
- Unsupported claim count: `0`
- Blocked safe count: `0`
- Source status counts: `{}`

## Track Summary

| Track | Answered | Average | Grades | Hallucination Watch | Unsupported Claims | Blocked Safe | Source Status |
|---|---:|---:|---|---:|---:|---:|---|

## Results

| Query | Platform | Track | Grade | Source Status | Score | Expected Hits | Watch | Unsupported Claims |
|---|---|---|---|---|---:|---|---|---|
| q_domain_001 | kimi | domain_concept_discovery | miss | no_source_provided | 0/12 | - | - | - |
| q_domain_002 | kimi | domain_concept_discovery | miss | no_source_provided | 0/12 | - | - | - |
| q_domain_003 | kimi | domain_concept_discovery | miss | no_source_provided | 0/12 | - | - | - |
| q_entity_001 | kimi | brand_entity_exact | miss | no_source_provided | 0/12 | - | - | - |
| q_entity_002 | kimi | brand_entity_exact | miss | no_source_provided | 0/12 | - | - | - |
| q_compare_001 | kimi | comparison | miss | no_source_provided | 0/12 | - | - | - |
| q_compare_002 | kimi | comparison | miss | no_source_provided | 0/12 | - | - | - |
| q_boundary_001 | kimi | safety_boundary | miss | no_source_provided | 0/12 | - | - | - |
| q_boundary_002 | kimi | safety_boundary | miss | no_source_provided | 0/12 | - | - | - |
| q_boundary_003 | kimi | safety_boundary | miss | no_source_provided | 0/12 | - | - | - |

## Interpretation Rules

- Treat scores as internal heuristics, not proof of ranking, citation frequency, or platform recognition.
- Review `hallucination_watch` hits manually before making any claim.
- Treat `unsupported_claim_hits` as hard negative signals that require human review.
- Treat `blocked_safe` as a safe refusal / source-boundary signal, not evidence that the project is recognized.
- `ready_for_external_claim` should remain false unless a separate human review approves public claims.
- Empty answers mean the query was not run or no answer was pasted.
