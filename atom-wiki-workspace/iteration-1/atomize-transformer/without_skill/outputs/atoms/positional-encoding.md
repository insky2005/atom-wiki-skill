---
title: "位置编码（Positional Encoding）"
type: concept
created: 2026-04-21
updated: 2026-04-21
source: transformer-overview.md
source_section: "核心组件 > 位置编码"
tags:
  - positional-encoding
  - transformer
  - sequence-modeling
  - sinusoidal
  - position-information
related:
  - transformer-architecture
  - transformer-limitations
---

# 位置编码（Positional Encoding）

由于 Transformer 不包含递归和卷积，它本身无法感知序列的位置信息。位置编码通过正弦和余弦函数生成固定编码，为模型提供位置信息。

## 问题背景

- Transformer 不含递归结构（不像 RNN 天然有序列顺序）
- Transformer 不含卷积结构（不像 CNN 有局部位置感知）
- 因此需要额外的机制来注入位置信息

## 解决方案

- 使用正弦（sin）和余弦（cos）函数生成固定编码
- 位置编码与词嵌入相加（element-wise addition）
- 这样模型在处理每个词时既包含语义信息也包含位置信息

## 局限性

- 对超出训练长度的序列泛化能力有限
- 这是 Transformer 的已知局限之一（参见 [[transformer-limitations]]）
