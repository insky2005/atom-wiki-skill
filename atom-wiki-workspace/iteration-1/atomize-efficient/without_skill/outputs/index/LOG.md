# Atom Wiki 处理日志

## 2026-04-21 — 知识库创建与第二次原子化

### 操作一：初始化知识库

- **时间：** 2026-04-21
- **操作：** 创建知识库结构
- **路径：** /tmp/atom-wiki-eval-1-noskill/
- **说明：** 知识库不存在，创建新结构并处理两个来源文档

### 操作二：原子化第一来源（transformer-overview.md）

- **时间：** 2026-04-21
- **来源文件：** transformer-overview.md
- **生成条目：** 7 个原子条目
  1. transformer-self-attention.md — 自注意力机制
  2. transformer-multi-head-attention.md — 多头注意力
  3. transformer-positional-encoding.md — 位置编码
  4. transformer-feed-forward-network.md — 前馈网络
  5. transformer-encoder-decoder.md — 编码器-解码器结构
  6. transformer-key-impact.md — Transformer 的关键影响
  7. transformer-limitations.md — Transformer 的局限性

### 操作三：原子化第二来源（efficient-transformers.md）

- **时间：** 2026-04-21
- **来源文件：** efficient-transformers.md
- **生成新条目：** 5 个原子条目
  1. efficient-transformer-linformer.md — Linformer
  2. efficient-transformer-reformer.md — Reformer
  3. efficient-transformer-performer.md — Performer
  4. efficient-transformer-flash-attention.md — Flash Attention
  5. efficient-transformer-comparison.md — 高效方法比较

### 操作四：矛盾检测与标记

- **时间：** 2026-04-21
- **矛盾类型：** 视角矛盾（对 O(n^2) 复杂度严重性的不同判断）
- **涉及条目：**
  - transformer-limitations.md（来源一立场：O(n^2) 是主要局限）
  - on2-complexity-debate.md（来源二立场：常用序列长度下不是瓶颈）
- **处理方式：**
  - 更新 transformer-limitations.md，添加矛盾标记段落
  - 创建独立的矛盾记录条目 on2-complexity-debate.md
  - 在两个条目间建立双向交叉引用
- **综合判断：** 两来源视角互补而非完全矛盾——O(n^2) 确实是理论局限，但在实际常用序列长度下不是主要瓶颈；近似方法仅在超长序列（10K+）场景才有明显优势
