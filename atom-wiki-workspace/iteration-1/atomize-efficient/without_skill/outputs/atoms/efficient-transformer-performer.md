# Performer：随机正交特征的线性注意力

## 内容

Performer 使用随机正交特征（FAVOR+）近似 softmax 注意力核函数，实现线性时间复杂度 O(n)。

**核心原理：**
- 使用 FAVOR+（Fast Attention Via Orthogonal Random features）方法
- 近似 softmax 注意力核函数
- 不需要改变注意力结构，可以直接替换标准注意力模块（即插即用）

**性能表现：**
- 在蛋白质序列建模等超长序列任务中表现优异

**优势：** 即插即用，无需修改注意力结构

**劣势：** 长序列精度有损失

## 来源

- efficient-transformers.md

## 标签

#performer #efficient-transformer #FAVOR+ #linear-attention #O(n) #kernel-approximation

## 交叉引用

- [[transformer-self-attention]] - Performer 改进的基础自注意力机制
- [[efficient-transformer-comparison]] - 与其他高效方法的比较
- [[transformer-limitations]] - Performer 针对的 O(n^2) 局限
