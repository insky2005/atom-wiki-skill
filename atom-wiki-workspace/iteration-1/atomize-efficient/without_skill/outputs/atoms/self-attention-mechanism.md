---
title: "自注意力机制（Self-Attention）"
type: concept
created: 2026-04-21
updated: 2026-04-21
source: transformer-overview.md
source_section: "核心组件 > 自注意力机制"
tags:
  - self-attention
  - attention-mechanism
  - transformer
  - neural-network
  - softmax
related:
  - transformer-architecture
  - multi-head-attention
  - encoder-decoder-structure
---

# 自注意力机制（Self-Attention）

自注意力机制允许模型在处理每个位置时，直接关注输入序列中的所有其他位置。

## 计算公式

```
Attention(Q, K, V) = softmax(QK^T / sqrt(d_k)) V
```

## 参数说明

| 符号 | 含义 |
|------|------|
| Q | 查询（Query），输入的线性变换 |
| K | 键（Key），输入的线性变换 |
| V | 值（Value），输入的线性变换 |
| d_k | 键向量的维度 |

## 关键设计

- **缩放因子**：除以 `sqrt(d_k)` 是为了防止点积过大导致 softmax 梯度消失
- **全局感受野**：每个位置可以直接关注序列中的所有其他位置，无需像 RNN 那样逐步传递信息

## 与其他注意力机制的关系

自注意力机制是多头注意力（Multi-Head Attention）的基础构建单元。多头注意力将自注意力扩展到多个子空间并行计算。
