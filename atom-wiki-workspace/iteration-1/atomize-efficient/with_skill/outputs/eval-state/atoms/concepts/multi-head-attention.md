---
title: "多头注意力（Multi-Head Attention）"
type: concept
created: 2026-04-21
updated: 2026-04-21
sources: [transformer-overview.md]
tags: [multi-head-attention, transformer, attention-mechanism, deep-learning]
related: [[transformer]], [[self-attention-mechanism]]
---

多头注意力是自注意力机制的扩展形式，将 Q、K、V 分别投影到 h 个不同的子空间，并行计算注意力，然后将结果拼接并线性变换。

这一设计让模型能同时关注不同位置的不同表征子空间中的信息。每个注意力头可以学习关注不同类型的依赖关系——例如一个头关注语法关系，另一个头关注语义关系。

原始 Transformer 论文中使用 h=8 个头。多头注意力的计算成本与单头全维度注意力相近，但提供了更丰富的表征能力。
