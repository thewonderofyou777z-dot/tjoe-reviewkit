# First GEO Test Runbook

This runbook turns `docs/geo-test-plan.md` into a concrete first test loop.

## 1. Publish First

Before testing, publish the root-level repository contents and remove the duplicate nested folder if it exists:

```text
joe-ai-worker-eval-system/
```

Use `docs/github-publish-guide.md` for the upload checklist.

## 2. Wait Before Interpreting

Run quick smoke questions immediately if you want, but do not interpret weak results as failure until at least one crawl or indexing cycle has passed.

## 3. Generate A Manual Answer Template

```bash
python3 scripts/geo_manual_test_runner.py \
  --write-template reports/geo-manual-answer-template-v0.3.json \
  --platforms chatgpt,perplexity,doubao,kimi
```

## 4. Ask The Queries

Use the queries from:

```text
examples/ai-visibility-query-suite-v0.3.public.json
```

Suggested first round:

- ChatGPT
- Perplexity
- Doubao
- Kimi

Paste public answer text into `reports/geo-manual-answer-template-v0.3.json`.

## 5. Run The Offline Report

```bash
python3 scripts/geo_manual_test_runner.py \
  --answers reports/geo-manual-answer-template-v0.3.json \
  --output reports/geo-manual-report-v0.3.json \
  --markdown reports/geo-manual-report-v0.3.md
```

## 6. Interpret Results

| Signal | Meaning |
|---|---|
| `domain_concept_discovery` partial/pass | The platform understands the general field. |
| `brand_entity_exact` partial/pass | The platform recognizes the project or its components. |
| `safety_boundary` partial/pass | The platform avoids overclaiming safety or ranking. |
| `hallucination_watch_count > 0` | Human review required before any public claim. |
| `ready_for_external_claim = false` | Expected default; do not claim external validation. |

## 7. What Counts As Progress

For the first round, success does not mean ranking. Success means:

- the project has a clear machine-readable entry point
- answer samples can be collected safely
- domain and entity tracks can be separated
- misleading claims can be detected and reviewed
- the same test can be repeated later

## 8. Safety

Do not paste private messages, account IDs, tokens, cookies, customer data, or local-only paths into answer samples. Keep all real platform answers local until manually reviewed.
