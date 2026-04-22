---
title: "位置编码对超长序列的泛化限制"
type: fact
created: 2026-04-21
updated: 2026-04-21
sources: [transformer-overview.md]
tags: [positional-encoding, generalization, transformer, limitation]
related: [[positional-encoding]], [[self-attention-o2-complexity]]
---

位置编码对超出训练长度的序列泛化能力有限。原始 Transformer 使用的正弦/余弦位置编码虽然在理论上可以外推到任意长度，但在实践中，模型对超出训练时所见序列长度的位置编码表征能力显著下降。

这意味着如果模型在训练时只见过长度为 512 的序列，在推理时面对长度为 1024 的序列时，性能可能会明显下降。这一限制与 [[self-attention-o2-complexity|O(n²) 计算复杂度]]共同构成了 Transformer 处理长序列的双重挑战。

RoPE（旋转位置编码）和 ALiBi 等改进方案旨在缓解此问题。
