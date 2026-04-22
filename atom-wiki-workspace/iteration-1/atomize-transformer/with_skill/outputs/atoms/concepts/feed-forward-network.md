---
title: "前馈网络（Feed-Forward Network）"
type: concept
created: 2026-04-21
updated: 2026-04-21
sources: [transformer-overview.md]
tags: [feed-forward-network, transformer, deep-learning]
related: [[transformer]], [[encoder-decoder-structure]]
---

每个 Transformer 层包含一个逐位置的前馈网络，由两个线性变换和 ReLU 激活组成：

**FFN(x) = max(0, xW₁ + b₁)W₂ + b₂**

前馈网络对每个位置独立应用相同的变换（即参数跨位置共享），其隐藏维度通常是模型维度的 4 倍。例如，若模型维度 d_model=512，则前馈网络的隐藏维度 d_ff=2048。

前馈网络的作用是在自注意力层完成信息交互后，对每个位置的表征进行非线性变换，增强模型的表达能力。它与自注意力层交替堆叠，构成 Transformer 的基本构建块。
