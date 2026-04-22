---
title: "编码器-解码器结构（Encoder-Decoder）"
type: concept
created: 2026-04-21
updated: 2026-04-21
source: transformer-overview.md
source_section: "编码器-解码器结构"
tags:
  - encoder-decoder
  - transformer
  - seq2seq
  - residual-connection
  - layer-normalization
  - masked-attention
related:
  - transformer-architecture
  - self-attention-mechanism
  - multi-head-attention
  - feed-forward-network
---

# 编码器-解码器结构（Encoder-Decoder）

原始 Transformer 采用编码器-解码器结构，这是序列到序列（seq2seq）模型的经典架构。

## 编码器（Encoder）

- 由 **6 层**相同的层堆叠而成
- 每层包含两个子层：
  1. **多头自注意力子层**
  2. **前馈网络子层**
- 均使用**残差连接**和**层归一化**

## 解码器（Decoder）

- 同样 **6 层**
- 包含三个子层：
  1. **掩码自注意力子层**：防止关注未来位置（因果掩码）
  2. **编码器-解码器注意力子层**：查询来自前一解码器层，键和值来自编码器输出
  3. **前馈网络子层**
- 均使用**残差连接**和**层归一化**

## 关键设计

- **残差连接**：缓解深层网络的梯度消失问题
- **层归一化**：稳定训练过程
- **掩码自注意力**：确保解码时的自回归性质，只能看到已生成的位置
- **编码器-解码器注意力**：实现编码器信息向解码器的传递

## 变体

后续工作发展出了不同变体：
- 仅编码器：BERT
- 仅解码器：GPT 系列
- 编码器-解码器：T5
