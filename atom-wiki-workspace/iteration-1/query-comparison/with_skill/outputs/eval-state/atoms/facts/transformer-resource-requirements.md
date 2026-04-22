---
title: "Transformer 的大规模资源需求"
type: fact
created: 2026-04-21
updated: 2026-04-21
sources: [transformer-overview.md]
tags: [transformer, resource-requirements, scalability, limitation]
related: [[transformer]], [[self-attention-o2-complexity]]
---

Transformer 模型参数量大，需要大量数据和算力进行训练。这是其重要的局限性之一。

随着模型规模的增大，训练所需的计算资源、内存和能源消耗呈指数级增长。大语言模型（如 GPT-3 的 1750 亿参数）的训练成本可达数百万美元。推理阶段同样需要大量计算资源，尤其是在自回归生成时需要重复前向传播。

这种高资源需求限制了 Transformer 在资源受限环境（如移动设备、边缘计算）中的应用，也引发了关于 AI 可持续性和可及性的讨论。
