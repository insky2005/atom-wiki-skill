---
name: atom-wiki
description: >
  Guides AI Agents to initialize, build, and query an atomized knowledge base from
  raw documents. Initialization creates a wiki directory structure with raw/, atoms/
  (entities, concepts, facts, how-to, cases, comparisons, qa, synthesis), index.md,
  log.md, and an AGENTS.md file at the project root that always directs agents to use
  this skill. Atomization means breaking documents into the smallest self-contained,
  meaningful knowledge units (atomic notes), each stored as an independent markdown
  file with metadata, tags, and cross-references. When new documents arrive, the agent
  reads, extracts, classifies, and integrates atomic units into the wiki — updating
  existing pages, flagging contradictions, and strengthening synthesis. When the user
  asks questions, the agent searches the knowledge base, assembles relevant atoms, and
  synthesizes answers with citations. Use this skill whenever the user mentions
  "atom wiki", "atomized knowledge", "knowledge base", "知识库", "原子化",
  "整理文档", "拆分文档", "归类文档", "build wiki", "initialize wiki", "初始化知识库",
  "create wiki", "ingest document", "answer from wiki", or wants to organize, split,
  categorize, or query a structured knowledge base from their documents.
version: 0.1.0
---

# Atom Wiki — Atomized Knowledge Base

Build and maintain a knowledge base where every piece of knowledge is an **atomic unit** — a small, self-contained, linkable markdown file that can be independently understood and recombined to answer any question.

## Why Atomization?

A traditional document bundles ten ideas into one file. Atomization splits them: each idea, fact, entity, or procedure gets its own file with metadata. The wiki becomes a graph of composable units — queries assemble the right units, updates touch only affected atoms, knowledge compounds without re-derivation.

## Directory Structure

```
wiki/
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
└── SCHEMA.md             # Wiki conventions (co-evolved with user)
```

## Atomic Unit Format

Every atomic unit is a markdown file with YAML frontmatter:

```yaml
---
title: "Descriptive Title"
type: entity | concept | fact | how-to | case | comparison | qa | synthesis
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: [source-file-1.md, source-file-2.md]
tags: [tag1, tag2, tag3]
related: [[other-atom]], [[another-atom]]
---
```

**Core rules**: one idea per atom, self-contained (makes sense alone), concise (50-300 words), tagged and categorized.

## Four Operations

### 0. Initialize — Create Wiki Structure

**Trigger**: User asks to create, initialize, bootstrap, or set up a wiki/knowledge base. Also triggers automatically when the first atomize operation is requested but no wiki structure exists yet.

**Steps** (full protocol: [references/bootstrap.md](references/bootstrap.md)):

1. **Determine root directory** — Use user-specified path or current working directory
2. **Create directory structure** — raw/, atoms/ (8 subdirectories), index.md, log.md
3. **Create AGENTS.md** — At project root, with wiki path, structure, and explicit instruction to always use the atom-wiki skill
4. **Seed index.md and log.md** — Empty index template, initialization log entry

The AGENTS.md file is the persistent entry point: any AI agent opening this project will read it and know to load the atom-wiki skill for all wiki operations.

### 1. Atomize — Document Processing

**Trigger**: User provides a document and asks to process, ingest, atomize, or add to knowledge base.

**Steps** (full protocol: [references/atomize.md](references/atomize.md)):

1. **Read & Comprehend** — Read the source, detect language, identify atomic candidates (5-15 per source typically)
2. **Classify & Plan** — Assign type to each candidate, present summary to user
3. **Create Atoms** — Write atom files with frontmatter, body, cross-references
4. **Ripple Updates** — Update existing atoms with new info, flag contradictions
5. **Update Index & Log** — Add entries to `index.md`, append to `log.md` (Step 5 is mandatory — verify every created/updated atom has an index entry)

### 2. Query — Knowledge-Based Answering

**Trigger**: User asks a question about the wiki's domain.

**Steps** (full protocol: [references/query.md](references/query.md)):

1. **Search** — Read `index.md`, find relevant atoms, follow related links
2. **Synthesize** — Compose answer with inline citations and confidence levels
3. **File Decision** — Always preserve the answer: if an existing atom covers the topic, UPDATE it; otherwise CREATE a new atom. Never skip filing entirely for a file-worthy answer.

### 3. Lint — Health Check

**Trigger**: User says "lint", "health check", "review wiki", or "检查知识库".

**Steps** (full protocol: [references/lint.md](references/lint.md)):

1. **Full Scan** — Read index and all listed atoms
2. **Run Checks** — Structural (orphans, broken links), content (contradictions, stale claims), cross-reference (missing backlinks, tag inconsistency)
3. **Report & Fix** — Output severity-grouped report, execute approved fixes

## Conventions

- **Filenames**: lowercase, hyphens, no spaces (e.g. `transformer-architecture.md`)
- **One idea per atom** — split when an atom contains two distinct ideas
- **Preserve original claims** — summarize faithfully, critique separately
- **Tag consistently** — prefer existing tags over creating new ones
- **Cross-reference liberally** — `related` links are the connective tissue
- **Language**: atoms follow source language; structural elements (YAML keys, type values, filenames, index/log headers) stay in English

Full conventions detail: [references/conventions.md](references/conventions.md)
