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
