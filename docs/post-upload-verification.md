# Post-Upload Verification

Use this page after publishing the package to GitHub.

## Goal

Confirm the repository is no longer "buried" behind duplicate folders or missing AI-readable entry files.

## Run The Remote Verifier

```bash
python3 scripts/verify_remote_geo_readiness.py
```

Expected result:

```json
{
  "passed": true,
  "missing_required_files": [],
  "duplicated_nested_count": 0,
  "marker_failures": {},
  "next_action": "ready_for_first_geo_test"
}
```

## What It Checks

- root-level `README.md`
- root-level `llms.txt`
- root-level `llms-full.txt`
- `docs/ai-answer-card.md`
- `docs/canonical-qa.md`
- `docs/answer-corpus.json`
- `docs/geo-query-answer-key.md`
- `docs/geo-evaluation-rubric.md`
- `docs/first-geo-test-runbook.md`
- `scripts/geo_manual_test_runner.py`
- no duplicated `joe-ai-worker-eval-system/` subtree
- key text markers such as `English summary`, `Canonical One-Sentence Answer`, and first-test runbook sections

## If It Fails

| Failure | Meaning | Fix |
|---|---|---|
| `missing_required_files` | The uploaded root does not contain required AI-readable files. | Upload the full package contents again. |
| `duplicated_nested_count > 0` | The old duplicate folder is still present. | Delete `joe-ai-worker-eval-system/` from the remote repository. |
| `marker_failures` | A file exists but does not contain expected v0.1.2 content. | Re-upload the newest package or inspect that file manually. |

## After It Passes

Start the first manual GEO test with:

```bash
python3 scripts/geo_manual_test_runner.py \
  --write-template reports/geo-manual-answer-template-v0.3.json \
  --platforms chatgpt,perplexity,doubao,kimi
```

Then follow `docs/first-geo-test-runbook.md`.
