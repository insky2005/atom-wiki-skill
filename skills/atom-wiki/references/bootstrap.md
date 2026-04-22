# Bootstrap Protocol — Full Reference

Detailed protocol for initializing a new atom-wiki knowledge base in a user-specified or current directory.

## Trigger

User asks to create, initialize, bootstrap, or set up a wiki, knowledge base, or atom-wiki. Phrases: "create wiki", "初始化知识库", "建立 wiki", "bootstrap atom-wiki", "set up knowledge base", "在这个目录建 wiki", "create atom wiki".

Also triggers automatically when the first atomize operation is requested but no wiki structure exists yet — in this case, initialize first, then proceed with atomization.

## Step 1: Determine Wiki Root Directory

1. **If user specifies a directory path**: Use that path as the wiki root. If it doesn't exist, create it.
2. **If no directory specified**: Use the current working directory as the wiki root.
3. **Confirm with user**: "I'll create the wiki structure at `{wiki-root}`. Correct?"

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

Create `AGENTS.md` at the **project root** (the parent of the wiki root, or the wiki root itself if no parent project exists). This file serves as the persistent instruction file for any AI agent that opens this project.

Use the template at [assets/agents-template.md](assets/agents-template.md). Fill in the placeholders:

| Placeholder | Value |
|-------------|-------|
| `{WIKI_ROOT}` | The wiki root directory path (relative to AGENTS.md location) |
| `{WIKI_DESCRIPTION}` | Brief description of what this wiki is about (from user input or inferred from domain) |
| `{DATE}` | Current date in YYYY-MM-DD |

The AGENTS.md file must:
1. **Always direct agents to use the atom-wiki skill** for any wiki-related operations
2. **Specify the wiki root directory path** so agents know where to find files
3. **List all key directories** (`raw/`, `atoms/`, etc.) so agents know the structure
4. **Explain the three operations** (Atomize, Query, Lint) at a high level
5. **Include the atom-wiki skill name** so agents know which skill to invoke

**Important**: The AGENTS.md file is the primary way any AI agent (not just the current session) learns about the wiki. It must be clear, actionable, and explicitly reference the atom-wiki skill.

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
