# Atom Wiki 索引

## 知识库概览

- **创建时间：** 2026-04-21
- **来源文档数：** 2
- **原子条目数：** 21
- **矛盾标记数：** 1

## 来源文档

1. **transformer-overview.md** — Transformer 架构概述（第一来源）
2. **efficient-transformers.md** — 高效 Transformer 改进方案（第二来源）

## 原子条目索引

### 基础架构与核心组件（来源一：transformer-overview.md）

| 文件 | 标题 | 标签 |
|------|------|------|
| attention-is-all-you-need-paper.md | Attention Is All You Need 论文 | #paper #milestone |
| transformer-architecture.md | Transformer 架构概述 | #architecture #overview |
| self-attention-mechanism.md | 自注意力机制 | #self-attention #core-component |
| multi-head-attention.md | 多头注意力 | #multi-head-attention #core-component |
| positional-encoding.md | 位置编码 | #positional-encoding #core-component |
| feed-forward-network.md | 前馈网络 | #feed-forward #core-component |
| encoder-decoder-structure.md | 编码器-解码器结构 | #encoder-decoder #architecture |
| transformer-impact.md | Transformer 的关键影响 | #impact #BERT #GPT #T5 |
| transformer-limitations.md | Transformer 的局限性 | #limitations #O(n^2) **⚠️ 矛盾已标记** |

### 第一来源补充条目（二次原子化产出）

| 文件 | 标题 | 标签 |
|------|------|------|
| transformer-self-attention.md | 自注意力机制（公式版） | #self-attention #core-component |
| transformer-multi-head-attention.md | 多头注意力（补充） | #multi-head-attention #core-component |
| transformer-positional-encoding.md | 位置编码（补充） | #positional-encoding #core-component |
| transformer-feed-forward-network.md | 前馈网络（补充） | #feed-forward #core-component |
| transformer-encoder-decoder.md | 编码器-解码器结构（补充） | #encoder-decoder #architecture |
| transformer-key-impact.md | Transformer 关键影响（补充） | #impact #BERT #GPT #T5 |

### 高效方法（来源二：efficient-transformers.md）— 新增

| 文件 | 标题 | 标签 |
|------|------|------|
| efficient-transformer-linformer.md | Linformer | #linformer #O(n) #low-rank |
| efficient-transformer-reformer.md | Reformer | #reformer #O(n-log-n) #LSH |
| efficient-transformer-performer.md | Performer | #performer #O(n) #FAVOR+ |
| efficient-transformer-flash-attention.md | Flash Attention | #flash-attention #GPU-optimization |
| efficient-transformer-comparison.md | 高效方法比较 | #comparison #complexity |

### 矛盾记录 — 新增

| 文件 | 标题 | 涉及来源 |
|------|------|---------|
| on2-complexity-debate.md | O(n^2) 复杂度是否为真正瓶颈？ | transformer-overview.md vs efficient-transformers.md |

## 矛盾摘要

**矛盾条目：** transformer-limitations.md + on2-complexity-debate.md
- 来源一立场：O(n^2) 是 Transformer 的主要局限，对长序列处理效率低
- 来源二立场：对于常用序列长度（512-4096 tokens），O(n^2) 不是瓶颈；IO 优化比降复杂度更有效；近似方法仅在超长序列（10K+）才有优势
- 综合判断：两来源视角互补而非矛盾——理论局限确实存在，但实际瓶颈取决于场景

## 标签云

#self-attention #transformer #core-component #attention-mechanism #multi-head-attention #encoder-decoder #positional-encoding #feed-forward #limitations #O(n^2) #efficient-transformer #linformer #reformer #performer #flash-attention #FAVOR+ #LSH #GPU-optimization #low-rank #comparison #complexity #矛盾
