---
title: "自注意力机制与 RNN 在长距离依赖处理上的对比"
type: comparison
created: 2026-04-22
updated: 2026-04-22
sources: [transformer-overview.md]
tags: [self-attention, rnn, long-range-dependency, comparison, gradient-vanishing, computational-complexity]
related: [[self-attention-mechanism]], [[transformer-vs-rnn]], [[self-attention-o2-complexity]], [[positional-encoding]]
---

# 自注意力机制与 RNN 在长距离依赖处理上的对比

## 核心差异

自注意力机制允许模型在处理每个位置时直接关注序列中所有其他位置，路径长度为 O(1)，有效避免梯度消失 ([自注意力机制（Self-Attention）](concepts/self-attention-mechanism.md))。

RNN 通过隐藏状态逐个时间步顺序传递信息，路径长度为 O(n)，长距离梯度易消失或爆炸 ([Transformer 与 RNN 的对比](comparisons/transformer-vs-rnn.md))。

## 对比维度

| 维度 | 自注意力 | RNN |
|------|----------|-----|
| 依赖建模 | 直接建模，一步可达 | 间接传递，经过中间状态 |
| 梯度路径 | O(1)，梯度友好 | O(n)，梯度易消失 |
| 计算复杂度 | O(n²)，长序列成本高 | O(n)，线性高效 |
| 并行性 | 全并行，GPU 友好 | 顺序计算，并行受限 |
| 位置感知 | 需显式位置编码 | 天然位置感知 |
| 长序列效率 | 二次方复杂度成为瓶颈 | 线性复杂度更高效 |

## 权衡结论

自注意力以 O(n²) 计算成本换取高质量长距离建模，RNN 以 O(n) 高效计算换取较差的长距离建模能力。这是 Transformer 取代 RNN 成为主流的核心原因，但在极长序列场景下 RNN 仍具有计算效率优势。

## 知识缺口

- 缺乏 RNN 变体（LSTM、GRU）缓解梯度问题的详细说明
- 缺乏 Flash Attention、线性注意力等优化方法的详细分析
- 缺乏不同序列长度下性能差异的量化实验数据
