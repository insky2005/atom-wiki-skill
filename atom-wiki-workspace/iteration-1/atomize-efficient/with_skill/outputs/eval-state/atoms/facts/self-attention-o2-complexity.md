---
title: "自注意力的 O(n²) 计算复杂度"
type: fact
created: 2026-04-21
updated: 2026-04-21
sources: [transformer-overview.md, efficient-transformers.md]
tags: [self-attention, complexity, transformer, scalability]
related: [[self-attention-mechanism]], [[transformer-resource-requirements]]
---

自注意力机制的计算复杂度为 O(n²)，其中 n 为输入序列长度。这意味着当序列长度翻倍时，计算量增加约 4 倍。

这一复杂度来源于自注意力需要计算序列中每对位置之间的相似度：n 个查询与 n 个键的点积产生 n×n 的注意力矩阵。这使得 Transformer 在处理长序列时效率显著降低，是 Transformer 的主要局限性之一。

近年来，Flash Attention、线性注意力等改进方法致力于缓解这一复杂度瓶颈。

> **CONTRADICTION** (added 2026-04-22)
> This atom claims: "O(n²) 复杂度使得 Transformer 在处理长序列时效率显著降低，是 Transformer 的主要局限性之一"
> [[efficient-transformers-comparison]] and [[on2-not-always-bottleneck]] claim: "自注意力的 O(n²) 复杂度问题在实际应用中并非总是瓶颈。对于常见的序列长度（512-4096 tokens），标准注意力的计算速度通常足够"
> Resolution: both valid in different contexts — O(n²) 确实是超长序列（10K+ tokens）的瓶颈，但对于常见长度（512-4096），IO 优化（如 Flash Attention）比降低复杂度更有效
