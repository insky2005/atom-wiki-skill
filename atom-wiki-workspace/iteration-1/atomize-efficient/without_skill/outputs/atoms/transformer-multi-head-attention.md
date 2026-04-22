# 多头注意力（Multi-Head Attention）

## 内容

多头注意力将 Q、K、V 分别投影到 h 个不同的子空间，并行计算注意力，然后将结果拼接并线性变换。

**关键特性：**
- 让模型能同时关注不同位置的不同表征子空间中的信息
- 原论文使用 h=8 个头
- 增强了模型关注不同位置和不同语义层面的能力

## 来源

- transformer-overview.md

## 标签

#multi-head-attention #transformer #core-component #attention-mechanism

## 交叉引用

- [[transformer-self-attention]] - 多头注意力的基础
- [[transformer-encoder-decoder]] - 多头注意力在编码器-解码器中的应用
