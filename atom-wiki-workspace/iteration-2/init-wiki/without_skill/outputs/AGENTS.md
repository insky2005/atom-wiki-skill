# AI Agent 使用指南 - 机器学习算法学习笔记知识库

## 概述

本知识库位于 `/tmp/atom-wiki-init-eval-noskill/`，用于系统化整理和管理**机器学习算法学习笔记**。知识库采用原子化设计，将知识拆分为最小自包含单元，便于检索、更新和交叉引用。

## 目录结构

```
/tmp/atom-wiki-init-eval-noskill/
├── sources/                    # 原始文档存放目录
│   └── (放入PDF、笔记、教程等原始文档)
├── atoms/                      # 原子化知识单元（核心）
│   ├── entities/               # 实体：算法、模型、人物、框架等
│   ├── concepts/               # 概念：理论基础、数学原理、术语等
│   ├── facts/                  # 事实：属性、特征、已知结论等
│   ├── how-to/                 # 操作指南：实现步骤、调参方法等
│   ├── cases/                  # 案例：应用场景、实例分析等
│   ├── comparisons/            # 对比：算法对比、方法优劣等
│   ├── qa/                     # 问答：常见问题、疑难解答等
│   └── synthesis/              # 综合：主题综述、知识整合等
├── index/                      # 索引文件目录
├── index.md                    # 主索引文件
└── log.md                      # 变更日志
```

## Agent 工作流程

### 1. 摄取新文档 (Ingest)

当用户提供新的学习文档时：

1. **保存原文档**: 将文档复制到 `sources/` 目录
2. **阅读并理解**: 分析文档内容，识别知识点
3. **原子化拆分**: 将文档拆分为最小自包含知识单元
4. **分类存储**: 根据类型存入 `atoms/` 对应子目录
5. **添加元数据**: 每个文件头部添加 YAML front matter
6. **建立关联**: 在 `related` 字段中添加交叉引用
7. **更新索引**: 如有需要，更新 `index/tags.md`
8. **记录日志**: 在 `log.md` 中记录本次操作

### 2. 查询知识 (Query)

当用户提问时：

1. **搜索相关原子**: 根据关键词、标签在 `atoms/` 中查找
2. **组装知识**: 收集所有相关的原子单元
3. **综合回答**: 整合信息，给出结构化回答
4. **引用来源**: 标注引用的原子文件路径

### 3. 更新知识 (Update)

当发现新信息或修正时：

1. **定位相关原子**: 找到需要更新的 `atoms/` 文件
2. **更新内容**: 修改文件内容，更新 `updated` 日期
3. **检查关联**: 确认交叉引用是否仍然有效
4. **标记矛盾**: 如发现冲突信息，在文件中添加标注
5. **记录日志**: 在 `log.md` 中记录变更

## 原子单元分类指南

| 类型 | 何时使用 | 示例 |
|------|----------|------|
| **entities** | 描述具体的算法、模型、框架、人物 | `linear-regression.md`, `tensorflow.md` |
| **concepts** | 解释抽象理论、原理、数学基础 | `gradient-descent.md`, `overfitting.md` |
| **facts** | 记录客观事实、属性、定理 | `svm-kernel-trick.md` |
| **how-to** | 提供操作步骤、实现方法 | `implement-cross-validation.md` |
| **cases** | 实际应用场景、案例分析 | `random-forest-feature-selection.md` |
| **comparisons** | 算法或方法之间的对比 | `decision-tree-vs-random-forest.md` |
| **qa** | 常见问题及解答 | `bias-variance-tradeoff.md` |
| **synthesis** | 主题综述、知识整合、学习路线 | `supervised-learning-overview.md` |

## 文件命名规范

- 使用小写英文字母和连字符：`gradient-descent.md`
- 保持简洁且有描述性
- 同一实体/概念只存在一个主文件
- 避免空格和特殊字符

## 元数据格式 (YAML Front Matter)

每个原子文件**必须**包含以下元数据：

```yaml
---
title: "中文或英文标题"
type: "entity|concept|fact|how-to|case|comparison|qa|synthesis"
tags: [tag1, tag2, tag3]
created: "YYYY-MM-DD"
updated: "YYYY-MM-DD"
source: "来源文档路径或URL"
related:
  - "../concepts/related-concept.md"
  - "../entities/related-entity.md"
---
```

## 原子单元编写原则

1. **自包含**: 每个文件应独立完整，无需依赖其他文件即可理解
2. **原子性**: 一个文件只描述一个知识点
3. **可链接**: 通过 `related` 字段建立知识关联
4. **可追溯**: 标注来源文档，便于验证
5. **简洁**: 用最少的文字表达完整含义

## 主要知识领域

- **监督学习**: 线性模型、决策树、SVM、神经网络、集成学习等
- **无监督学习**: 聚类(K-Means, DBSCAN)、降维(PCA, t-SNE)、异常检测等
- **强化学习**: MDP、Q-Learning、策略梯度、Actor-Critic等
- **深度学习**: CNN、RNN、LSTM、Transformer、GAN等
- **模型评估**: 交叉验证、评估指标、偏差-方差权衡等
- **特征工程**: 特征选择、特征提取、数据预处理等
- **优化方法**: SGD、Adam、RMSProp、正则化(L1/L2)等

## 注意事项

- 不要修改 `sources/` 中的原始文档
- 发现矛盾信息时，不要删除，而是添加标注说明
- 保持文件间的交叉引用更新
- 定期整理 `index/tags.md` 索引
- 每次操作后务必更新 `log.md`
