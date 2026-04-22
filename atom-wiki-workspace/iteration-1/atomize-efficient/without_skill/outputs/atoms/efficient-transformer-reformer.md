# Reformer：局部敏感哈希注意力

## 内容

Reformer 使用局部敏感哈希（LSH）注意力，只计算最相似的键值对，将复杂度降至 O(n log n)。

**核心原理：**
- 使用 LSH（Locality-Sensitive Hashing）注意力
- 只计算最相似的键值对，避免全对计算
- 采用可逆残差层（Reversible Residual Layers）替代标准残差连接，大幅减少内存占用

**优势：** 内存效率高

**劣势：** LSH 注意力在实践中有时精度下降明显

## 来源

- efficient-transformers.md

## 标签

#reformer #efficient-transformer #LSH #O(n-log-n) #memory-efficient

## 交叉引用

- [[transformer-self-attention]] - Reformer 改进的基础自注意力机制
- [[efficient-transformer-comparison]] - 与其他高效方法的比较
- [[transformer-limitations]] - Reformer 针对的 O(n^2) 局限
