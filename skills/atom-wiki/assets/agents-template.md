# Project AI Agent Instructions

This project contains an atomized knowledge base managed by the **atom-wiki** skill.

> **IMPORTANT**: For any operation related to the wiki — processing documents, answering questions, or maintaining the knowledge base — you MUST use the `atom-wiki` skill. Do not attempt to process wiki files without loading this skill first.

## Knowledge Base Location

The wiki is located at: `{WIKI_ROOT}`

All paths below are relative to this directory.

## Directory Structure

```
{WIKI_ROOT}/
├── raw/                  # Immutable source documents (read-only)
│   └── assets/           # Images and attachments
├── atoms/                # Atomic knowledge units
│   ├── entities/         # People, organizations, products, places
│   ├── concepts/         # Ideas, theories, frameworks, principles
│   ├── facts/            # Specific claims, data points, statistics
│   ├── how-to/           # Procedures, guides, recipes, methods
│   ├── cases/            # Case studies, examples, stories
│   ├── comparisons/      # Side-by-side analyses
│   ├── qa/               # Q&A derived from queries
│   └── synthesis/        # Higher-level synthesis
├── index.md              # Content catalog
└── log.md                # Operation log
```

## How to Use the Wiki

The wiki supports three operations. For all of them, invoke the `atom-wiki` skill:

### 1. Atomize — Process Documents

When the user provides a document and asks to process it, ingest it, or add it to the knowledge base:

1. Load the `atom-wiki` skill
2. Follow the skill's atomize protocol: read the source, extract atomic knowledge units, classify them, write atom files with frontmatter, cross-reference with existing atoms, flag contradictions, update index and log

Example user prompts: "处理这个文档", "atomize this article", "add to wiki"

### 2. Query — Answer Questions

When the user asks a question about the wiki's domain:

1. Load the `atom-wiki` skill
2. Follow the skill's query protocol: search index.md for relevant atoms, read them, synthesize an answer with citations and confidence levels, file the answer as a new atom if valuable

Example user prompts: "What do we know about X?", "How does Y work?", "这个知识库对 Z 有什么看法"

### 3. Lint — Health Check

When the user asks to review, check, or maintain the wiki:

1. Load the `atom-wiki` skill
2. Follow the skill's lint protocol: scan for orphaned atoms, broken links, contradictions, stale claims, missing cross-references

Example user prompts: "lint wiki", "检查知识库", "review wiki"

## Rules

- **Never modify files in `raw/`** — source documents are immutable
- **Always use the atom-wiki skill** for wiki operations — do not improvise your own approach
- **Always update index.md and log.md** after any operation that creates or modifies atoms
- **Preserve the atom format** — every atom file must have YAML frontmatter with title, type, created, updated, sources, tags, related fields

## Initialization Date

Wiki initialized on: `{DATE}`

{WIKI_DESCRIPTION}
