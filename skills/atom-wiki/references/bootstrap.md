# Bootstrap Protocol — Full Reference

Detailed protocol for initializing a new atom-wiki knowledge base in a user-specified or current directory.

## Trigger

User asks to create, initialize, bootstrap, or set up a wiki, knowledge base, or atom-wiki. Phrases: "create wiki", "初始化知识库", "建立 wiki", "bootstrap atom-wiki", "set up knowledge base", "在这个目录建 wiki", "create atom wiki".

Also triggers automatically when the first atomize operation is requested but no wiki structure exists yet — in this case, initialize first, then proceed with atomization.

## Step 1: Determine Wiki Root Directory

**Always create `wiki/` as a subdirectory in the current working directory.**

- Wiki root: `./wiki/`
- AGENTS.md: `./AGENTS.md` (same level as the `wiki/` folder)

Store the wiki root path for all subsequent operations. This path is used to locate the wiki's `atoms/`, `index.md`, `log.md`, and to create the `AGENTS.md` file.

## Step 2: Create Directory Structure

Create the complete directory tree at the wiki root:

```
{wiki-root}/
├── raw/                  # Immutable source documents (read-only)
│   └── assets/           # Images and attachments
├── atoms/                # Atomic knowledge units (the core)
│   ├── entities/         # People, organizations, products, places
│   ├── concepts/         # Ideas, theories, frameworks, principles
│   ├── facts/            # Specific claims, data points, statistics
│   ├── how-to/           # Procedures, guides, recipes, methods
│   ├── cases/            # Case studies, examples, stories
│   ├── comparisons/      # Side-by-side analyses of 2+ things
│   ├── qa/               # Questions and answers derived from queries
│   └── synthesis/        # Higher-level synthesis across atoms
├── index.md              # Content catalog — updated on every operation
├── log.md                # Chronological operation log — append only
└── SCHEMA.md             # Wiki conventions (optional, co-evolved with user)
```

Use `mkdir -p` to create all directories. Empty directories are fine at this stage — they'll be populated as atoms are created.

## Step 3: Create Seed Files

### 3.1 index.md

Create `wiki/index.md` with the complete template (all type sections, empty tables):

```markdown
# Knowledge Base Index

## Entities
| File | Title | Tags | Sources |
|------|-------|------|---------|

## Concepts
| File | Title | Tags | Sources |
|------|-------|------|---------|

## Facts
| File | Title | Tags | Sources |
|------|-------|------|---------|

## How-to
| File | Title | Tags | Sources |
|------|-------|------|---------|

## Cases
| File | Title | Tags | Sources |
|------|-------|------|---------|

## Comparisons
| File | Title | Topic | Sources |
|------|-------|-------|---------|

## Q&A
| File | Question | Tags | Sources |
|------|----------|------|---------|

## Synthesis
| File | Topic | Tags | Sources |
|------|-------|------|---------|
```

### 3.2 log.md

Create `wiki/log.md` with the initialization entry:

```
## [{date}] init
- Wiki initialized at {wiki-root}
- AGENTS.md created at {agents-md-path}
```

## Step 4: Create AGENTS.md

Create `AGENTS.md` at the current working directory, alongside the `wiki/` folder.

- Wiki root: `./wiki/`
- AGENTS.md: `./AGENTS.md`

This file serves as the persistent instruction for any AI agent that opens the project — it lives alongside the wiki folder, never inside it.

**Use this exact template. Only replace the two placeholders in backticks. Do NOT modify anything else.**

````markdown
# Project AI Agent Instructions

This project contains an atomized knowledge base managed by the **atom-wiki** skill.

> **IMPORTANT**: For any operation related to the wiki — processing documents, answering questions, or maintaining the knowledge base — you MUST use the `atom-wiki` skill. Do not attempt to process wiki files without loading this skill first.

## Knowledge Base Location

The wiki is located at: `wiki/`

All paths below are relative to this directory.

## Directory Structure

```
wiki/
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

When the user provides a document (uploaded file, pasted text, URL, or file path) and asks to process it, ingest it, or add it to the knowledge base:

1. Load the `atom-wiki` skill
2. **FIRST: Save the source document to `raw/` directory** — this is mandatory. If the user uploaded a file, copy it to `raw/`. If they pasted text, save it as `{topic}-{date}.md` in `raw/`. Do NOT proceed with atomization until the source is saved.
3. Follow the skill's atomize protocol: read the source, extract atomic knowledge units, classify them, write atom files with frontmatter, cross-reference with existing atoms, flag contradictions, update index and log

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
````

Replace only these two placeholders:
- `{DATE}` → Current date in YYYY-MM-DD
- `{WIKI_DESCRIPTION}` → Brief description of what this wiki is about (from user input or inferred from domain)

## Step 5: Initialize .gitignore (Optional)

If the wiki root is a git repository, create `.gitignore`:

```
# OS files
.DS_Store
Thumbs.db

# Editor files
*.swp
*~

# Keep everything else tracked
!*.md
```

## Step 6: Summary

Output a brief summary:

```
Wiki initialized at {wiki-root}
AGENTS.md created at {agents-md-path}

Structure:
  raw/          → Drop source documents here
  atoms/        → Atomic knowledge units (entities, concepts, facts, etc.)
  index.md      → Content catalog
  log.md        → Operation log

Next steps:
  1. Add source documents to raw/
  2. Use atom-wiki skill to atomize: "atomize raw/my-document.md"
  3. Ask questions: "What do we know about X?"
```
