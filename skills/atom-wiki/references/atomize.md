# Atomize Protocol — Full Reference

Detailed protocol for ingesting a new source and breaking it into atomic knowledge units.

## Trigger

User provides a document (file path, pasted text, or URL) and asks to process, ingest, atomize, or add it to the knowledge base. Phrases: "处理这个文档", "整理这篇文章", "atomize this", "ingest", "add to wiki", "拆分这个文档", "归类".

## Pre-flight Checks

1. Verify the source exists and is readable
2. Determine file type:
   | Type | Action |
   |------|--------|
   | Markdown / text | Read directly |
   | PDF | Extract text (ask user for tool if unavailable) |
   | Image | Describe contents, note as visual source |
   | CSV / JSON | Summarize structure and key data points |
   | Other | Ask user how to handle |
3. Check `wiki/log.md` — has this source been processed before? If yes, ask: "This source was processed on {date}. Re-process (update) or skip?"

## Step 1: Read and Comprehend

Read the entire source. Produce internal notes (not written to file):

- **Primary language** of the source. All atoms derived from this source MUST be written in this language. Structural elements (YAML keys, `type` values, filenames, table column headers in index/log) stay in English.
- **Atomic candidates**: every distinct idea, entity, concept, fact, procedure, case study, or comparison that can stand on its own.
- **Relationships**: which atoms reference each other, which share context.
- **Contradictions**: does anything in this source conflict with existing wiki content?

A single source typically yields 5-15 atomic units. A dense research paper might yield 20+. A casual note might yield 2-3. The goal is to capture every meaningful unit — err on the side of more atoms, not fewer. Merging is easy; splitting later is hard.

## Step 2: Classify and Plan

For each atomic candidate, assign a type:

| Type | Directory | Criteria |
|------|-----------|----------|
| Entity | `atoms/entities/` | Has identity: a person, org, product, place, event, tool |
| Concept | `atoms/concepts/` | An idea, theory, framework, principle, pattern, mental model |
| Fact | `atoms/facts/` | A specific claim, data point, statistic, or verifiable assertion |
| How-to | `atoms/how-to/` | A procedure, method, recipe, guide — steps to achieve something |
| Case | `atoms/cases/` | A concrete example, case study, story, or narrative |
| Comparison | `atoms/comparisons/` | A structured side-by-side analysis of 2+ things |
| Synthesis | `atoms/synthesis/` | A higher-level insight synthesized from multiple atoms |

Present a brief summary to the user: "I found {N} atomic units from this source: {breakdown by type}. Key highlights: {2-3 bullet points}. Anything to emphasize or de-emphasize?"

This step is skippable if the user says "atomize silently" or "batch process".

## Step 3: Create Atomic Units

For each planned atom:

1. **Write the atom file** at the appropriate path with full frontmatter and body content.
2. **Source reference**: list the source filename in the `sources` field (filename only, e.g. `[article.md]`, not `raw/article.md`).
3. **Cross-reference**: add `related` links to other atoms this one connects to — both new and existing atoms.
4. **Quote faithfully**: preserve the source's original claims. Summarize faithfully, critique separately.

### Atom Body Guidelines

- **Entity atoms**: who/what it is, key attributes, significance, notable events/relationships
- **Concept atoms**: definition, core mechanism, when/where it applies, key implications
- **Fact atoms**: the claim, evidence or source context, scope and limitations
- **How-to atoms**: goal, prerequisites, step-by-step procedure, common pitfalls
- **Case atoms**: context, what happened, outcome, lessons or implications
- **Comparison atoms**: dimensions being compared, structured table or analysis, conclusion
- **Synthesis atoms**: thesis, supporting atoms cited, broader implications

## Step 4: Ripple Updates

For each new atom, check whether existing atoms need updating:

- **Existing entity/concept atoms**: if the new source adds information about an already-documented entity or concept, update that atom — add the new source to `sources`, append new content, update `updated` date.
- **Contradictions**: if the new source contradicts an existing atom, add a contradiction block:

```markdown
> **CONTRADICTION** (added {date})
> [[existing-atom]] claims: "{quote or paraphrase}"
> This source claims: "{quote or paraphrase}"
> Resolution: {pending | newer data supersedes | both valid in different contexts}
```

- **New relationships**: if the new atom reveals a connection between existing atoms that wasn't previously linked, add `related` entries to both.

## Step 5: Update Index — MANDATORY

Update `wiki/index.md` to reflect ALL changes from this operation. This step is mandatory — do not skip it.

**The process**:
1. **List all affected atoms**: write down every atom you created or updated in this operation (both new and existing atoms).
2. **Read the current `index.md`**.
3. For each affected atom:
   - **New atom**: add a new entry under the correct type section.
   - **Updated atom**: verify the existing entry is present and accurate. If the entry was missing, add it now.
4. Verify completeness: count the `.md` files in each `atoms/` subdirectory and confirm each one has a corresponding entry in `index.md`. If any are missing, add them before proceeding.

The index format:

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

Keep entries sorted alphabetically within each section. Update on every operation — not just ingests, but also query-filing and lint fixes.

## Step 6: Update Log

Append to `wiki/log.md`:

```
## [{date}] atomize | {Source Title}
- Source: raw/{filename}
- Atoms created: {count} ({breakdown by type})
- Atoms updated: {list of updated atom files}
- Contradictions: {list or "none"}
```

The log is append-only and parseable: `grep "^## \[" wiki/log.md | tail -10`

## Batch Processing

When processing multiple sources at once:
1. Process sequentially (not in parallel — each source may affect the next)
2. Skip Step 2 (user discussion) unless contradictions are found
3. Consolidate log entries into a single batch entry
4. Update index once at the end, not after each source

## Edge Cases

| Situation | Resolution |
|-----------|------------|
| Source overlaps significantly with existing source | Note overlap, only add genuinely new atoms |
| Source is a primary document (legal text, spec) | Summarize but link to raw file for exact wording |
| Source is in a different language than existing atoms | Write this source's atoms in the source's language. Cross-source pages use majority language or ask user. |
| Source contains images | Describe key images in text, reference image files in `raw/assets/` |
| Source is very long (book chapter, 50+ pages) | Break into sections, create atoms per section |
| Atomic candidate spans two types | Create one atom per type and cross-reference with `related` |
