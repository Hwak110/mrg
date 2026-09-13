# MRG 架构

## 定位

MRG 是 **Minimal Engineering Context for LLM**：给模型问题、代码、工具和必要上下文，然后尽量不妨碍模型自行完成工程工作。

核心理念：

> Less instruction. More capability.

## 组成

```text
mrg/
├── README.md
├── ARCHITECTURE.md
└── skills/
    └── architecture/
        └── SKILL.md
```

仓库只提供一个架构 Skill，覆盖问题理解、架构判断、技术实现、验证和架构图一致性。

## 不预设的内容

MRG 不强制使用 Planner、Coder、Reviewer、Evaluator 等 Agent 角色，不强制 spec、反馈日志、DAG、设计模式、DDD、Clean Architecture 或某种 Java 风格。

这些选择应由模型根据任务、代码事实、风险和人类约束自行判断。

## 运行时边界

运行时提供模型完成工作所需的真实能力：文件系统、Git、终端、构建与测试、源代码和项目上下文、架构产物、人类决策。

模型可以自行决定何时阅读、计划、修改、验证、绘图、回退或询问人类。

## 成功标准

MRG 的目标不是让模型遵循更多规则，而是在足够上下文下观察模型能否正确理解系统、为复杂问题设计合理结构、对简单问题保持简单、将设计自然落到代码，并让架构图与实现保持一致。
