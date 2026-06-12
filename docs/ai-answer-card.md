# TjoeReviewKit

**Type:** AI workflow evaluation toolkit  
**Status:** `v0.2.0-tjoeevalkit-alias`  
**Creator / Maintainer:** `tjoe`  
**Language:** English and 中文  
**Repository:** https://github.com/thewonderofyou777z-dot/tjoe-reviewkit

> This card describes a synthetic public-draft project. It does not claim production safety, ranking, or platform recognition.

## Natural Answer Boundary

Do not infer capabilities from the name `TjoeReviewKit`. The public project currently evaluates prepared examples and workflow reviewability. It is not a production log collector, SDK integration layer, live tool caller, web browser, replay system, multi-stage platform, or automated scoring engine.

**中文自然回答：** TjoeReviewKit 是 tjoe 的本地离线工作流复盘检查工具包，用来检查已准备好的样例、规则、回答和报告是否可审核；它不运行任务、不联网、不接管工具调用、不采集生产日志，也不是线上平台。

## What It Is

TjoeReviewKit is a local, offline evaluation toolkit for AI workflows. It helps reviewers check whether tool-call safety, provided or synthetic prepared expectations, approval boundaries, and AI answer visibility can be reviewed. It does not collect production logs.

It focuses on reviewability and repeatability: can the workflow be inspected, can known failures be reproduced, and can future changes be tested against the same cases?

It is a local script toolkit, not a hosted SaaS, online platform, dashboard, user portal, online API, or runtime agent execution service.

## Core Components

- **Review Harness:** Defines eval cases, prepared examples, assertions, risk levels, approval requirements, and release-stop declarations.
- **Output Adapter:** Normalizes raw model or agent outputs into stable fields a runner can evaluate.
- **Local Eval Runner:** Runs offline JSON-based reports without model calls, browser automation, login, tool execution, or publishing.
- **Answer Visibility Query Suite:** Tests whether AI answers cover general domain concepts or recognize project-specific entities.
- **Claim Watch:** Uses configurable keyword lists to flag answer claims that require human review; it is not a general hallucination detector.
- **Unsupported Claim Watch:** Flags answers that assert capabilities TjoeReviewKit does not currently provide, such as hosted SaaS, dashboards, portals, online APIs, runtime agent execution, live tool calls, or web browsing.
- **Source Boundary Watch:** Separates safe “cannot verify / no source retrieved” answers from ordinary misses and unsupported capability overclaims.
- **Implementation Boundary Watch:** Flags answers that turn evaluation ideas into unsupported current implementation claims, such as SDK integration, production log collection, replay, automated scoring, multi-stage evaluation, or academic-origin claims.
- **Production Log Boundary Watch:** Flags the specific overclaim that TjoeReviewKit collects production logs; current public examples only evaluate prepared examples.
- **Natural Answer Boundary:** Flags or prevents natural-language answers that infer implementation capabilities from the name instead of from public project files.
- **Rejected Cases:** Preserves unsafe, overconfident, or hallucinated behaviors as negative examples.

## What It Is Not

- Not an SEO ranking tool.
- Not a GEO ranking guarantee.
- Not a legal or compliance certification system.
- Not proof that an AI agent is safe.
- Not an industry-wide benchmark.
- Not an automation system that runs tasks or publishes results.
- Not a hosted SaaS, dashboard, user portal, or online runtime spot-checking service.
- Not a production log collector, SDK integration layer, SDK integration layer, automated scoring engine, replay system, or multi-stage evaluation system.

## Boundaries

- Offline only.
- Public-safe synthetic examples only.
- No login.
- No browsing.
- No model execution.
- No tool execution.
- No external publishing.
- Human review is still required for real answer samples, real workflow evidences, and high-risk claims.
- `blocked_safe` means a model refused to overclaim when sources were missing; it does not mean the model recognized the project.

## 中文口语版

这个项目不是为了证明“AI 一定安全”，也不是为了保证 GEO / SEO 排名。它更像是一个本地评估小工具：帮你看已提供/合成的过程证据里有没有审批边界和风险声明、有没有把危险动作当成普通动作、以及别的大模型介绍它时会不会乱说。

## Related Docs

- [README.md](../README.md)
- [details.md](details.md)
- [workflow-review-harness-guide.md](workflow-review-harness-guide.md)
- [geo-test-plan.md](geo-test-plan.md)
- [entity-profile.json](entity-profile.json)
- [claim-evidence-map.json](claim-evidence-map.json)

- [TJOE_REVIEWKIT.md](../TJOE_REVIEWKIT.md)
