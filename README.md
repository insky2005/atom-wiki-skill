# Atom Wiki — Atomized Knowledge Base

一个基于 LLM 的原子化知识库系统，将文档拆分为最小的、自包含的知识单元，构建持久化、可互联的 Markdown 知识库。

## 项目简介

Atom Wiki 实现了一种不同于传统 RAG 的知识管理方式：不是每次查询时重新从原始文档中检索碎片信息，而是让 LLM **增量构建并维护一个持久化的 wiki** —— 一个结构化、相互关联的 Markdown 文件集合。随着新文档的加入，知识库不断积累、更新、演化，形成可复用的知识资产。

核心理念：**Wiki 是一个持久化、复利的产物。**

## 灵感来源

本项目基于 [LLM Wiki 概念文档](docs/llm-wiki.md) 实现，该文档描述了 Karpathy 模式的个人知识库构建方法。

## 项目结构

```
atom-wiki-skill/
├── skills/atom-wiki/          # Qoder 技能定义
│   ├── SKILL.md               # 技能主文件，定义操作流程和规范
│   ├── references/            # 参考文档
│   │   ├── atomize.md         # 文档原子化流程
│   │   ├── bootstrap.md       # 初始化 wiki 流程
│   │   ├── query.md           # 查询 wiki 流程
│   │   ├── lint.md            # 知识库健康检查流程
│   │   └── conventions.md     # 命名和结构规范
│   ├── evals/                 # 评估测试用例和数据
│   └── assets/                # 技能相关资源
├── docs/
│   └── llm-wiki.md            # LLM Wiki 原始概念文档（灵感来源）
├── atom-wiki-workspace/       # 工作区和评估数据
│   ├── iteration-1/           # 第一轮评估（Transformer 相关文档）
│   └── iteration-2/           # 第二轮评估（初始化 wiki 测试）
└── README.md                  # 本文件
```

## 核心能力

### 1. Initialize — 初始化 Wiki 结构

创建完整的 wiki 目录结构，包括 `raw/`、`atoms/`（8 个子目录）、`index.md`、`log.md` 和 `AGENTS.md`。

### 2. Atomize — 文档原子化

将文档拆分为最小的、自包含的知识单元（atomic notes），每个知识单元存储为独立的 Markdown 文件，包含元数据、标签和交叉引用。

### 3. Query — 基于知识库查询

根据用户问题搜索相关知识单元，组装答案并附带引用和置信度说明。

### 4. Lint — 知识库健康检查

定期检查知识库中的矛盾、过时内容、孤立页面、缺失交叉引用等问题。

## 知识库结构

```
wiki/
├── raw/                  # 原始源文档（只读）
│   └── assets/           # 图片和附件
├── atoms/                # 原子知识单元（核心）
│   ├── entities/         # 人物、组织、产品、地点
│   ├── concepts/         # 概念、理论、框架、原则
│   ├── facts/            # 具体声明、数据点、统计
│   ├── how-to/           # 流程、指南、方法
│   ├── cases/            # 案例研究、示例
│   ├── comparisons/      # 对比分析
│   ├── qa/               # 问答记录
│   └── synthesis/        # 高层综合总结
├── index.md              # 内容目录（每次操作时更新）
├── log.md                # 操作日志（仅追加）
└── SCHEMA.md             # Wiki 规范
```

## 评估数据

项目包含两轮评估数据，对比使用 Skill 和不使用 Skill 的效果差异：

| 指标 | With Skill | Without Skill | 差异 |
|------|------------|---------------|------|
| 通过率 | 90% | 46% | +44% |
| 耗时(秒) | 103 | 68 | +35s |
| Token 消耗 | 39,000 | 27,000 | +12K |

评估结果表明：使用 Skill 能显著提高任务完成的规范性和质量，特别是在目录结构遵循、命名规范、日志格式、知识库引用等方面。

详细评估数据参见：`atom-wiki-workspace/iteration-1/benchmark.json`

## 安装方法

### 方式一：使用 npx skills add（推荐）

```bash
npx skills add https://github.com/insky2005/atom-wiki-skill --skill atom-wiki
```

### 方式二：手动安装

将 `skills/atom-wiki/` 目录复制到你的 Agent 技能目录中：

```bash
# 克隆本仓库
git clone https://github.com/insky2005/atom-wiki-skill.git

# 复制 skill 到技能目录
cp -r atom-wiki-skill/skills/atom-wiki ~/.agents/skills/

# 添加软链接（参考如下）
ln -sfn .agents/skills/atom-wiki ~/.qoder/skills/atom-wiki
```

### 方式三：通过 Agent 界面安装

在 Agent 中使用 `/skills` 命令，然后选择 `Add Skill`，输入仓库 URL 或本地路径。

## 使用方法

在 Agent 中，当需要以下操作时会自动触发 atom-wiki 技能：

- 创建、初始化、设置 wiki/知识库
- 处理、拆分、归类文档
- 从知识库中查询问题
- 检查知识库健康

相关关键词：`atom wiki`、`atomized knowledge`、`knowledge base`、`知识库`、`原子化`、`整理文档`、`拆分文档`、`build wiki`、`initialize wiki`、`初始化知识库`

## 许可证

本项目仅供个人学习和研究使用。
