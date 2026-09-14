# Area Indexing Automation Reference

## Use case

Use this reference when maintaining a derived index for an Obsidian area or article corpus.

## Required fields

- Exact source path
- Human-readable title
- Primary theme
- Commercial priority or review state
- Candidate buyer
- Buyer problem or decision
- Possible monetization route
- Classification signal
- Confidence and limitations

## Batch procedure

1. Enumerate the exact in-scope files recursively.
2. Exclude only documented system files, caches, and prior generated outputs.
3. Read metadata and a bounded body window.
4. Normalize only for comparison; preserve original paths and titles in output.
5. Assign one primary category using explicit rules.
6. Emit stable, deterministic ordering.
7. Count source files and index rows programmatically.
8. Check duplicate paths and missing paths.
9. Write one derived Markdown index.
10. Record method, exclusions, and limitations.

## Commercial triage

A direct candidate must connect to a buyer decision such as product positioning, game publishing, market entry, pricing, retention, workflow automation, or behavioral friction. General-interest content is useful for audience building but should not be labeled commercially validated.

## Verification commands

```bash
cd "$VAULT_PATH" && obsidian files path="20_Articles" format=json
cd "$VAULT_PATH" && obsidian read path="PATH/TO/INDEX.md"
```

For large corpora, use a deterministic script for deduplication and count comparison. Never infer totals from truncated terminal output.
