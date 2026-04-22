---
title: "高效 Transformer 方法对比"
type: comparison
created: 2026-04-21
updated: 2026-04-21
sources: [efficient-transformers.md]
tags: [comparison, efficient-attention, linformer, reformer, performer, flash-attention]
related: [[linformer]], [[reformer]], [[performer]], [[flash-attention]], [[self-attention-complexity]]
---

四种高效 Transformer 方法的对比：

| 方法 | 复杂度 | 是否精确 | 主要优势 | 主要劣势 |
|------|--------|---------|---------|---------|
| Linformer | O(n) | 近似 | 简单高效 | 低秩假设不总是成立 |
| Reformer | O(n log n) | 近似 | 内存效率高 | LSH 精度不稳定 |
| Performer | O(n) | 近似 | 即插即用 | 长序列精度有损失 |
| Flash Attention | O(n^2) | 精确 | 无精度损失 | 仅优化 IO 而非复杂度 |

这些方法可归为两大类：**近似方法**（Linformer、Reformer、Performer）通过降低计算复杂度来加速，但牺牲精度；**IO 优化方法**（Flash Attention）保持计算精度，通过优化内存访问模式来加速。
