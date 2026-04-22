---
title: "Performer"
type: concept
created: 2026-04-22
updated: 2026-04-22
sources: [efficient-transformers.md]
tags: [performer, efficient-attention, transformer, favor+, kernel-approximation]
related: [[self-attention-mechanism]], [[self-attention-o2-complexity]], [[efficient-transformers-comparison]], [[on2-not-always-bottleneck]]
---

Performer 是一种高效 Transformer 变体，使用随机正交特征（FAVOR+）方法来近似 softmax 注意力核函数，实现线性时间复杂度 O(n)。

其优势在于不需要改变注意力结构，可以直接替换标准注意力模块，具有"即插即用"的特性。在蛋白质序列建模等超长序列任务中表现优异。

然而，Performer 在长序列任务中精度有一定损失。它属于**近似方法**，通过降低计算复杂度来加速，但以牺牲一定精度为代价。在需要处理超长序列（10K+ tokens）的场景下才展现出明显优势。
