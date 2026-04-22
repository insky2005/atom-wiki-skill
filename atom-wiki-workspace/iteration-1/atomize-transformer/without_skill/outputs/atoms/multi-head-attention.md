---
title: "多头注意力（Multi-Head Attention）"
type: concept
created: 2026-04-21
updated: 2026-04-21
source: transformer-overview.md
source_section: "核心组件 > 多头注意力"
tags:
  - multi-head-attention
  - attention-mechanism
  - transformer
  - parallel-computation
  - subspace-projection
related:
  - transformer-architecture
  - self-attention-mechanism
  - encoder-decoder-structure
---

# 多头注意力（Multi-Head Attention）

多头注意力将自注意力机制扩展到多个子空间并行计算，让模型能同时关注不同位置的不同表征子空间中的信息。

## 工作原理

1. 将 Q、K、V 分别投影到 h 个不同的子空间
2. 在每个子空间中并行计算注意力
3. 将 h 个注意力结果拼接（concatenate）
4. 对拼接结果进行线性变换，得到最终输出

## 原论文参数

- **头数**：h = 8（原论文设置）

## 核心优势

- **多子空间表征**：不同头可以关注不同的语义关系
- **并行计算**：多个头的计算可以并行执行
- **丰富表征**：拼接后的结果包含多角度的信息

## 与自注意力的关系

多头注意力是自注意力机制的扩展：每个头本质上就是一个独立的自注意力计算，但使用不同的投影矩阵将输入映射到不同的子空间。
