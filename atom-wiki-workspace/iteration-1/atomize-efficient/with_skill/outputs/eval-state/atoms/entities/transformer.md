---
title: "Transformer 架构"
type: entity
created: 2026-04-21
updated: 2026-04-21
sources: [transformer-overview.md, efficient-transformers.md]
tags: [deep-learning, neural-network, transformer, nlp]
related: [[self-attention-mechanism]], [[multi-head-attention]], [[positional-encoding]], [[encoder-decoder-structure]], [[transformer-vs-rnn]], [[linformer]], [[reformer]], [[performer]], [[flash-attention]], [[efficient-transformers-comparison]]
---

Transformer 是一种基于自注意力机制的神经网络架构，由 Vaswani 等人在 2017 年的论文 "Attention Is All You Need" 中提出。它彻底改变了自然语言处理领域，并逐渐扩展到计算机视觉、语音识别等多个领域。

作为神经网络架构，Transformer 的核心创新在于摒弃了传统的递归和卷积结构，完全依赖注意力机制来建模输入和输出之间的全局依赖关系。这一设计带来了两个关键优势：并行计算能力和长距离依赖建模。

Transformer 的出现催生了一系列里程碑式的工作，包括 [[transformer-milestone-works|BERT、GPT 系列和 T5]]，在机器翻译、文本生成、问答系统等任务上取得了突破性成果。

其核心组件包括 [[self-attention-mechanism|自注意力机制]]、[[multi-head-attention|多头注意力]]、[[positional-encoding|位置编码]]和 [[feed-forward-network|前馈网络]]，采用 [[encoder-decoder-structure|编码器-解码器结构]]。

## 效率改进

由于自注意力的 O(n²) 计算复杂度对长序列处理效率低，研究者提出了多种改进方案：[[linformer|Linformer]]（低秩投影，O(n)）、[[reformer|Reformer]]（LSH 注意力，O(n log n)）、[[performer|Performer]]（FAVOR+ 核近似，O(n)）和 [[flash-attention|Flash Attention]]（GPU 内存优化，保持 O(n²) 但加速 2-4 倍）。详见 [[efficient-transformers-comparison|高效 Transformer 方法对比]]。
