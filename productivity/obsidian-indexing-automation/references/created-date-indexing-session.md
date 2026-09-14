# Created-Date Indexing Reference

## Purpose

Provide a stable convention for date-aware Obsidian indexes and generated notes.

## Rules

- Obtain the year and date from the system, never from memory.
- Preserve the source note's created date when it is present.
- Use the generated artifact's creation date in its own frontmatter or metadata.
- Do not overwrite a same-name artifact; add a numeric suffix or ask for direction.
- Keep dates ISO-formatted as `YYYY-MM-DD` when machine comparison matters.
- Use Monday as the first day of the week for weekly grouping and reporting.

## Recommended metadata

```yaml
created: YYYY-MM-DD
updated: YYYY-MM-DD
source_scope: 20_Articles
artifact_type: derived-index
status: active
```

## Verification

After generation, confirm that every in-scope source has a row, every row points to an existing source, and the date in the artifact matches the system date used during creation.
