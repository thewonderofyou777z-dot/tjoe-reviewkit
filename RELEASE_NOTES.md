# Release Notes

## v0.1.2-geo-readiness-draft

Adds public-safe GEO readiness assets so AI systems and human reviewers have clearer entity, claim, and testing signals.

### Added

- `llms.txt`
- `llms-full.txt`
- `docs/ai-answer-card.md`
- `docs/canonical-qa.md`
- `docs/answer-corpus.json`
- `docs/geo-query-answer-key.md`
- `docs/geo-evaluation-rubric.md`
- `docs/entity-profile.json`
- `docs/claim-evidence-map.json`
- `docs/geo-test-plan.md`
- `docs/github-publish-guide.md`
- `docs/api-publish-runbook.md`
- `docs/post-upload-verification.md`
- `docs/first-geo-test-runbook.md`
- `examples/ai-visibility-query-suite-v0.3.public.json`
- `reports/answer-template-v0.3.public.json`
- `reports/template-only-report-v0.3.public.json`
- `scripts/geo_manual_test_runner.py`
- `scripts/publish_to_github.py`
- `scripts/verify_remote_geo_readiness.py`
- `.github/workflows/ci.yml`

### Updated

- `README.md` now includes an English canonical summary at the top.
- `scripts/geo_visibility_eval_runner.py` now defaults to the v0.3 public query suite.
- `examples/sample-answers.synthetic.json` now includes synthetic answers for the v0.3 query suite.
- `docs/details.md` now references the GEO readiness files.

### Notes

- These files improve AI readability, entity clarity, and manual GEO test readiness.
- They do not claim platform recognition, ranking improvement, production safety, or external validation.
- The v0.3 suite is still synthetic and public-safe.

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
