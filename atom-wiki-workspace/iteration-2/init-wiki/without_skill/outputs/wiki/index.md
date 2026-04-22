# 机器学习算法学习笔记 - 索引

> 原子化知识库 | Machine Learning Algorithm Study Notes

## 知识库概述

本知识库用于系统化整理和管理机器学习算法的学习笔记。所有知识以原子化单元（Atomic Notes）形式存储，每个单元独立、自包含、可交叉引用。

## 目录结构

```
atom-wiki-init-eval-noskill/
├── sources/                    # 原始文档存放目录
│   └── (原始PDF、笔记、教程等)
├── atoms/                      # 原子化知识单元
│   ├── entities/               # 实体：算法、模型、人物、框架等
│   ├── concepts/               # 概念：理论基础、数学原理、术语等
│   ├── facts/                  # 事实：属性、特征、已知结论等
│   ├── how-to/                 # 操作指南：实现步骤、调参方法等
│   ├── cases/                  # 案例：应用场景、实例分析等
│   ├── comparisons/            # 对比：算法对比、方法优劣等
│   ├── qa/                     # 问答：常见问题、疑难解答等
│   └── synthesis/              # 综合：主题综述、知识整合等
├── index/                      # 索引文件
│   └── (分类索引、标签索引等)
├── index.md                    # 本文件 - 主索引
└── log.md                      # 变更日志
```

## 原子单元类型说明

| 类型 | 目录 | 说明 | 示例 |
|------|------|------|------|
| Entities | `atoms/entities/` | 具体存在的实体：算法名称、模型架构、框架、人物等 | 线性回归、SVM、TensorFlow |
| Concepts | `atoms/concepts/` | 抽象概念：理论、原理、数学基础、术语定义 | 梯度下降、过拟合、正则化 |
| Facts | `atoms/facts/` | 客观事实：属性、特性、已知结论、定理 | SVM使用核函数处理非线性问题 |
| How-to | `atoms/how-to/` | 操作指南：实现步骤、调参技巧、最佳实践 | 如何实现交叉验证、如何选择学习率 |
| Cases | `atoms/cases/` | 应用案例：实际场景、问题分析、解决方案 | 用随机森林做特征选择 |
| Comparisons | `atoms/comparisons/` | 对比分析：算法对比、方法优劣、适用场景 | 决策树 vs 随机森林 |
| QA | `atoms/qa/` | 问答记录：常见问题、疑难解答、面试问题 | 什么是偏差-方差权衡？ |
| Synthesis | `atoms/synthesis/` | 综合整理：主题综述、知识图谱、学习路线 | 监督学习算法全景图 |

## 文件命名规范

- 使用小写字母和连字符：`gradient-descent.md`
- 中文标题可用拼音或英文：`linear-regression.md`
- 保持名称简洁且有描述性
- 同一实体/概念只存在一个主文件

## 元数据格式

每个原子文件头部包含 YAML front matter：

```yaml
---
title: "标题"
type: "entity|concept|fact|how-to|case|comparison|qa|synthesis"
tags: [标签1, 标签2]
created: "YYYY-MM-DD"
updated: "YYYY-MM-DD"
source: "来源文档或URL"
related: [相关文件链接]
---
```

## 主要知识领域

- **监督学习**: 线性模型、决策树、SVM、神经网络等
- **无监督学习**: 聚类、降维、异常检测等
- **强化学习**: MDP、Q-Learning、策略梯度等
- **深度学习**: CNN、RNN、Transformer 等
- **模型评估**: 交叉验证、指标、偏差方差等
- **特征工程**: 特征选择、特征提取、预处理等
- **优化方法**: 梯度下降 variants、正则化等

## 使用指南

1. **添加新文档**: 放入 `sources/` 目录
2. **拆分原子知识**: 从源文档提取最小自包含知识单元，分类存入 `atoms/` 对应子目录
3. **建立关联**: 在相关文件的 `related` 字段中添加交叉引用
4. **查询知识**: 通过标签、关键词或浏览目录结构查找
5. **更新日志**: 每次修改后在 `log.md` 中记录

## 统计

- 原子单元总数: 0
- 最后更新: 2026-04-22
- 知识领域覆盖: 初始化中
