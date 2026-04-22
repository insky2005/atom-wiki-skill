# Linformer：低秩投影的线性注意力

## 内容

Linformer 将自注意力的键和值矩阵通过低秩投影压缩，将复杂度从 O(n^2) 降至 O(n)。

**核心原理：**
- 核心假设是注意力矩阵具有低秩特性
- 可以通过 k 维投影（k << n）近似原始注意力分布

**性能表现：**
- 在长文档分类任务上，Linformer 比 BERT 快 5-10 倍

**优势：** 简单高效

**劣势：** 低秩假设不总是成立

## 来源

- efficient-transformers.md

## 标签

#linformer #efficient-transformer #linear-attention #low-rank #O(n)

## 交叉引用

- [[transformer-self-attention]] - Linformer 改进的基础自注意力机制
- [[efficient-transformer-comparison]] - 与其他高效方法的比较
- [[transformer-limitations]] - Linformer 针对的 O(n^2) 局限
