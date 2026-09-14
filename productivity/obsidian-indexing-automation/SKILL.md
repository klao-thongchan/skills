---
name: obsidian-indexing-automation
description: "Index and tag Obsidian vault metadata."
version: 1.0.0
license: MIT
platforms: [macos, linux, windows]
metadata:
  hermes:
    tags: [obsidian, indexing, metadata, taxonomy, tags]
---

# Obsidian Indexing Automation

## Mission

Build and maintain deterministic indexes over Obsidian notes without changing source content unless the user explicitly authorizes metadata edits.

## Trigger

Use for requests to index notes, classify articles, enrich metadata, audit tags, build MOCs, detect orphan notes, or maintain area indexes.

## Source of truth

- Vault: `/Users/klao-pro/Documents/sundayhalfob` unless `OBSIDIAN_VAULT_PATH` is set.
- Existing folder architecture is authoritative.
- Obsidian CLI is preferred for discovery and note reads.
- Use Python only for batch parsing, deduplication, statistical analysis, or transformations that CLI cannot perform efficiently. State why when using it.

## Workflow

1. Verify vault and CLI from inside the vault.
2. Establish exact scope, including recursive subfolders and excluded files.
3. List files and record the baseline count.
4. Read metadata and enough body text to support classification.
5. Assign one primary category per note unless the requested schema allows multiple categories.
6. Preserve exact source paths and identifiers.
7. Generate the index in the requested existing folder.
8. Validate that every in-scope file appears exactly once, or explain exclusions.
9. Re-read the generated index and report files scanned, rows produced, and files modified.

## Classification discipline

Separate:

- Observed metadata
- Keyword signal
- Human or model inference
- Confidence
- Manual-review status

A keyword match is not proof of a topic. Use a `needs review` bucket for ambiguous notes. Do not label an article commercially valuable merely because it contains business vocabulary.

## Index schema

A useful commercial index may include:

| Field | Meaning |
|---|---|
| Source path | Exact vault-relative path |
| Title | Parsed heading or filename |
| Primary theme | One dominant topic |
| Priority | A, B, C, or review |
| Candidate buyer | Who may benefit |
| Buyer problem | Decision or pain addressed |
| Possible route | Service, content, product, or none |
| Signal | Explainable classification evidence |

## Write policy

- Do not modify source notes by default.
- Do not overwrite an existing index without checking its contents and scope.
- Prefer one derived Markdown artifact over batch-editing hundreds of notes.
- Use Obsidian wikilinks only for verified paths.
- Keep a method and limitations section in generated indexes.

## Verification

Use a programmatic count for large indexes. Compare source-file count to index-entry count and check for duplicate source paths. Inspect the top of the generated note and at least one entry from each category. A successful write call alone is insufficient.

## Failure modes

- **Count mismatch:** re-scan before reporting completion.
- **Truncated CLI output:** use JSON or a saved output file; do not infer totals from displayed text.
- **Over-broad category:** lower confidence or split the category.
- **Missing wikilink:** preserve the exact source path and flag it.
- **Mixed archives:** state whether archive folders were included.

## Completion standard

The index is complete only when coverage is verified, limitations are documented, and source notes remain unchanged unless explicitly approved.

## Related files

- `references/created-date-indexing-session.md`
- `obsidian_cli` skill
