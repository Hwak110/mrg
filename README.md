# MRG

**Minimal Engineering Context for LLM**

MRG 研究一个问题：当模型能够自主完成软件工程时，人类还需要提供多少工程方法？

核心原则：

> Human attention is the scarce resource.

MRG 的目标不是让 AI 产生更多代码，而是把人类从代码生产和逐行检查中释放出来，只把需求、产品取舍、高风险决策、架构方向和不可逆操作留给人类。

```text
Human intent / decision → MRG → Model decides how
                                  ↓
                       Code · Tests · Diagram
                                  ↓
                              Evidence
                                  ↓
                         Need human? → Human / Done
```

## 唯一 Skill

[`skills/architecture/SKILL.md`](skills/architecture/SKILL.md) 只描述工程目标和结果，不灌输某个模型的错误经验、固定流程或 Java 设计模式。

模型可以自行决定是否计划、拆分、调用其他模型、评审、测试、回退或绘图。简单问题保持简单，复杂问题才引入必要结构。

## 成功标准

在相同任务上逐步减少人工 Skill 和先验规则，模型仍能稳定产出合理的架构设计、可工作的实现、自动验证证据、与实现一致的架构图，以及面向人的变更摘要、风险和待决策事项。

Planner、Coder、Evaluator、Quality Gate 等角色可以作为实验基线，但不是 MRG 的规定。
