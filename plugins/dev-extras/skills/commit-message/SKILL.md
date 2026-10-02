---
name: commit-message
description: 按 Conventional Commits 为当前改动写提交信息：类型、范围、一句话标题和说明原因的正文。准备提交代码时使用。
metadata:
  agentflow-requires-tools: [git.diff, git.status]
---

# 提交信息

先用 `git.status` 和 `git.diff` 看清这次提交包含哪些改动，再写：

```
<类型>(<范围>): <标题>

<正文：为什么改、改了什么行为；不是逐行复述 diff>

<脚注：BREAKING CHANGE: …、关联的需求编号>
```

- **类型**：`feat` 新功能、`fix` 修复、`refactor` 不改行为的重构、`perf` 性能、`test` 测试、`docs` 文档、`build` / `ci` 构建与流水线、`chore` 杂项。
- **范围**：受影响的模块或目录名，如 `api`、`web`、`auth`；跨很多模块时省略。
- **标题**：祈使句、不超过 72 个字符、结尾不加句号，说「做了什么」，如 `feat(api): 新增版本查询接口`。
- **正文**：说明动机和取舍；有不兼容的地方写 `BREAKING CHANGE:` 加迁移方法；有需求编号写在脚注，如 `Refs: KLINE-14`。

一次提交只做一件事。改动里混了不相关的内容时，先拆开提交。
