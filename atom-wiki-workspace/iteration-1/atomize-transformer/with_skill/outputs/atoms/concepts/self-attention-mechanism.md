---
title: "自注意力机制（Self-Attention）"
type: concept
created: 2026-04-21
updated: 2026-04-21
sources: [transformer-overview.md]
tags: [self-attention, transformer, attention-mechanism, deep-learning]
related: [[transformer]], [[multi-head-attention]], [[self-attention-o2-complexity]]
---

自注意力机制是 Transformer 的核心计算机制，允许模型在处理每个位置时，直接关注输入序列中的所有其他位置。

其计算公式为：

**Attention(Q, K, V) = softmax(QK^T / sqrt(d_k)) V**

其中 Q（查询）、K（键）、V（值）是输入的线性变换，d_k 是键向量的维度。除以 sqrt(d_k) 是为了防止点积过大导致 softmax 梯度消失。

自注意力的本质是一种加权求和：每个位置的输出是所有位置的值向量的加权和，权重由查询与键的相似度决定。这使得模型能够捕捉序列中任意两个位置之间的依赖关系，无论它们距离多远。

该机制的计算复杂度为 [[self-attention-o2-complexity|O(n²)]]，这是 Transformer 处理长序列时的主要瓶颈。
