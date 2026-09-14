---
name: periodic-story-synthesis
description: Use for monthly, quarterly, or yearly story synthesis.
version: 1.2.0
author: Thongchan Thananate
license: MIT
metadata:
  hermes:
    tags: [periodic-review, monthly, quarterly, yearly, obsidian]
---

# Periodic Story Synthesis

Create one evidence-based story synthesis for a completed calendar month, quarter, or year. Roll up the daily story system into a useful account of change, decisions, effects, patterns, and unresolved work.

## When to Use

Use for scheduled or manual monthly, quarterly, and yearly reviews derived from the daily story notes. Use the requested period mode; scheduled runs target the immediately preceding completed period.

The canonical output structure is stored at `80_Templates/Periodic Story Synthesis Zettelkasten.md` in the verified Obsidian vault. Read it before preparing a synthesis. Preserve its semantic fields and heading relationships while omitting unsupported optional sections.

## Period contract

Use Asia/Bangkok calendar boundaries. A scheduled run always targets the immediately preceding completed period:

| Mode | Source preference | Exact destination | Idempotency heading |
|---|---|---|---|
| Monthly | Daily notes for every date in the month | `02_Monthly/YYYY-MM.md` | `## Monthly Story Synthesis` |
| Quarterly | The three monthly synthesis blocks; daily notes fill documented gaps | `03_Quarterly/YYYY-QN.md` | `## Quarterly Story Synthesis` |
| Yearly | The four quarterly synthesis blocks; monthly or daily notes fill documented gaps | `04_Yearly/YYYY.md` | `## Yearly Story Synthesis` |

Resolve the periodic root from the cron prompt or verified vault convention. In this vault, the active year uses `10_Periodic/YYYY_Perioric`; a completed archived year uses `11_Periodic_Archive/YYYY_Periordic`. Prefer the exact active root. Use the archive root only when the active root is absent and the archive root exists. Stop with a clear prerequisite if neither exact root and its numbered subfolders exist. Never discover destinations through fuzzy filename matching. Validate that every source filename belongs to the target period and that the destination filename names that exact period.

Treat existing article indexes and unrelated note sections as preserved content, not evidence for the personal story synthesis. The daily story notes and lower-level story-synthesis blocks are the evidence unless the prompt explicitly adds another source.

## Evidence hierarchy

Enumerate the expected lower-level periods before reading. Record which expected notes exist, which are missing, and which lack a complete synthesis block. Missing notes are coverage gaps; they do not prove that nothing happened.

Prefer the nearest complete lower-level synthesis because it has already deduplicated source activity. Use the next lower level only to fill a named gap or verify a material claim. Do not count the same event again when it appears across daily, monthly, and quarterly notes.

Carry an open loop forward only when the sources do not establish that it was completed, abandoned, or superseded. Record closures and reversals as changes. Separate adopted decisions from suggestions, and observed downstream effects from plausible explanations.

## Synthesis standard

The rollup should answer:

- What was materially different at the end of the period?
- Which constraints, events, or realizations drove those changes?
- Which adopted decisions caused observable downstream effects?
- What meaningful progress, regressions, or reversals occurred?
- Which patterns repeated across more than one source interval?
- What remains unresolved, why, and what is the concrete next action?

Compress repeated episodes into a pattern only when at least two dated observations support it. Preserve important exceptions and turning points. Prefer mechanisms and consequences over a diary-like retelling. Label causal inference and uncertainty plainly.

## Output block

Append one complete block using the mode's idempotency heading:

```markdown
## <Monthly|Quarterly|Yearly> Story Synthesis

### At a Glance
- Three to seven high-value changes, outcomes, and unresolved matters.

### Narrative Arc
Starting state → pressures or triggers → decisions/actions → observed effects → ending state.

### Decisions and Consequences
- Adopted decision — reason — observed downstream effect or current uncertainty.

### Progress and Outcomes
- Material result, including reversals or stalled work where relevant.

### Recurring Patterns
- Evidence-based pattern with at least two dated supporting intervals and its practical implication.

### Open Loops
- Unresolved item — current blocker or uncertainty — concrete next action.

### Next Period
- A small set of evidence-grounded priorities or experiments, clearly identified as recommendations unless already committed.

### Learning Notes

#### <A declarative, transferable claim>
- **Claim:** <one atomic idea distilled across the period>
- **Evidence:** <two or more exact Obsidian links to supporting lower-level headings>
- **Area:** <one or two verified canonical knowledge hubs from `30_Area` or `31_Technical_Area`>
- **Connection:** <another learning note, verified vault note, or plain concept/tag>
- **Use:** <future rule, question, or experiment>

^zettel-<period-id>-short-slug

### Connections
- Sources: <compact links to the lower-level synthesis notes used>
- Parent periods: <deliberate links to the quarter/year that will contain this period>

### Coverage
- Period: <exact Bangkok date range>
- Reviewed: <compact list or count of source notes/periods>
- Missing or incomplete: <exact gaps, or None>
- Generated: <actual Asia/Bangkok timestamp>
```

Use only sections supported by the evidence, except `Coverage`, which is required. Keep the block readable: consolidate closely related material and avoid repeating the same fact under several headings.

Learning Notes are the Zettelkasten layer. Each note contains one reusable claim, not a compressed event summary. Monthly claims require support from at least two dated observations when possible; quarterly and yearly claims require support from at least two lower-level periods. Use exact heading links such as `[[2026-09-14#A constraint can change the right decision]]` or `[[2026-09#Monthly Story Synthesis]]`. Every learning note must link to one or two existing canonical Area hubs; search the exact top-level notes in `30_Area` and `31_Technical_Area` before choosing. Search before linking elsewhere. Use one to seven learning notes according to evidence density, and omit the section when no durable lesson is supported. Block IDs must be unique and use `YYYY-MM`, `YYYY-QN`, or `YYYY` as the period ID.

After the period note is verified, append one missing entry per learning note to each selected Area hub's final `## Zettelkasten Index`:

```markdown
- [[<period note>#Exact learning-note heading]] — <short retrieval cue>
```

The exact heading link is the idempotency key. Area updates preserve all existing bytes and append only missing entries. A retry of an already complete period synthesis must still audit and repair missing Area-index entries. Report partial indexing errors precisely so a later retry can converge without rewriting the period note.

## Append safety

Read the complete destination before any write. Existing bytes are immutable. If the exact idempotency heading exists with a complete block, verify it and make no change. If the heading exists with a partial or malformed block, report a structural conflict and stop.

Prepare the entire append, re-read the destination immediately before committing, and stop if it changed. Create a missing destination with the exact period title (`# YYYY-MM`, `# YYYY-QN`, or `# YYYY`). Otherwise append the block without rewriting, reordering, or normalizing prior content. Use the official Obsidian CLI from inside the verified vault. An explicit dry test produces a preview only and never consumes the period.

## Completion

Re-read the destination and verify its period, exactly one idempotency heading, the required Coverage section, preserved prior bytes, and no unrelated changes. Verify every selected Area hub has exactly one index entry back to each learning-note heading. Report created, appended, unchanged, or error; include the exact path, source coverage, Area-index status, and gaps.
