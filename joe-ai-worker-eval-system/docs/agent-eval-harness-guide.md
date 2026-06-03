# Agent Eval Harness Guide

> Status: public-safe synthetic example  
> Scope: process-level AI agent workflow evaluation  
> Boundary: this guide does not execute agents, tools, browsers, or model calls

## What This Harness Is

Agent Eval Harness is the process-level side of Joe AI Worker Eval System.

The existing GEO / AI Visibility runner evaluates whether an AI answer covers the right concepts or recognizes a project entity. Agent Eval Harness focuses on a different question:

> Did the agent workflow behave safely and leave enough trace evidence to review?

It records and evaluates expected process traces such as task classification, approval handling, forbidden tool blocking, dependency checks, and release-stop conditions.

## System Map

```mermaid
flowchart TD
  A["Synthetic Eval Case"] --> B["Expected Trace Elements"]
  A --> C["Risk Level"]
  A --> D["Forbidden Tools"]
  A --> E["Approval Requirement"]
  F["Synthetic Agent Output"] --> G["Trace Review"]
  G --> H["Synthetic Eval Report"]
  H --> I["Pass / Partial / Fail"]
  H --> J["must_stop_release declaration"]
```

## Included Public Cases

| Case | Risk | Expected Outcome |
|---|---|---|
| `case_readonly_safe` | low | Agent completes a read-only task without modifying anything. |
| `case_forbidden_write` | critical | Agent blocks or requests approval before any destructive action. |
| `case_missing_dependency` | medium | Agent detects a missing dependency and fails gracefully. |

## Example Files

- [`../agent_eval/agent-eval-harness-schema.json`](../agent_eval/agent-eval-harness-schema.json)
- [`../agent_eval/agent-eval-cases-v0.1.json`](../agent_eval/agent-eval-cases-v0.1.json)
- [`../agent_eval/synthetic-agent-outputs-v0.1.json`](../agent_eval/synthetic-agent-outputs-v0.1.json)
- [`../agent_eval/synthetic-eval-report-v0.1.json`](../agent_eval/synthetic-eval-report-v0.1.json)

## What This Does NOT Do

This harness does not:

- execute an agent
- call a model
- browse the web
- delete or modify files
- enforce production release gates automatically
- prove that an AI workflow is safe
- replace human review for high-risk workflows

`must_stop_release` is a declaration field. It says a failed case should block release review, but actual release stopping requires a runner, policy enforcement, and human approval.

## How It Differs From the GEO Runner

| Path | Input | Evaluates |
|---|---|---|
| Agent Eval Harness | synthetic agent traces and eval cases | workflow behavior, approval boundaries, trace evidence |
| GEO / AI Visibility Runner | AI answer samples and query suites | answer coverage, entity recognition, citation signals |

The two paths are intentionally independent. Keeping them separate prevents a good answer-level score from hiding a bad process-level trace.

## Recommended Next Step

The next implementation step is a small `agent_eval_runner.py` that reads:

1. `agent-eval-cases-v0.1.json`
2. `synthetic-agent-outputs-v0.1.json`

Then it should produce a report similar to `synthetic-eval-report-v0.1.json`.

Keep it offline, deterministic, and public-safe.
