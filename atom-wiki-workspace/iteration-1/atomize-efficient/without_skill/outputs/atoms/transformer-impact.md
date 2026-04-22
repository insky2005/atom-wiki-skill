---
title: "Transformer 的关键影响与里程碑工作"
type: synthesis
created: 2026-04-21
updated: 2026-04-21
source: transformer-overview.md
source_section: "关键影响"
tags:
  - transformer
  - BERT
  - GPT
  - T5
  - milestone
  - NLP
  - machine-translation
  - text-generation
  - QA
related:
  - transformer-architecture
  - encoder-decoder-structure
---

# Transformer 的关键影响与里程碑工作

Transformer 的出现催生了一系列里程碑式的工作，在多个 NLP 任务上取得了突破性成果。

## 里程碑模型

| 模型 | 架构变体 | 说明 |
|------|----------|------|
| BERT | 仅编码器 | 双向编码表示，适用于理解类任务 |
| GPT 系列 | 仅解码器 | 自回归生成，适用于生成类任务 |
| T5 | 编码器-解码器 | 文本到文本统一框架 |

## 突破性任务领域

- **机器翻译**：Transformer 的原始应用场景
- **文本生成**：GPT 系列引领的大语言模型方向
- **问答系统**：BERT 等模型在阅读理解上的突破

## 相比 RNN 的主要优势

1. **并行计算能力**：不像 RNN 需要逐步处理序列，Transformer 可以并行处理所有位置
2. **长距离依赖建模**：自注意力机制直接连接任意两个位置，路径长度为 O(1)，而 RNN 为 O(n)
