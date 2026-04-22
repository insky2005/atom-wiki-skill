---
title: "Flash Attention"
type: concept
created: 2026-04-22
updated: 2026-04-22
sources: [efficient-transformers.md]
tags: [flash-attention, efficient-attention, transformer, gpu-optimization, io-optimization]
related: [[self-attention-mechanism]], [[self-attention-o2-complexity]], [[efficient-transformers-comparison]], [[on2-not-always-bottleneck]]
---

Flash Attention 是一种高效 Transformer 实现方法，与 Linformer、Reformer、Performer 等近似方法不同，它并不近似注意力计算，而是通过优化 GPU 内存访问模式来加速。

Flash Attention 利用分块计算（tiling）和重计算（recomputation）策略，减少对 HBM（高带宽内存）的读写次数，实现了 2-4 倍的加速，同时完全保持计算精度。

该方法已广泛应用于 GPT-4、LLaMA 等大模型训练。对于常见的序列长度（512-4096 tokens），Flash Attention 的 IO 优化比近似方法带来更显著的加速效果。

Flash Attention 属于**IO 优化方法**，保持计算精度不变，通过优化内存访问模式来加速。其计算复杂度仍为 O(n²)，但在实际应用中往往比降低复杂度的近似方法更实用。
