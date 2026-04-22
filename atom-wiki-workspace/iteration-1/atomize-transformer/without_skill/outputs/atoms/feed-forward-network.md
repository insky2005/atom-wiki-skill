---
title: "前馈网络（Feed-Forward Network）"
type: concept
created: 2026-04-21
updated: 2026-04-21
source: transformer-overview.md
source_section: "核心组件 > 前馈网络"
tags:
  - feed-forward-network
  - FFN
  - transformer
  - ReLU
  - position-wise
related:
  - transformer-architecture
  - encoder-decoder-structure
---

# 前馈网络（Feed-Forward Network）

每个 Transformer 层包含一个逐位置的前馈网络，对每个位置独立地应用相同的变换。

## 计算公式

```
FFN(x) = max(0, xW1 + b1)W2 + b2
```

## 结构说明

- **两个线性变换**：W1 和 W2 分别是两个线性变换的权重矩阵
- **ReLU 激活函数**：`max(0, ...)` 即 ReLU 激活，在两个线性变换之间
- **偏置项**：b1 和 b2 分别是两个线性变换的偏置

## 维度特点

- **隐藏维度**：通常是模型维度的 4 倍
- **逐位置应用**：对序列中每个位置独立地应用相同的变换

## 在 Transformer 中的角色

前馈网络是 Transformer 层的两个子层之一（另一个是多头自注意力子层），位于注意力子层之后。
