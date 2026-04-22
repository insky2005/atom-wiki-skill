# Efficient Transformers: 长序列处理的改进方案

近年来，研究者提出了多种方案来降低 Transformer 在长序列上的 O(n^2) 计算复杂度。

## Linformer

Linformer 将自注意力的键和值矩阵通过低秩投影压缩，将复杂度从 O(n^2) 降至 O(n)。其核心假设是注意力矩阵具有低秩特性，可以通过 k 维投影（k << n）近似原始注意力分布。在长文档分类任务上，Linformer 比 BERT 快 5-10 倍。

## Reformer

Reformer 使用局部敏感哈希（LSH）注意力，只计算最相似的键值对，将复杂度降至 O(n log n)。同时采用可逆残差层（Reversible Residual Layers）替代标准残差连接，大幅减少内存占用。但 LSH 注意力在实践中有时精度下降明显。

## Performer

Performer 使用随机正交特征（FAVOR+）近似 softmax 注意力核函数，实现线性时间复杂度 O(n)。其优势在于不需要改变注意力结构，可以直接替换标准注意力模块。在蛋白质序列建模等超长序列任务中表现优异。

## Flash Attention

与上述方法不同，Flash Attention 并不近似注意力计算，而是通过优化 GPU 内存访问模式来加速。它利用分块计算（tiling）和重计算（recomputation）策略，减少对 HBM（高带宽内存）的读写次数，实现了 2-4 倍的加速，同时完全保持计算精度。已广泛应用于 GPT-4、LLaMA 等大模型训练。

## 比较总结

| 方法 | 复杂度 | 是否精确 | 主要优势 | 主要劣势 |
|------|--------|---------|---------|---------|
| Linformer | O(n) | 近似 | 简单高效 | 低秩假设不总是成立 |
| Reformer | O(n log n) | 近似 | 内存效率高 | LSH 精度不稳定 |
| Performer | O(n) | 近似 | 即插即用 | 长序列精度有损失 |
| Flash Attention | O(n^2) | 精确 | 无精度损失 | 仅优化 IO 而非复杂度 |

值得注意的是，自注意力的 O(n^2) 复杂度问题在实际应用中并非总是瓶颈。对于常见的序列长度（512-4096 tokens），标准注意力的计算速度通常足够，而 Flash Attention 的 IO 优化反而带来更显著的加速效果。近似方法在需要处理超长序列（10K+ tokens）的场景下才展现出明显优势。
