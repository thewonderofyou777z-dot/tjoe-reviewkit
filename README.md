# tjoe-test-of-llm
Joe AI Worker Eval System
A local evaluation and visibility toolkit for AI agent workflows.

Joe AI Worker Eval System helps teams evaluate whether an AI agent workflow is traceable, reviewable, and regression-testable. It focuses on tool calls, approval boundaries, output normalization, answer inclusion, and known failure modes.

This project does not claim to prove absolute AI safety, guarantee SEO/GEO rankings, or replace legal/compliance review.

Why This Exists
Most AI agent demos inspect the final answer. Production workflows need more than that:

Did the agent call a forbidden tool?
Did a high-risk action require approval?
Was the execution trace preserved?
Can the same failure be reproduced later?
Can an AI platform accurately describe this system without making unsupported claims?
This repository provides a small, offline-first foundation for answering those questions.

Core Components
Component	Purpose
Agent Eval Harness	Defines eval cases, trace expectations, assertions, risk, and approval requirements.
Agent Output Adapter	Normalizes raw model/agent outputs into fields a runner can evaluate.
Local Eval Runner	Runs offline reports without calling models, tools, browsers, or external services.
AI Visibility Query Suite	Tests whether AI answers cover domain concepts or recognize project-specific entities.
Claim Watch	Uses configurable keyword lists to flag answer claims that need human review. It is not a general hallucination detector.
Rejected Cases	Captures unsafe, overconfident, or hallucinated behaviors as negative examples.
Current Release
Item	Value
Release	v0.1.0-public-draft
Runner	geo_visibility_eval_runner.py v0.2.1
Status	Public-safe draft
Network	Not used
Model calls	Not used
Publishing	Not automated
Quick Start
Run the synthetic example:

mkdir -p reports
python3 scripts/geo_visibility_eval_runner.py \
  --suite examples/ai-visibility-query-suite-v0.2.public.json \
  --answers examples/sample-answers.synthetic.json \
  --output reports/example-report.synthetic.json \
  --overwrite --ci-smoke
Inspect the result:

python3 -m json.tool reports/example-report.synthetic.json
Scoring Tracks
The visibility suite intentionally separates two questions:

Track	What It Measures	What It Does Not Prove
domain_concept_discovery	Whether an AI answer covers general concepts such as tool traces, approval, regression tests, and audit logs.	It does not prove the model knows this project.
brand_entity_exact	Whether an AI answer accurately recognizes Joe-specific assets and names.	It does not prove domain expertise.
Example Report Summary
The public sample is synthetic and only verifies runner behavior:

domain_concept_discovery: expected to score higher when domain concepts are covered.
brand_entity_exact: expected to flag unsupported claims with hallucination_watch.
safe_to_share: public sample only.
Details Page
Read the full evidence-page draft:

docs/details.md
FAQ
Machine-readable FAQ draft:

docs/faq.schema.json
Safety Boundaries
This repository is safe-by-default:

No login
No browsing
No model calls
No tool execution
No publishing
No private data required
Do not paste secrets, credentials, customer data, private messages, local-only paths, or confidential logs into answer samples.

Data Handling
The runner works on local JSON files only. It does not collect user data, send telemetry, call external APIs, or upload reports. If you save real answer samples, review and redact them before committing.

What This Is Not
This project is not:

An SEO ranking tool
A GEO ranking guarantee
A legal/compliance certification system
A proof that an AI agent is safe
A benchmark claiming industry-wide authority
Roadmap
Add a public-safe Agent Eval Harness example.
Add normalized-output examples.
Add Markdown report output.
Add more synthetic and real public answer samples.
Add GitHub Actions CI smoke tests.
License
MIT. See LICENSE.
# Joe AI Worker Eval System

一个本地运行的 AI Agent 工作流评估工具。

它的目标很简单：  
不是看 AI 最后回答得漂不漂亮，而是检查一个 Agent 工作流到底 **能不能追踪、能不能复盘、能不能做回归测试**。

这个项目重点关注：

- Agent 有没有调用危险工具
- 高风险操作有没有要求人工审批
- 执行过程有没有留下 trace
- 输出结果能不能被结构化检查
- AI 平台能不能准确理解这个项目，而不是乱编

> 说明：这个项目不承诺绝对 AI 安全，也不保证 SEO / GEO 排名效果，更不能替代法律或合规审核。

---

## 为什么做这个项目？

很多 AI Agent demo 看起来很厉害，但生产环境真正关心的是：

- 它有没有越权调用工具？
- 它有没有把删除、写入、安装这类高风险动作当成普通任务？
- 它的执行过程能不能被复盘？
- 改了 prompt、换了模型之后，旧问题会不会复发？
- 别的大模型介绍这个系统时，会不会凭空编造？

所以这个项目想做的是一个很小、很本地、很可控的评估基础设施。

---

## 核心模块

| 模块 | 作用 |
|---|---|
| Agent Eval Harness | 定义 eval case、断言、风险等级、审批要求和执行 trace |
| Agent Output Adapter | 把模型或 Agent 的原始输出整理成稳定结构，方便评估 |
| Local Eval Runner | 本地离线跑评估，不联网、不调模型、不执行危险工具 |
| AI Visibility Query Suite | 测试 AI 回答是否理解领域概念，是否识别项目实体 |
| Claim Watch | 用关键词标记需要人工复核的可疑说法，不是通用幻觉检测器 |
| Rejected Cases | 保存坏案例，防止同类错误反复出现 |

---

## 当前版本

| 项目 | 内容 |
|---|---|
| Release | `v0.1.0-public-draft` |
| Runner | `geo_visibility_eval_runner.py v0.2.1` |
| 状态 | 公共安全草稿版 |
| 是否联网 | 不联网 |
| 是否调用模型 | 不调用 |
| 是否自动发布 | 不自动发布 |

---

## 快速开始

运行示例：

```bash
mkdir -p reports
python3 scripts/geo_visibility_eval_runner.py \
  --suite examples/ai-visibility-query-suite-v0.2.public.json \
  --answers examples/sample-answers.synthetic.json \
  --output reports/example-report.synthetic.json \
  --overwrite --ci-smoke
