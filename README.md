# MRG

**Minimal Engineering Context for LLM**

MRG 不试图再造一个复杂的 Agent 工作流框架。它只提供一个最小的 `architecture` Skill，让模型在真实代码、工具和约束中自行完成：

```text
需求 → 理解 → 架构判断 → 实现 → 验证 → 架构图
```

模型可以根据任务复杂度自行决定是否需要计划、拆分、评审、测试或绘图。简单问题保持简单，复杂问题才引入必要的结构。

## 文件

- [`ARCHITECTURE.md`](ARCHITECTURE.md)：MRG 的定位、边界和设计原则
- [`skills/architecture/SKILL.md`](skills/architecture/SKILL.md)：唯一的工程 Skill

核心理念：

> 给模型问题、代码、工具和必要上下文，然后别妨碍它。
