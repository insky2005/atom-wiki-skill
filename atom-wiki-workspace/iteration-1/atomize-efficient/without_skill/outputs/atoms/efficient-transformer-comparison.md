# 高效 Transformer 方法比较

## 内容

| 方法 | 复杂度 | 是否精确 | 主要优势 | 主要劣势 |
|------|--------|---------|---------|---------|
| Linformer | O(n) | 近似 | 简单高效 | 低秩假设不总是成立 |
| Reformer | O(n log n) | 近似 | 内存效率高 | LSH 精度不稳定 |
| Performer | O(n) | 近似 | 即插即用 | 长序列精度有损失 |
| Flash Attention | O(n^2) | 精确 | 无精度损失 | 仅优化 IO 而非复杂度 |

**关键观察：**
- Linformer 和 Performer 实现了线性复杂度 O(n)，但都是近似方法
- Reformer 实现了 O(n log n) 复杂度，也是近似方法
- Flash Attention 保持了 O(n^2) 复杂度，但通过 IO 优化实现实际加速且不损失精度

## 来源

- efficient-transformers.md

## 标签

#efficient-transformer #comparison #complexity #approximation #exact

## 交叉引用

- [[efficient-transformer-linformer]] - Linformer 详情
- [[efficient-transformer-reformer]] - Reformer 详情
- [[efficient-transformer-performer]] - Performer 详情
- [[efficient-transformer-flash-attention]] - Flash Attention 详情
- [[on2-complexity-debate]] - 复杂度与实际性能的关系讨论
