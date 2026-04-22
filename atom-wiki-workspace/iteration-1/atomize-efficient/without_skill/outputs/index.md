# Atom Wiki 索引

## 知识库概览

- **来源文档**：transformer-overview.md
- **原子单元数量**：9
- **创建日期**：2026-04-21

## 原子单元目录

### 实体（Entity）

| 文件名 | 标题 | 标签 |
|--------|------|------|
| transformer-architecture.md | Transformer 架构 | transformer, neural-network, architecture, deep-learning, NLP |

### 概念（Concept）

| 文件名 | 标题 | 标签 |
|--------|------|------|
| self-attention-mechanism.md | 自注意力机制（Self-Attention） | self-attention, attention-mechanism, transformer, softmax |
| multi-head-attention.md | 多头注意力（Multi-Head Attention） | multi-head-attention, attention-mechanism, transformer, parallel-computation |
| positional-encoding.md | 位置编码（Positional Encoding） | positional-encoding, transformer, sequence-modeling, sinusoidal |
| feed-forward-network.md | 前馈网络（Feed-Forward Network） | feed-forward-network, FFN, transformer, ReLU |
| encoder-decoder-structure.md | 编码器-解码器结构（Encoder-Decoder） | encoder-decoder, transformer, seq2seq, residual-connection, masked-attention |

### 事实（Fact）

| 文件名 | 标题 | 标签 |
|--------|------|------|
| attention-is-all-you-need-paper.md | Attention Is All You Need 论文 | paper, transformer, Vaswani, 2017, landmark-paper |

### 综合（Synthesis）

| 文件名 | 标题 | 标签 |
|--------|------|------|
| transformer-impact.md | Transformer 的关键影响与里程碑工作 | transformer, BERT, GPT, T5, milestone |

### 比较（Comparison）

| 文件名 | 标题 | 标签 |
|--------|------|------|
| transformer-limitations.md | Transformer 的局限性 | transformer, limitations, complexity, computational-cost |

## 关系图谱

```
transformer-architecture
├── self-attention-mechanism
│   └── multi-head-attention
├── positional-encoding
│   └── transformer-limitations (泛化问题)
├── feed-forward-network
├── encoder-decoder-structure
│   ├── self-attention-mechanism
│   ├── multi-head-attention
│   └── feed-forward-network
├── attention-is-all-you-need-paper
├── transformer-impact
│   └── encoder-decoder-structure (变体)
└── transformer-limitations
    ├── self-attention-mechanism (O(n^2) 复杂度)
    └── positional-encoding (泛化问题)
```

## 类型统计

| 类型 | 数量 |
|------|------|
| entity | 1 |
| concept | 5 |
| fact | 1 |
| synthesis | 1 |
| comparison | 1 |
| **总计** | **9** |
