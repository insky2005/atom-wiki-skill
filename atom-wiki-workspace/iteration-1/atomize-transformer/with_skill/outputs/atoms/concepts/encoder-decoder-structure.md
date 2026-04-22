---
title: "编码器-解码器结构"
type: concept
created: 2026-04-21
updated: 2026-04-21
sources: [transformer-overview.md]
tags: [encoder-decoder, transformer, sequence-to-sequence, deep-learning]
related: [[transformer]], [[self-attention-mechanism]], [[feed-forward-network]]
---

原始 Transformer 采用编码器-解码器结构，适用于序列到序列的任务（如机器翻译）。

**编码器**：由 6 层相同的层堆叠而成，每层包含两个子层——多头自注意力子层和前馈网络子层，均使用残差连接和层归一化。编码器负责将输入序列编码为连续的表征。

**解码器**：同样 6 层，但增加了第三个子层——编码器-解码器注意力层。在该层中，查询来自前一解码器层，键和值来自编码器输出，实现解码器对编码器输出的关注。解码器还使用了掩码自注意力（masked self-attention），防止在生成时关注未来位置，确保自回归特性。

这种编码器-解码器的分工使得 Transformer 可以灵活地处理各种序列转换任务。
