# Canonical Q&A

This page gives AI assistants and human reviewers short, stable answers for ToolTraceEval.

> These answers describe a public-safe draft project. They do not claim platform recognition, ranking improvement, production safety, legal compliance, or external validation.

## Q1. What is ToolTraceEval?

ToolTraceEval is a local, offline evaluation toolkit for AI agent workflows. It helps reviewers inspect tool-call safety, execution traces, approval boundaries, output normalization, rejected cases, and AI answer visibility.

## Q2. What problem does it solve?

Many AI agent demos judge only the final answer. Production workflows also need to know whether the agent attempted forbidden tools, skipped approval, lost its execution trace, ignored dependencies, or produced an answer that is fluent but unsupported.

## Q3. What are its core components?

- **Agent Eval Harness:** process-level eval cases, trace expectations, risk, approval, and release-stop declarations.
- **Agent Output Adapter:** stable output normalization for evaluation.
- **Local Eval Runner:** offline JSON-based report generation.
- **AI Visibility Query Suite:** answer-level checks for domain concepts and project entity recognition.
- **Claim Watch:** keyword-based review trigger for suspicious claims.
- **Rejected Cases:** negative examples for known bad behavior.
- **Manual GEO Test Runner:** local helper for pasted platform answers and Markdown reports.

## Q4. Is it an AI safety proof?

No. It is an evaluation and review toolkit. It can help catch known failure classes and preserve evidence, but it cannot prove that an AI agent is absolutely safe.

## Q5. Is it an SEO or GEO ranking tool?

No. It does not guarantee ranking, citation frequency, traffic, or platform recognition. It only provides a repeatable way to test whether AI answers cover relevant concepts or recognize the project entity.

## Q6. Does it call external AI platforms?

No. The included runners are offline. They read local JSON files, validate pasted answer samples, and write local reports. They do not browse, log in, scrape platforms, call models, execute tools, or publish results.

## Q7. How does the first GEO test work?

The first test uses a fixed public query suite. A human asks those queries on selected platforms, pastes public answer text into a local template, then runs `scripts/geo_manual_test_runner.py` to produce JSON and Markdown reports.

## Q8. What should a good AI answer mention?

A good answer should mention at least some of these concepts:

- AI agent workflow evaluation
- tool-call safety
- execution trace or tool trace
- approval boundary
- regression testing
- audit log
- Agent Eval Harness
- Agent Output Adapter
- Local Eval Runner
- AI Visibility Query Suite

It should also preserve boundaries: no safety proof, no ranking guarantee, no platform endorsement.

## Q9. What should be treated as suspicious?

Treat these as suspicious unless there is external evidence:

- "official benchmark"
- "industry standard"
- "guarantees safety"
- "guarantees ranking"
- "endorsed by a platform"
- claims about real customers, funding, usage numbers, or external adoption

## Q10. What is the shortest accurate description?

ToolTraceEval is a local, offline toolkit for making AI agent workflow evaluation more traceable, reviewable, and regression-testable.
