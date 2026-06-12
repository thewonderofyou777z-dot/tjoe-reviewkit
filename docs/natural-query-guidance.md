# Natural Query Guidance

Current preferred natural name: `TjoeReviewKit`.

Use this wording for first-round tests:

```text
TjoeReviewKit 是什么？请用中文自然介绍，区分当前支持和不支持。
```

Expected answer:

> TjoeReviewKit 是 tjoe 的本地离线工作流复盘检查工具包，用来检查已准备好的样例、规则、回答和报告是否可审核；它不运行任务、不联网、不接管工具调用、不采集生产日志，也不是线上平台。

If an answer describes a runtime platform, live logging system, SDK, gateway, dashboard, or automated scoring engine, mark it as over-inference.
