# Flash Attention：GPU 内存访问优化

## 内容

Flash Attention 与近似方法不同，并不近似注意力计算，而是通过优化 GPU 内存访问模式来加速。

**核心原理：**
- 利用分块计算（tiling）策略
- 使用重计算（recomputation）策略
- 减少对 HBM（高带宽内存）的读写次数

**关键特性：**
- 完全保持计算精度（不近似）
- 实现 2-4 倍的加速
- 已广泛应用于 GPT-4、LLaMA 等大模型训练

**优势：** 无精度损失

**劣势：** 仅优化 IO 而非计算复杂度，理论复杂度仍为 O(n^2)

## 来源

- efficient-transformers.md

## 标签

#flash-attention #efficient-transformer #GPU-optimization #exact-attention #tiling #recomputation #O(n^2)

## 交叉引用

- [[transformer-self-attention]] - Flash Attention 优化的基础自注意力计算
- [[efficient-transformer-comparison]] - 与近似方法的比较
- [[on2-complexity-debate]] - Flash Attention 在常用序列长度下的实际加速效果
- [[transformer-limitations]] - 与 O(n^2) 局限性的关系（IO 优化而非复杂度优化）
