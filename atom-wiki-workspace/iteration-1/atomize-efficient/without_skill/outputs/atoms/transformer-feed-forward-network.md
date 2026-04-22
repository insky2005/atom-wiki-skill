# 前馈网络（Feed-Forward Network）

## 内容

每个 Transformer 层包含一个逐位置的前馈网络，由两个线性变换和 ReLU 激活组成。

**计算公式：**

FFN(x) = max(0, xW1 + b1)W2 + b2

**关键特性：**
- 隐藏维度通常是模型维度的 4 倍
- 逐位置独立计算（即每个位置使用相同的变换参数）
- 提供非线性变换能力

## 来源

- transformer-overview.md

## 标签

#feed-forward #transformer #core-component #neural-network

## 交叉引用

- [[transformer-encoder-decoder]] - FFN 在编码器-解码器结构中的位置
