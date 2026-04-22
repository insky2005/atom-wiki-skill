---
title: "Reformer"
type: concept
created: 2026-04-22
updated: 2026-04-22
sources: [efficient-transformers.md]
tags: [reformer, efficient-attention, transformer, lsh, reversible-residual]
related: [[self-attention-mechanism]], [[self-attention-o2-complexity]], [[efficient-transformers-comparison]], [[on2-not-always-bottleneck]]
---

Reformer 是一种高效 Transformer 变体，使用局部敏感哈希（LSH）注意力机制，只计算最相似的键值对，将计算复杂度从 O(n²) 降至 O(n log n)。

除了 LSH 注意力，Reformer 还采用可逆残差层（Reversible Residual Layers）替代标准残差连接，大幅减少内存占用，使得可以训练更深的网络。

然而，LSH 注意力在实践中有时精度下降明显，稳定性不如标准注意力。这种近似方法在需要处理超长序列（10K+ tokens）的场景下才展现出明显优势。

Reformer 属于**近似方法**，通过降低计算复杂度来加速，但以牺牲一定精度为代价。
