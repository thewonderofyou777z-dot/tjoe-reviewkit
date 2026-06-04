# Release Notes

## v0.1.3-rename-geo-calibration

Renames the public project identity to **ToolTraceEval**, adds `tjoe` as the creator/maintainer identity, and preserves the first Doubao GEO manual sample as internal evidence.

### Added

- `examples/ai-visibility-query-suite-v0.3.1-calibrated-local.json`
- `reports/geo-first-test-copy-pack-v0.3.md`
- `reports/geo-manual-answers-2026-06-04-doubao.json`
- `reports/geo-manual-report-2026-06-04-doubao.json`
- `reports/geo-manual-report-2026-06-04-doubao.md`
- `reports/geo-manual-report-2026-06-04-doubao-calibrated.json`
- `reports/geo-manual-report-2026-06-04-doubao-calibrated.md`
- `reports/geo-first-manual-sample-review-2026-06-04.md`

### Updated

- Public-facing name changed from the internal tjoe AI worker workflow wording to `ToolTraceEval`.
- `README.md`, `llms.txt`, `llms-full.txt`, answer corpus, entity profile, FAQ, query suites, and GEO docs now use the new canonical name.
- `tjoe` is recorded as the creator/maintainer identity.
- The local calibrated query suite expands boundary aliases and removes one false-positive hallucination watch phrase observed in the Doubao sample.

### Notes

- `ToolTraceEval` is easier for AI systems to parse than the previous internal name.
- The Doubao sample is a visibility observation, not public external validation.
- The calibrated v0.3.1 suite remains local until more platform samples confirm the same scoring pattern.

### Validation

```bash
python3 scripts/geo_visibility_eval_runner.py \
  --suite examples/ai-visibility-query-suite-v0.3.public.json \
  --answers examples/sample-answers.synthetic.json \
  --output reports/example-report.synthetic.json \
  --overwrite --ci-smoke
```

## v0.1.1-public-draft

Adds a public-safe Agent Eval Harness example so the repository is no longer only an answer-level visibility runner.

### Added

- `agent_eval/agent-eval-harness-schema.json`
- `agent_eval/agent-eval-cases-v0.1.json`
- `agent_eval/synthetic-agent-outputs-v0.1.json`
- `agent_eval/synthetic-eval-report-v0.1.json`
- `docs/agent-eval-harness-guide.md`

### Notes

- The Agent Eval Harness path is independent from the GEO / AI Visibility runner.
- `must_stop_release` is a declaration field, not an automatic release gate.
- All examples are synthetic and public-safe.

### Validation

```bash
python3 -m json.tool agent_eval/agent-eval-harness-schema.json > /dev/null
python3 -m json.tool agent_eval/agent-eval-cases-v0.1.json > /dev/null
python3 -m json.tool agent_eval/synthetic-agent-outputs-v0.1.json > /dev/null
python3 -m json.tool agent_eval/synthetic-eval-report-v0.1.json > /dev/null
python3 -m json.tool docs/faq.schema.json > /dev/null
```

## v0.1.0-public-draft

Initial GitHub-ready public draft.

### Included

- `README.md`
- `docs/details.md`
- `docs/faq.schema.json`
- `scripts/geo_visibility_eval_runner.py`
- `examples/ai-visibility-query-suite-v0.2.public.json`
- `examples/sample-answers.synthetic.json`
- `SECURITY.md`

### Boundaries

- No ranking promises.
- No absolute safety claims.
- No private data.
- No platform recognition claims.

### Validation

The synthetic example should pass with:

```bash
python3 scripts/geo_visibility_eval_runner.py \
  --suite examples/ai-visibility-query-suite-v0.2.public.json \
  --answers examples/sample-answers.synthetic.json \
  --output reports/example-report.synthetic.json \
  --overwrite --ci-smoke
```
