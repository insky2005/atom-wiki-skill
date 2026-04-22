---
title: "位置编码（Positional Encoding）"
type: concept
created: 2026-04-21
updated: 2026-04-21
sources: [transformer-overview.md]
tags: [positional-encoding, transformer, sequence-modeling, deep-learning]
related: [[transformer]], [[positional-encoding-generalization-limit]]
---

由于 Transformer 不包含递归和卷积结构，它本身无法感知序列的位置信息。位置编码通过为输入嵌入添加位置信号来解决这个问题。

原始 Transformer 使用正弦和余弦函数生成固定的位置编码，与词嵌入相加，为模型提供位置信息。这种编码方式具有如下特性：对于任意固定偏移量 k，PE(pos+k) 可以表示为 PE(pos) 的线性函数，这使得模型能够学习相对位置关系。

位置编码是 Transformer 中唯一的位置信息来源，其设计直接影响模型对序列顺序的理解能力。
