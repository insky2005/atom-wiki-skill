# Query Protocol — Full Reference

Detailed protocol for answering questions against the atomized knowledge base and optionally filing answers as new atoms.

## Trigger

User asks a question about the wiki's domain. No special command needed — any question that relates to the knowledge base's domain triggers this workflow.

## Step 1: Search the Knowledge Base

1. **Read `wiki/index.md`** to find potentially relevant atoms. Match by title, tags, and type.
2. **Read relevant atoms** in full. If an atom references related atoms via `related` links that seem relevant, follow those links too.
3. **Stop conditions**: stop searching when you have sufficient context, or after reading 20+ atoms (work with what you have at that point).

The index is the primary search mechanism at moderate scale. No embedding or vector search is needed for wikis up to ~500 atoms. Beyond that, consider adding a search tool (e.g., `qmd` with hybrid BM25/vector search).

## Step 2: Assemble and Synthesize

Compose an answer that:

- **Directly addresses** the user's question
- **Cites atoms inline**: `[Atom Title](atoms/{type}/{slug}.md)`
- **Notes confidence**: high (3+ corroborating atoms), medium (1-2 atoms), low (inference from incomplete data)
- **Flags gaps**: if the knowledge base lacks information, say so explicitly

### Answer Format by Question Type

| Question Type | Format |
|---------------|--------|
| "What is X?" | Prose explanation, 1-3 paragraphs |
| "Compare X and Y" | Markdown table with dimensions as rows |
| "How does X work?" | Step-by-step explanation |
| "What do we know about X?" | Structured summary with source citations |
| "What are the open questions?" | Numbered list with confidence levels |
| "Summarize X" | Section-based overview |
| "Timeline of X" | Chronological list or table |
| "Pros and cons of X" | Two-column table or structured list |

### Confidence Assessment

When presenting an answer, include a confidence indicator:

- **High confidence**: 3+ corroborating atoms from independent sources, no contradictions
- **Medium confidence**: 1-2 atoms, or multiple atoms from the same source family
- **Low confidence**: inference from incomplete data, single-source claims, or unresolved contradictions exist
- **Unknown**: the wiki contains no relevant atoms

## Step 3: File Decision — Preserve or Skip

After answering, assess: is this answer a valuable artifact worth preserving in the wiki?

**File-worthy signals**:
- Comparison or analysis the user is likely to revisit
- New connection discovered between existing atoms
- Synthesis across 3+ atoms
- Answer fills a gap in the wiki's coverage
- The question itself is a common one that future queries might repeat

**Not file-worthy**:
- Simple factual lookups (fully covered by a single existing atom)
- Clarifying questions about wiki structure
- Trivial or one-off queries

**Before creating or updating, check: does an existing atom already cover the core topic of this answer?**

### Path A: Existing atom covers the topic → UPDATE it

If an existing atom already covers the core topic (e.g. a comparison atom about the same pair of concepts, or a synthesis atom about the same theme):
1. **Update the existing atom** — append the new insight from this query as a new section or integrate it into existing content
2. **Add source reference** — if the query used atoms as sources, add a note like `## Insights from query [{date}]` at the bottom of the atom
3. **Update `updated` date** in the atom's frontmatter
4. **Update `wiki/index.md`** — the entry already exists, but verify it's present
5. Append to `wiki/log.md`:
   ```
   ## [{date}] query-updated | {existing atom title}
   - Question: {original question}
   - Updated atom: atoms/{type}/{slug}.md
   - Related atoms: {list}
   ```

### Path B: No existing atom covers the topic → CREATE a new atom

If no existing atom covers the core topic:
1. **Create the atom** with proper frontmatter at `atoms/{type}/{slug}.md`
2. **Add `related` links** to and from the relevant existing atoms
3. **Update `wiki/index.md`** — add a new entry under the correct type section
4. Append to `wiki/log.md`:
   ```
   ## [{date}] query-filed | {title}
   - Question: {original question}
   - Filed as: atoms/{type}/{slug}.md
   - Related atoms: {list}
   ```

**Important**: always choose one of the two paths. Never skip filing entirely — if the answer is file-worthy, it must be captured either by updating an existing atom or creating a new one.

## Step 4: Final Sync — MANDATORY

After filing the answer (Path A or Path B), verify the knowledge base is consistent:

1. **Verify index.md**: if you created a new atom, confirm it has an entry in `index.md`. If you updated an existing atom, confirm its entry is still present and accurate.
2. **Verify log.md**: confirm the operation is logged with the correct format.
3. **Verify backlinks**: if you added `related` links from the filed/updated atom to existing atoms, add reciprocal `related` links from those atoms back to this one.

## When the Wiki Cannot Answer

If the knowledge base lacks sufficient information:

1. State clearly what's missing
2. Suggest sources or topics that might fill the gap
3. Optionally create a **stub atom** noting the knowledge gap:
   ```yaml
   ---
   title: "{topic}"
   type: concept
   created: {date}
   updated: {date}
   sources: []
   tags: [stub, needs-sources]
   related: [[related-existing-atom]]
   ---

   ## Knowledge Gap

   This topic was identified as relevant but the wiki currently lacks source material.

   **What's missing**: {description of the gap}
   **Suggested sources**: {types of sources that could fill this}
   ```

Stub atoms serve as reminders and help the lint operation identify knowledge gaps systematically.
