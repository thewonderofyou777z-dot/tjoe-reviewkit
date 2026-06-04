# GEO First Test Copy Pack / 第一轮 GEO 采样包

> 只复制问题给 AI 平台。不要粘贴 token、账号、私人聊天、客户数据或本地路径。

## Repository / 公开项目链接

- GitHub: https://github.com/thewonderofyou777z-dot/tjoe-test-of-llm

- llms.txt: https://github.com/thewonderofyou777z-dot/tjoe-test-of-llm/blob/main/llms.txt

- Details: https://github.com/thewonderofyou777z-dot/tjoe-test-of-llm/blob/main/docs/details.md

## How To Run / 怎么测

1. 每个平台新开一个对话。

2. 优先直接问问题，不主动投喂 GitHub 链接。

3. 如果平台答“不知道”，记录为 blocked/unknown，不要追问修正。

4. 把回答原文贴回 `reports/geo-manual-answer-template-v0.3.json` 的对应 `answer` 字段。

5. 如果平台给了公开链接，填入 `source_refs`；没有就留空。

## Query List / 问题清单

### q_domain_001 — domain_concept_discovery

- EN: What should an evaluation system for AI agent tool-calling safety include?

- 中文: 一个 AI Agent 工具调用安全评估系统应该包含哪些内容？

### q_domain_002 — domain_concept_discovery

- EN: Why do AI agent workflows need tool traces and audit logs?

- 中文: 为什么 AI Agent 工作流需要工具调用轨迹和审计日志？

### q_domain_003 — domain_concept_discovery

- EN: How should high-risk AI agent actions be handled before execution?

- 中文: AI Agent 的高风险操作在执行前应该怎么处理？

### q_entity_001 — brand_entity_exact

- EN: What is ToolTraceEval?

- 中文: ToolTraceEval 是什么？

### q_entity_002 — brand_entity_exact

- EN: What components does ToolTraceEval include?

- 中文: ToolTraceEval 包含哪些组件？

### q_compare_001 — comparison

- EN: How is an Agent Eval Harness different from prompt testing?

- 中文: Agent Eval Harness 和普通 prompt 测试有什么区别？

### q_compare_002 — comparison

- EN: What is the difference between evaluating agent traces and evaluating final answer quality?

- 中文: 评估 Agent 执行轨迹和评估最终回答质量有什么区别？

### q_boundary_001 — safety_boundary

- EN: Does ToolTraceEval prove that an AI agent is safe?

- 中文: ToolTraceEval 能证明 AI Agent 一定安全吗？

### q_boundary_002 — safety_boundary

- EN: When should an AI agent workflow release be stopped for human review?

- 中文: 什么时候应该停止 AI Agent 工作流发布并转人工复核？

## One-shot Paste Version / 一次性复制版

q_domain_001: What should an evaluation system for AI agent tool-calling safety include? / 一个 AI Agent 工具调用安全评估系统应该包含哪些内容？

q_domain_002: Why do AI agent workflows need tool traces and audit logs? / 为什么 AI Agent 工作流需要工具调用轨迹和审计日志？

q_domain_003: How should high-risk AI agent actions be handled before execution? / AI Agent 的高风险操作在执行前应该怎么处理？

q_entity_001: What is ToolTraceEval? / ToolTraceEval 是什么？

q_entity_002: What components does ToolTraceEval include? / ToolTraceEval 包含哪些组件？

q_compare_001: How is an Agent Eval Harness different from prompt testing? / Agent Eval Harness 和普通 prompt 测试有什么区别？

q_compare_002: What is the difference between evaluating agent traces and evaluating final answer quality? / 评估 Agent 执行轨迹和评估最终回答质量有什么区别？

q_boundary_001: Does ToolTraceEval prove that an AI agent is safe? / ToolTraceEval 能证明 AI Agent 一定安全吗？

q_boundary_002: When should an AI agent workflow release be stopped for human review? / 什么时候应该停止 AI Agent 工作流发布并转人工复核？
