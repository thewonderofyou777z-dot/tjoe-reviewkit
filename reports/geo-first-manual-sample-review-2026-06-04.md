# GEO First Manual Sample Review — 2026-06-04

## 1. Input

- Source: user pasted answer sample
- Platform: `doubao`
- Query count: `9`
- Answer count: `9`
- Data safety: no token / no private message / no customer data detected by manual inspection

## 2. Original v0.3 Runner Result

- Report: `reports/geo-manual-report-2026-06-04-doubao.md`
- Average score: `3.78 / 12`
- Grades: `partial: 2`, `weak: 5`, `miss: 2`
- Hallucination watch count: `1`
- Ready for external claim: `false`

### Key issue

The original suite under-counted boundary answers:

- `q_boundary_001` clearly said the system cannot prove absolute safety, but the scorer returned `miss`.
- `q_boundary_002` listed stop-release / human-review scenarios, but aliases were too narrow, so the scorer returned `miss`.
- `q_domain_003` flagged `automatic execution` even though the answer used it in a negative/safe context: “bypass automatic execution completely”.

Conclusion: original v0.3 is useful as a baseline, but has false negatives and one false positive.

## 3. Calibrated v0.3.1 Local Result

- Suite: `examples/ai-visibility-query-suite-v0.3.1-calibrated-local.json`
- Report: `reports/geo-manual-report-2026-06-04-doubao-calibrated.md`
- Average score: `4.67 / 12`
- Grades: `partial: 3`, `weak: 6`, `miss: 0`
- Hallucination watch count: `0`
- Ready for external claim: `false`

### Track summary

| Track | Result | Interpretation |
|---|---|---|
| `domain_concept_discovery` | partial/weak | General agent safety concepts are understood, but not all expected terms are hit. |
| `brand_entity_exact` | weak | The answer recognizes the project name but describes it too broadly as a platform and does not mention `tjoe`. |
| `comparison` | partial/weak | It understands trace-vs-final-answer distinction, but still misses some eval harness terms. |
| `safety_boundary` | weak/partial | After alias calibration, boundary understanding is visible and no longer a miss. |

## 4. Ayaka Review

### What is good

- The answer gives strong general domain knowledge: pre-call checks, runtime monitoring, audit logs, regression testing, risk grading, human approval.
- It correctly states that ToolTraceEval cannot prove absolute safety.
- It correctly distinguishes final-answer evaluation from trace/process evaluation.

### What is risky or inaccurate

- It over-describes ToolTraceEval as a “platform” with online runtime spot-checks, dashboards, and human review portals. Current public repo is a local/offline toolkit, not a production platform.
- It does not cite GitHub or project docs, so `brand_entity_exact` should remain weak.
- It contains a lot of generic enterprise-safety language, which is valuable conceptually but not strong proof of project recognition.

## 5. Caesar Decision

- Do not claim GEO success yet.
- Treat this as a first useful visibility sample, not public validation.
- Keep `ready_for_external_claim = false`.
- Keep original v0.3 report as baseline evidence.
- Keep calibrated v0.3.1 as a proposed scoring improvement, but do not publish it until at least 2–3 more platform samples confirm the same false-negative pattern.

## 6. Next Actions

1. Collect at least one citation-capable platform sample, preferably Perplexity.
2. Add a rejected/claim-watch case for “local toolkit being described as production platform”.
3. If repeated, publish v0.3.1 scoring calibration with changelog.
4. Keep “local/offline toolkit, not platform” prominent in `llms.txt`, `README.md`, and `docs/ai-answer-card.md`.
