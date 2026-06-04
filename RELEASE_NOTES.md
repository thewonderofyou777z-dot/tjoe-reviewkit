# Release Notes

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
