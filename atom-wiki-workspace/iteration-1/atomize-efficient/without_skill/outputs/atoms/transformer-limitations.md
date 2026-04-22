---
title: "Transformer 的局限性"
type: comparison
created: 2026-04-21
updated: 2026-04-21
source: transformer-overview.md
source_section: "局限性"
tags:
  - transformer
  - limitations
  - complexity
  - long-sequence
  - computational-cost
  - generalization
related:
  - transformer-architecture
  - self-attention-mechanism
  - positional-encoding
---

# Transformer 的局限性

尽管 Transformer 取得了巨大成功，它仍存在以下已知局限。

## 1. 计算复杂度问题

- **自注意力的计算复杂度为 O(n^2)**
- 序列长度 n 增加时，计算和内存开销呈二次增长
- 对长序列处理效率低
- 这催生了高效注意力变体的研究（如 Linformer、Performer 等）

## 2. 位置编码泛化问题

- 位置编码对**超出训练长度的序列**泛化能力有限
- 训练时见过的最大序列长度限制了推理时的有效长度
- 虽然存在可扩展位置编码方案（如 ALiBi、RoPE），原始正弦编码的泛化性不足

## 3. 资源需求问题

- 模型参数量大
- 需要大量数据训练
- 需要大量算力训练
- 这使得大模型训练成为少数机构的特权，引发对 AI 民主化的担忧

## ⚠️ 矛盾标记

> **与 efficient-transformers.md 存在矛盾**
>
> 本文（来源一）将 O(n^2) 复杂度列为"对长序列处理效率低"的主要局限。
> 第二来源（efficient-transformers.md）指出：对于常见序列长度（512-4096 tokens），标准注意力的计算速度通常足够，O(n^2) 复杂度问题并非总是瓶颈。Flash Attention 的 IO 优化在此场景下反而带来更显著的加速效果。近似方法仅在超长序列（10K+ tokens）场景下才展现明显优势。
>
> **综合判断：** 两来源并非完全矛盾，而是视角不同——O(n^2) 确实是理论上的主要局限，但在实际常用序列长度下，计算速度并非主要瓶颈，IO 访问模式优化（如 Flash Attention）更为关键。在超长序列场景下，O(n^2) 的局限才显著体现。
>
> 详见 → [[on2-complexity-debate]]

## 标签

#transformer #limitations #complexity #O(n^2) #long-sequence #computational-cost #generalization #矛盾已标记

## 交叉引用

- [[on2-complexity-debate]] - 关于 O(n^2) 复杂度是否为真正瓶颈的详细讨论
- [[efficient-transformer-flash-attention]] - Flash Attention 通过 IO 优化而非近似来加速
- [[efficient-transformer-comparison]] - 各高效方法的复杂度与精度比较
- [[self-attention-mechanism]] - O(n^2) 复杂度的来源
