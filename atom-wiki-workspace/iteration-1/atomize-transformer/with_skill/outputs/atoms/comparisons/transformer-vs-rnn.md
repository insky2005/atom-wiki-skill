---
title: "Transformer 与 RNN 的对比"
type: comparison
created: 2026-04-21
updated: 2026-04-21
sources: [transformer-overview.md]
tags: [transformer, rnn, comparison, deep-learning]
related: [[transformer]], [[self-attention-mechanism]]
---

| 维度 | Transformer | RNN |
|------|-------------|-----|
| 计算方式 | 并行计算，所有位置同时处理 | 顺序计算，逐个时间步处理 |
| 长距离依赖 | 通过自注意力直接建模，无需经过中间状态 | 依赖隐藏状态传递，长距离梯度易消失 |
| 训练速度 | 可充分利用 GPU 并行性，训练速度快 | 顺序依赖限制了并行化，训练速度慢 |
| 序列长度 | O(n²) 复杂度，长序列成本高 | O(n) 复杂度，但效果随距离衰减 |

相比 RNN，Transformer 的主要优势在于**并行计算能力**和**长距离依赖建模**。并行计算使 Transformer 能够高效利用现代硬件加速器，大幅缩短训练时间。自注意力机制使模型能够直接关注序列中任意位置，避免了 RNN 中长期依赖梯度消失的问题。

然而，Transformer 的 [[self-attention-o2-complexity|二次方复杂度]]使其在处理极长序列时不如 RNN 高效。
