# 位置编码（Positional Encoding）

## 内容

由于 Transformer 不包含递归和卷积，它本身无法感知序列的位置信息。位置编码通过正弦和余弦函数生成固定编码，与词嵌入相加，为模型提供位置信息。

**关键要点：**
- 使用正弦和余弦函数生成固定位置编码
- 位置编码与词嵌入相加
- 为模型提供位置感知能力

## 来源

- transformer-overview.md

## 标签

#positional-encoding #transformer #core-component #sequence-modeling

## 交叉引用

- [[transformer-limitations]] - 位置编码对超出训练长度的序列泛化能力有限
