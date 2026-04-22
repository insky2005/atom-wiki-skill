# Conventions — Full Reference

Detailed conventions for the atomized knowledge base.

## File Naming

- **Lowercase, hyphens, no spaces**: `transformer-architecture.md`, not `Transformer Architecture.md`
- **Descriptive slugs**: the filename should hint at the content. `self-attention-mechanism.md` not `sa.md`
- **Source filenames**: same convention. Place in `raw/` before processing

## Atomic Unit Principles

### One Idea Per Atom
If a paragraph introduces two distinct concepts, split into two atoms and cross-reference them via `related`. Merging is always easier than splitting — err on the side of more granular atoms.

### Self-Contained
An atom should make sense without reading other atoms. Include enough context in the body — don't rely on the reader having seen other files. This doesn't mean repeating everything; it means providing enough framing that the atom is independently understandable.

### Concise
Aim for 50-300 words of body content. If an atom grows beyond 500 words, consider whether it actually contains multiple ideas that should be split. Synthesis atoms are an exception — they may be longer due to their integrative nature.

### Tagged and Categorized
Tags enable flexible retrieval beyond the fixed type hierarchy. The `type` field determines directory placement; tags provide additional dimensions for search. Use both consistently.

## Tagging Guidelines

- **Prefer existing tags** over creating new ones. Check `index.md` for tag usage patterns before introducing a new tag.
- **Be specific but not overly narrow**: `machine-learning` is good; `ml` is too vague; `transformer-based-deep-learning-models` is too narrow.
- **Use kebab-case**: `natural-language-processing`, not `Natural Language Processing` or `nlp`.
- **Avoid synonyms as separate tags**: pick one canonical form and use it consistently.
- **Common tag categories**: domain, method, technology, era, source-type

## Cross-Referencing

- Use `[[wikilink]]` syntax in body text for inline references
- Use the `related` frontmatter field for significant structural relationships
- Cross-references should be bidirectional when topically relevant: if A references B, B should usually reference A
- Don't over-link: only reference atoms that genuinely add context or enable navigation

## Source Attribution

- In `sources` frontmatter, use filenames only (e.g. `[article.md, paper.md]`), not full paths like `raw/article.md`
- Cite sources inline when quoting or paraphrasing specific claims: `[Source Title](../sources/{slug}.md)` or simply reference the source name
- When an atom's content is derived from multiple sources, list all contributing sources

## Language Rules

All wiki content follows the language of the source being processed:

1. **Detection**: On each atomize operation, detect the source's primary language before writing any atom.
2. **Content atoms**: All atoms derived from a source are written in the source's language.
3. **Structural elements stay English**: YAML frontmatter keys, `type` values, filename slugs, table column headers in `index.md` / `log.md`, section headings in index/log — these are protocol identifiers, not content.
4. **Cross-source atoms**: For comparisons, synthesis, and Q&A that span multiple sources, use the language of the majority of sources. If tied, ask the user.
5. **Conversations**: When discussing takeaways with the user, use the same language as the source(s) involved.

## Preservation vs. Critique

- **Preserve original claims faithfully**: summarize what the source says accurately
- **Critique separately**: if you disagree with a source's claims, add analysis as a separate paragraph or a separate atom — don't silently modify the source's claims
- **Contradictions are data**: when two sources disagree, document both sides rather than picking one

## Quick Reference

| Aspect | Convention |
|--------|-----------|
| Filename | lowercase-hyphens.md |
| One idea | per atom |
| Body length | 50-300 words (synthesis may be longer) |
| Tags | kebab-case, reuse existing |
| Sources field | filenames only, no paths |
| Language | follow source language |
| Links | `[[wikilink]]` in body, `related` in frontmatter |
