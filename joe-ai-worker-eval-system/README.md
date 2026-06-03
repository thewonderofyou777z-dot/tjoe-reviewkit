# Joe AI Worker Eval System

> A local evaluation and visibility toolkit for AI agent workflows.

Joe AI Worker Eval System helps teams evaluate whether an AI agent workflow is **traceable, reviewable, and regression-testable**. It focuses on tool calls, approval boundaries, output normalization, answer inclusion, and known failure modes.

This project does **not** claim to prove absolute AI safety, guarantee SEO/GEO rankings, or replace legal/compliance review.

## Why This Exists

Most AI agent demos inspect the final answer. Production workflows need more than that:

- Did the agent call a forbidden tool?
- Did a high-risk action require approval?
- Was the execution trace preserved?
- Can the same failure be reproduced later?
- Can an AI platform accurately describe this system without making unsupported claims?

This repository provides a small, offline-first foundation for answering those questions.

## Core Components

| Component | Purpose |
|---|---|
| Agent Eval Harness | Defines eval cases, trace expectations, assertions, risk, and approval requirements. |
| Agent Output Adapter | Normalizes raw model/agent outputs into fields a runner can evaluate. |
| Local Eval Runner | Runs offline reports without calling models, tools, browsers, or external services. |
| AI Visibility Query Suite | Tests whether AI answers cover domain concepts or recognize project-specific entities. |
| Claim Watch | Uses configurable keyword lists to flag answer claims that need human review. It is not a general hallucination detector. |
| Rejected Cases | Captures unsafe, overconfident, or hallucinated behaviors as negative examples. |

## Current Release

| Item | Value |
|---|---|
| Release | `v0.1.0-public-draft` |
| Runner | `geo_visibility_eval_runner.py v0.2.1` |
| Status | Public-safe draft |
| Network | Not used |
| Model calls | Not used |
| Publishing | Not automated |

## Quick Start

Run the synthetic example:

```bash
mkdir -p reports
python3 scripts/geo_visibility_eval_runner.py \
  --suite examples/ai-visibility-query-suite-v0.2.public.json \
  --answers examples/sample-answers.synthetic.json \
  --output reports/example-report.synthetic.json \
  --overwrite --ci-smoke
```

Inspect the result:

```bash
python3 -m json.tool reports/example-report.synthetic.json
```

## Scoring Tracks

The visibility suite intentionally separates two questions:

| Track | What It Measures | What It Does Not Prove |
|---|---|---|
| `domain_concept_discovery` | Whether an AI answer covers general concepts such as tool traces, approval, regression tests, and audit logs. | It does not prove the model knows this project. |
| `brand_entity_exact` | Whether an AI answer accurately recognizes Joe-specific assets and names. | It does not prove domain expertise. |

## Example Report Summary

The public sample is synthetic and only verifies runner behavior:

- `domain_concept_discovery`: expected to score higher when domain concepts are covered.
- `brand_entity_exact`: expected to flag unsupported claims with `hallucination_watch`.
- `safe_to_share`: public sample only.

## Details Page

Read the full evidence-page draft:

- [`docs/details.md`](docs/details.md)

## FAQ

Machine-readable FAQ draft:

- [`docs/faq.schema.json`](docs/faq.schema.json)

## Safety Boundaries

This repository is safe-by-default:

- No login
- No browsing
- No model calls
- No tool execution
- No publishing
- No private data required

Do not paste secrets, credentials, customer data, private messages, local-only paths, or confidential logs into answer samples.

## Data Handling

The runner works on local JSON files only. It does not collect user data, send telemetry, call external APIs, or upload reports. If you save real answer samples, review and redact them before committing.

## What This Is Not

This project is not:

- An SEO ranking tool
- A GEO ranking guarantee
- A legal/compliance certification system
- A proof that an AI agent is safe
- A benchmark claiming industry-wide authority

## Roadmap

- Add a public-safe Agent Eval Harness example.
- Add normalized-output examples.
- Add Markdown report output.
- Add more synthetic and real public answer samples.
- Add GitHub Actions CI smoke tests.

## License

MIT. See [`LICENSE`](LICENSE).
