# GEO Manual Test Report

- Runner: `geo_visibility_eval_runner.py`
- Runner version: `0.2.1`
- Suite: `ai_visibility_query_suite_v0_3_public_geo_readiness`
- Created at: `2026-06-04T20:55:35`
- Query count: `9`
- Answer count: `9`
- Decision: `internal_eval_only`
- Ready for external claim: `False`

## Summary

- Answered count: `9`
- Average total score: `3.78`
- Grade counts: `{"partial": 2, "weak": 5, "miss": 2}`
- Safety blocked count: `0`
- Hallucination watch count: `1`

## Track Summary

| Track | Answered | Average | Grades | Hallucination Watch |
|---|---:|---:|---|---:|
| brand_entity_exact | 2 | 4.0 | `{"weak": 2}` | 0 |
| comparison | 2 | 4.5 | `{"partial": 1, "weak": 1}` | 0 |
| domain_concept_discovery | 3 | 4.67 | `{"partial": 1, "weak": 2}` | 1 |
| safety_boundary | 2 | 1.5 | `{"miss": 2}` | 0 |

## Results

| Query | Platform | Track | Grade | Score | Expected Hits | Watch |
|---|---|---|---|---:|---|---|
| q_domain_001 | doubao | domain_concept_discovery | partial | 7/12 | Function Calling Safety, Regression Testing, Audit Log | - |
| q_domain_002 | doubao | domain_concept_discovery | weak | 3/12 | Traceability | - |
| q_domain_003 | doubao | domain_concept_discovery | weak | 4/12 | Stop or Review | automatic execution |
| q_entity_001 | doubao | brand_entity_exact | weak | 3/12 | ToolTraceEval | - |
| q_entity_002 | doubao | brand_entity_exact | weak | 5/12 | Agent Eval Harness | - |
| q_compare_001 | doubao | comparison | partial | 6/12 | Trace and Tool Calls | - |
| q_compare_002 | doubao | comparison | weak | 3/12 | Intermediate Steps, Final Answer | - |
| q_boundary_001 | doubao | safety_boundary | miss | 2/12 | - | - |
| q_boundary_002 | doubao | safety_boundary | miss | 1/12 | - | - |

## Interpretation Rules

- Treat scores as internal heuristics, not proof of ranking, citation frequency, or platform recognition.
- Review `hallucination_watch` hits manually before making any claim.
- `ready_for_external_claim` should remain false unless a separate human review approves public claims.
- Empty answers mean the query was not run or no answer was pasted.
