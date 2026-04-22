# 自注意力机制（Self-Attention）

## 内容

自注意力机制是 Transformer 的核心组件，允许模型在处理每个位置时，直接关注输入序列中的所有其他位置。

**计算公式：**

Attention(Q, K, V) = softmax(QK^T / sqrt(d_k)) V

其中：
- Q（查询）、K（键）、V（值）是输入的线性变换
- d_k 是键向量的维度
- 除以 sqrt(d_k) 是为了防止点积过大导致 softmax 梯度消失

## 来源

- transformer-overview.md

## 标签

#self-attention #transformer #core-component #attention-mechanism

## 交叉引用

- [[transformer-multi-head-attention]] - 多头注意力扩展了自注意力
- [[transformer-limitations]] - 自注意力的计算复杂度是主要局限之一
- [[on2-complexity-debate]] - 关于 O(n^2) 复杂度是否为真正瓶颈的争论
