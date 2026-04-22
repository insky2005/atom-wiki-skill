---
title: "Linformer"
type: concept
created: 2026-04-22
updated: 2026-04-22
sources: [efficient-transformers.md]
tags: [linformer, efficient-attention, transformer, low-rank, linear-complexity]
related: [[self-attention-mechanism]], [[self-attention-o2-complexity]], [[efficient-transformers-comparison]], [[on2-not-always-bottleneck]]
---

Linformer 是一种高效 Transformer 变体，通过将自注意力的键（Key）和值（Value）矩阵通过低秩投影进行压缩，将计算复杂度从 O(n²) 降至 O(n)。

其核心假设是注意力矩阵具有低秩特性，可以通过 k 维投影（k << n）近似原始注意力分布。这种方法避免了计算完整的 n×n 注意力矩阵。

在长文档分类任务上，Linformer 比 BERT 快 5-10 倍。然而，其低秩假设并非在所有场景下都成立，这限制了其通用性。

Linformer 属于**近似方法**，通过降低计算复杂度来加速，但以牺牲一定精度为代价。在需要处理超长序列（10K+ tokens）的场景下才展现出明显优势。
