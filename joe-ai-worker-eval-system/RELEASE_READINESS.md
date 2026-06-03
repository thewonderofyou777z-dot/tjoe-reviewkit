# Release Readiness

Status: ready for GitHub repo creation and public push.

Date: 2026-06-03
Package: joe-ai-worker-eval-system
Release target: v0.1.0-public-draft

## Scope

This package is a public-safe starter release for evaluating how AI platforms answer GEO / SEO / AI visibility questions.

It includes:

- an offline deterministic runner
- public synthetic query and answer examples
- an example report
- a details page
- FAQ schema draft
- contribution, security, release, and license documents

It does not include:

- private answers
- customer data
- credentials
- local-only workspace paths
- private OpenClaw / Hermes / Ollama configuration
- claims that the system proves ranking, GEO performance, or model truthfulness

## OpenClaw Retest

The OpenClaw review layer reviewed the release package after the P0 fixes.

Result:

- P0 verification: passed
- remaining blockers: none
- ready_to_create_repo: yes
- ready_to_push_public: yes

Reviewed fixes:

- MIT license added
- public runner no longer includes internal role names in `ENTITY_TERMS`
- README overclaim was changed from hallucination prevention to unsupported-claim detection
- `hallucination_watch` is documented as a keyword claim-watch mechanism, not a general hallucination detector
- runner default paths are repo-relative
- contribution and data-handling docs were added
- synthetic smoke report exists and is public-safe

## Final Checks

Final checks passed:

- Python syntax check passed for `scripts/geo_visibility_eval_runner.py`
- JSON validation passed for `docs/faq.schema.json`
- JSON validation passed for `examples/ai-visibility-query-suite-v0.2.public.json`
- JSON validation passed for `examples/sample-answers.synthetic.json`
- JSON validation passed for `reports/example-report.synthetic.json`
- synthetic smoke test passed with `--ci-smoke`
- package file list contains no generated `__pycache__`
- public safety scan found only documentation warnings and runner regex patterns, not actual secrets

## Caveats

- The example report uses synthetic answers only.
- Scores are diagnostic signals, not proof of real GEO visibility.
- Claim Watch flags suspicious keyword patterns; it does not verify truth by itself.
- Public release should start as a draft or v0.1.0-public-draft.
- Any real platform answers should be reviewed before publishing.

## Suggested First GitHub Steps

```bash
git init
git add .
git commit -m "Initial public draft of Joe AI Worker Eval System"
gh repo create joe-ai-worker-eval-system --public --source=. --remote=origin --push
```

Do not run these commands until the repo name, license holder, and public release intent are confirmed.

## Local Commit Status

The package has been initialized as an independent local git repository.

- branch: `main`
- commit: `33ba8ae Initial public draft`
- working tree: clean after commit

## Current Publishing Blocker

GitHub push is blocked by missing authentication tooling or credentials.

Observed state:

- `gh` is not installed in the active shell
- no `GITHUB_TOKEN` or `GH_TOKEN` is available
- no SSH key is configured for GitHub push
- no `origin` remote is configured yet

Next valid options:

1. Install and authenticate GitHub CLI:

```bash
brew install gh
gh auth login
```

Then run from this directory:

```bash
gh repo create joe-ai-worker-eval-system --public --source=. --remote=origin --push
```

2. Create an empty GitHub repository manually, then add the remote:

```bash
git remote add origin git@github.com:<owner>/joe-ai-worker-eval-system.git
git push -u origin main
```

3. Provide a temporary GitHub token through a secure shell environment and use the GitHub API to create the repo.
