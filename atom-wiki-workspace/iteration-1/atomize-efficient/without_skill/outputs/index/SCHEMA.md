# Atom Wiki Schema

## 条目格式规范

每个原子条目（atom）应包含以下结构：

```markdown
# [条目标题]

## 内容

[核心知识内容，自包含、可独立理解]

## 来源

- [来源文档名]

## ⚠️ 矛盾标记（仅在有矛盾时添加）

> **与 [矛盾来源] 存在矛盾**
>
> [矛盾描述]
>
> **综合判断：** [调和分析]

## 标签

#[tag1] #[tag2] ...

## 交叉引用

- [[related-atom]] - 关系说明
```

## 矛盾处理规范

1. **检测：** 新条目与已有条目内容冲突时标记
2. **标记方式：**
   - 在被矛盾的已有条目中添加 "⚠️ 矛盾标记" 段落
   - 创建独立的矛盾记录条目（命名格式：`[主题]-debate.md`）
3. **综合判断：** 尽可能给出调和两个来源的分析
4. **交叉引用：** 在矛盾条目间建立双向引用

## 命名规范

- 第一来源条目：`transformer-[topic].md`
- 第二来源条目：`efficient-transformer-[topic].md`
- 矛盾记录：`[主题]-debate.md`

## 标签体系

- 架构层级：#core-component #architecture
- 功能模块：#self-attention #multi-head-attention #positional-encoding #feed-forward
- 效率相关：#efficient-transformer #complexity #O(n^2) #O(n) #O(n-log-n)
- 方法标签：#linformer #reformer #performer #flash-attention
- 元标签：#矛盾已标记 #practical-vs-theoretical
