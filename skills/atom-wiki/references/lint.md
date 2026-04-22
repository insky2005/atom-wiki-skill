# Lint Protocol — Full Reference

Detailed protocol for knowledge base health checks. Catches structural issues, contradictions, and knowledge gaps.

## Trigger

User says "lint", "health check", "review wiki", "检查知识库", "review consistency", or "wiki maintenance".

## Step 1: Full Scan

Read `wiki/index.md`, then read every atom listed. Build an internal model of:
- All atoms and their types
- All `[[wikilinks]]` and `related` references and their targets
- All `sources` frontmatter entries
- All contradiction blocks
- All tags and their usage patterns

## Step 2: Run Checks

Execute each check category. Collect findings as a numbered list.

### 2.1 Structural Checks

| Check | Issue | Severity |
|-------|-------|----------|
| Orphan atoms | Atom exists but has no `related` links in or out | Medium |
| Broken links | `[[target]]` or `related` references a file that doesn't exist | High |
| Missing atoms | Concept/entity mentioned 3+ times across atoms but has no dedicated atom | Medium |
| Index drift | Atom exists in `atoms/` but not listed in `index.md` | High |
| Empty atoms | Atom has frontmatter but no meaningful body content | Low |
| Wrong directory | Atom `type` doesn't match its directory location | High |

### 2.2 Content Checks

| Check | Issue | Severity |
|-------|-------|----------|
| Unresolved contradictions | Contradiction block with `Resolution: pending` older than 3 operations | Medium |
| Stale claims | Atom content contradicted by newer sources without the atom being updated | High |
| Single-source atoms | Atom backed by only 1 source (flag for verification, not necessarily an error) | Low |
| Outdated overview/synthesis | Synthesis atom not updated since 3+ atomize operations on related topics | Medium |

### 2.3 Cross-reference Checks

| Check | Issue | Severity |
|-------|-------|----------|
| Missing backlinks | Atom A references Atom B via `related`, but B doesn't reference A (when topically relevant) | Low |
| Isolated clusters | Groups of atoms that reference each other but not the rest of the wiki | Medium |
| Tag inconsistency | Same concept tagged differently across atoms | Low |
| Redundant atoms | Two atoms cover substantially the same idea (possible merge candidate) | Medium |

## Step 3: Report

Output findings grouped by severity:

```markdown
## Knowledge Base Lint Report — {date}

**Summary**: {total} issues — {high} high, {medium} medium, {low} low

### High ({count})
1. {finding with specific file references}
...

### Medium ({count})
1. ...

### Low ({count})
1. ...

### Suggestions
- {Proactive recommendations: topics to explore, sources to find, atoms to create}
- {Mergers to consider}
- {Gaps identified from stub atoms}
```

## Step 4: Triage

Ask user: "Which items should I fix now?" Accept:
- "All" — fix everything
- "High only" — fix high-severity items
- Specific numbers — "Fix 1, 3, 7"
- "None" — just log the report

## Step 5: Execute Fixes

For each approved fix:
- Create/update atoms as needed
- Resolve contradictions if newer data provides clear resolution
- Merge redundant atoms (preserve both sources in `sources` field, combine `tags` and `related`)
- Update cross-references bidirectionally
- Update `wiki/index.md`

## Step 6: Log

Append to `wiki/log.md`:
```
## [{date}] lint
- Total issues: {count}
- High: {count}, Medium: {count}, Low: {count}
- Fixed: {list of fixed items}
- Deferred: {list of deferred items}
```

## Suggested Lint Schedule

| Wiki Size | Recommended Frequency |
|-----------|-----------------------|
| < 20 atoms | After every 5 atomize operations |
| 20-100 atoms | After every 10 atomize operations |
| 100+ atoms | After every 20 atomize operations, or when queries return inconsistent results |
