---
title: "O(n^2) 复杂度并非总是瓶颈"
type: synthesis
created: 2026-04-21
updated: 2026-04-21
sources: [efficient-transformers.md]
tags: [synthesis, complexity, bottleneck, practical-performance, O-n2]
related: [[self-attention-complexity]], [[flash-attention]], [[efficient-transformers-comparison]]
---

自注意力的 O(n^2) 复杂度问题在实际应用中并非总是瓶颈。对于常见的序列长度（512-4096 tokens），标准注意力的计算速度通常足够，而 Flash Attention 的 IO 优化反而带来更显著的加速效果。近似方法在需要处理超长序列（10K+ tokens）的场景下才展现出明显优势。

这意味着选择高效注意力方法时，需要根据实际序列长度和精度需求来判断：短序列场景优先考虑 IO 优化（如 Flash Attention），超长序列场景才需要近似方法（如 Linformer、Performer）。

> **CONTRADICTION** (added 2026-04-21)
> [[self-attention-complexity]] claims: "O(n^2) 复杂度使得标准 Transformer 在处理超长文本时面临巨大的计算和内存开销" —— 暗示 O(n^2) 是主要瓶颈
> This source claims: "O(n^2) 复杂度问题在实际应用中并非总是瓶颈，对于常见序列长度 Flash Attention 的 IO 优化更显著"
> Resolution: both valid in different contexts — O(n^2) 确实是长序列（10K+）的瓶颈，但对于常见长度（512-4096），IO 才是实际瓶颈
