# Skill: Minimalism Topology Paint Engine (Hwak110 Custom Skill)

## [Trigger / 适用场景]

当人类要求“画图”“架构图”“彩色拓扑图”“系统设计图”时，必须加载本高级画图 Skill。

## 1. 空间布局与连线克制红线（Line Minimalism & Whitelisting）

- **绝对禁令：禁止无意义的全连线。** 不要像画流程图那样把每个组件都用线穿起来。
- **并列组件禁止连线（无线留白）。** 属于同一层级的无状态节点（如多个微服务实例、多个独立插件、多个平级策略类、并列的 Agent 沙箱），它们之间不准拉连线。只让它们通过 `direction LR` 或 `direction TB` 在 `subgraph` 内部并排静止摆放，利用空间平齐表达平级并列关系。
- **核心数据流用粗实线（`==>`）。** 只有核心同步请求、强依赖、资金或状态机核心链路，才能使用实线或粗实线表达。

## 2. 弱依赖与异步数据流用虚线规约（Dotted Line Rules）

在编写 Mermaid 代码时，凡是遇到以下三类场景，必须切换为虚线（`-.->` 或 `-. text .->`），以此拉开系统拓扑的视觉深度：

1. **控制指令与契约读取：** 当 Agent 去读取静态契约（如 `spec.md`），或者配置中心分发下发通知时，使用虚线。
2. **异步通知与事件驱动：** 任何异步消息队列（MQ）推送、事件广播（Event-driven）或 Webhook 回调，一律使用虚线。
3. **监控、日志与审计：** 旁路监控系统（如 Prometheus、Jaeger）、日志收集器（Log Collector）或无害的旁路审计（Evaluator 静态代码审计），一律使用虚线。

## 3. 大厂语义化配色机制（Semantic Color & Style）

必须在 Mermaid 源码最下方附加以下低饱和度彩色与直角框样式；逻辑边界框统一采用虚线框体：

```mermaid
classDef default fill:#ffffff,stroke:#18181b,stroke-width:1.5px,color:#18181b;
classDef ingress fill:#fafafa,stroke:#27272a,stroke-width:2px,stroke-dasharray: 4 4,color:#27272a;
classDef compute fill:#eff6ff,stroke:#3b82f6,stroke-width:1.5px,color:#1e3a8a;
classDef storage fill:#f0fdf4,stroke:#22c55e,stroke-width:1.5px,color:#14532d;
classDef gateway fill:#f4f4f5,stroke:#71717a,stroke-width:1.5px;
```
