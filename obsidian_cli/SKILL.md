---
name: obsidian_cli
description: Operate Klao's Obsidian vault through its native CLI.
version: 1.1.0
metadata:
  hermes:
    tags: [obsidian, cli, markdown, pkm, vault, sundayhalfob, notes, knowledge-base, workflows, prompts]
    category: note-taking
    requires_toolsets: [terminal]
    config:
      - key: obsidian_cli.vault_path
        description: Absolute filesystem path to Klao's Obsidian vault.
        default: /Users/klao-pro/Documents/sundayhalfob
        prompt: Obsidian vault path
---

# Obsidian CLI Vault Operator

## Mission

Operate Klao's Obsidian vault using the official Obsidian CLI.

Target vault:

    /Users/klao-pro/Documents/sundayhalfob

This vault uses the following top-level structure:

    00_SYSTEM
    10_Periodic
    11_Periodic_Archive
    20_Articles
    21_Articles_Archive
    30_Area
    31_Technical_Area
    32_Techincal_Archive
    33_Commercial_Thesis
    60_Workflows
    70_Prompts
    80_Templates

Use this skill when Klao asks to:

- search the Obsidian vault
- read notes
- inspect tags
- inspect tasks
- inspect backlinks
- inspect outgoing links
- find unresolved links
- find orphan notes
- find dead-end notes
- create review notes
- create MOCs
- create workflows
- create prompts
- create templates
- learn from the Obsidian vault
- turn raw articles into durable Markdown artifacts
- open notes in Obsidian
- use Obsidian CLI

## Non-Negotiable Vault Rule

Always run Obsidian CLI commands from inside the vault directory.

Correct pattern:

    cd "$VAULT_PATH" && obsidian <command>

Do not use a filesystem path as:

    vault=/Users/klao-pro/Documents/sundayhalfob

`vault=<name>` or `vault=<id>` is only for Obsidian's vault-name or vault-ID targeting. For this vault, always prefer changing directory into the vault path first.

## Tool Priority Policy

### Default Execution Path

For all normal Obsidian vault operations, use terminal commands with the official Obsidian CLI.

Preferred pattern:

```bash
cd "$VAULT_PATH" && obsidian <command>
```

### Use Obsidian CLI First For

- searching notes
- reading notes
- creating notes
- appending notes
- opening notes
- listing files/folders
- inspecting tags
- inspecting tasks
- inspecting backlinks
- inspecting outgoing links
- inspecting unresolved links
- inspecting orphans
- inspecting deadends
- reading properties
- setting properties

### Avoid Python By Default

Do not use Python for normal vault operations.

Python is allowed only when:

- Klao explicitly asks for Python
- Obsidian CLI cannot perform the operation
- the task requires batch parsing, deduplication, statistical analysis, or large-scale transformation
- the skill first explains why Obsidian CLI is insufficient

### Long Markdown Note Creation

For long Markdown note creation, prefer shell heredoc or Obsidian CLI `create`/`append`. Do not default to Python.

Preferred long-note pattern:

```bash
cat > "$VAULT_PATH/path/to/note.md" <<'MARKDOWN'
# Title

Content here.
MARKDOWN

cd "$VAULT_PATH" && obsidian open path="path/to/note.md"
```

### Reporting When Python Is Used

If Python is used, report:

- why Obsidian CLI was not enough
- exact Python command or script used
- files read
- files modified
- safety impact

## Vault Path Resolution

Resolve `VAULT_PATH` in this order:

1. Hermes skill config value:

       skills.config.obsidian_cli.vault_path

2. Environment variable:

       OBSIDIAN_VAULT_PATH

3. Hard-coded fallback:

       /Users/klao-pro/Documents/sundayhalfob

Before doing any operation, verify:

    VAULT_PATH="/Users/klao-pro/Documents/sundayhalfob"
    test -d "$VAULT_PATH" && echo "Vault exists: $VAULT_PATH"
    command -v obsidian
    cd "$VAULT_PATH" && obsidian help >/dev/null

If `obsidian` is not found, tell Klao to enable Obsidian CLI in:

    Obsidian → Settings → General → Command line interface

On macOS, if the CLI symlink is missing, suggest:

    sudo ln -sf /Applications/Obsidian.app/Contents/MacOS/obsidian-cli /usr/local/bin/obsidian

## Vault Folder Semantics

Use the folder architecture as operating boundaries.

### 00_SYSTEM

Purpose:

- vault rules
- taxonomy
- metadata standards
- MOCs
- dashboards
- indexes
- operating protocols
- Hermes/agent instructions
- system-level governance

Use this folder for:

- `00_SYSTEM/Hermes Obsidian Operating Protocol.md`
- `00_SYSTEM/Vault Index.md`
- `00_SYSTEM/Tag Taxonomy.md`
- `00_SYSTEM/MOC - Agents.md`
- `00_SYSTEM/MOC - Product Strategy.md`

Do not put raw article summaries here unless they become system doctrine.

### 10_Periodic (formerly 10_Preordic)

Purpose:

- daily notes (`10_Periodic/2026_Periodic/01_Daily`)
- weekly reviews
- monthly reviews (`10_Periodic/2026_Periodic/02_Monthly`)
- quarterly reviews (`10_Periodic/2026_Periodic/03_Quarterly`)
- yearly reviews (`10_Periodic/2026_Periodic/04_Yearly`)
- periodic syntheses
- retrospectives
- recurring vault audits

Use this folder for:

- `10_Periodic/Hermes Vault Learning Baseline - YYYY-MM-DD.md`
- `10_Periodic/Weekly Review - YYYY-WW.md`
- `10_Periodic/Monthly Review - YYYY-MM.md`

Historical archives live in `11_Periodic_Archive/`.

### 20_Articles

Purpose:

- source articles
- reading notes
- captured external knowledge
- article-to-insight transformations

Use this folder for:

- raw pasted articles
- summarized articles
- annotated source notes
- extraction from NotebookLM outputs
- article synthesis notes

Folder structure convention:

- Organize articles under year subdirectories: `20_Articles/<YYYY>_Article/` (e.g. `20_Articles/2026_Article/`). Do not place loose notes directly in the `20_Articles/` root.

Standard frontmatter and header schema for articles:

```markdown
---
title: "Article Title"
description: >-
  Concise plain-language summary of the thesis or scope.
date: 'YYYY-MM-DD'
categories:
  - Category1
  - Category2
keywords:
  - keyword1
  - keyword2
slug: ''
---

Created date: [[YYYY-MM-DD]]
Created month: [[YYYY-MM]]
Created quarter: [[YYYY-Q#]]
Created year: [[YYYY]]

Tags: [[Tag Name]] [[Another Tag]]
```

Default article transformation format:

    # Title

    ## Source Context

    ## Core Thesis

    ## Mechanism

    ## Strategic Implication

    ## Technical / Operational Implication

    ## Behavioral Economics Angle

    ## Weak Assumptions

    ## Links Into Vault

    ## Tags

### 30_Area

Purpose:

- durable non-technical areas of responsibility
- product strategy
- behavioral economics
- marketing
- game publishing
- business models
- career
- research domains
- conversational captures and chat Q&A research (`30_Area/chatGPT Conversations/`)

Use this folder for evergreen conceptual notes, area-level MOCs, and captured chat conversations.

#### Chat Conversation & Q&A Note Standard

When turning conversational Q&A, travel guides, or topic discussions into vault notes under `30_Area/chatGPT Conversations/`:
Prepend the standard vault temporal wikilink header:

```markdown
Created date: [[YYYY-MM-DD]]
Created month: [[YYYY-MM]]
Created quarter: [[YYYY-Q#]]
Created year: [[YYYY]]
```

Examples:

- `30_Area/Product Strategy.md`
- `30_Area/Behavioral Economics.md`
- `30_Area/Game Publishing.md`
- `30_Area/Market Narrative Design.md`
- `30_Area/chatGPT Conversations/Baltic Countries Travel Guide.md`

### 31_Technecial_Area / 31_Technical_Area

The visible vault folder is:

    31_Technical_Area

Purpose:

- technical systems
- AI agents
- Codex
- Hermes
- n8n
- Firebase
- OpenAI workflows
- automation architecture
- developer tooling
- cross-platform systems

Use this folder for technical evergreen notes.

Examples:

- `31_Technical_Area/Hermes Agent Architecture.md`
- `31_Technical_Area/Codex Workflow Architecture.md`
- `31_Technical_Area/Obsidian CLI.md`
- `31_Technical_Area/Agent Memory Systems.md`
- `31_Technical_Area/n8n Automation Patterns.md`

### 60_Workflows

Purpose:

- reusable execution workflows
- SOPs
- agent loops
- automation procedures
- recurring operating systems
- Hermes cron patterns
- Codex task flows

Use this folder for step-by-step repeatable processes.

Examples:

- `60_Workflows/Hermes Weekly Vault Review Workflow.md`
- `60_Workflows/NotebookLM to Obsidian Workflow.md`
- `60_Workflows/Article to Evergreen Note Workflow.md`
- `60_Workflows/Codex Vibe Coding Workflow.md`

### 70_Prompts

Purpose:

- reusable prompts
- agent instructions
- Telegram command templates
- Codex prompts
- Hermes prompts
- NotebookLM prompts
- adversarial review prompts

Use this folder for reusable language patterns.

Examples:

- `70_Prompts/Hermes Vault Audit Prompt.md`
- `70_Prompts/Codex Implementation Prompt.md`
- `70_Prompts/Strategic Article Analysis Prompt.md`

### 80_Templates

Purpose:

- reusable note templates
- article templates
- MOC templates
- workflow templates
- project templates
- review templates

Use this folder for note scaffolds.

Examples:

- `80_Templates/Article Synthesis Template.md`
- `80_Templates/Weekly Review Template.md`
- `80_Templates/MOC Template.md`
- `80_Templates/Workflow Template.md`
- `80_Templates/Project Note Template.md`

## Operating Principles

Obsidian is the source of truth.

Hermes memory should only store compact operational facts, such as:

- vault path
- taxonomy rules
- naming conventions
- folder semantics
- workflow preferences
- active high-level projects

Do not store full article summaries, raw notes, long project details, or temporary thinking in Hermes memory.

For durable knowledge, write Markdown notes into the vault.

Do not create new top-level folders without explicit approval.

Use the existing top-level folder structure unless Klao asks to redesign the vault.

## Safety Policy

Default mode is read-only.

### Placeholder Path Handling

Treat obviously fake or instructional paths as placeholders, never as real files. Examples include:

- `PASTE_EXACT_NOTE_NAME.md`
- `EXACT_NOTE_NAME.md`
- `ARTICLE_NAME.md`
- `SHORT_TITLE.md`
- any path containing an obviously fake placeholder such as `YOUR_NOTE`, `REPLACE_ME`, or `TODO`

When a placeholder path is provided:

1. Do not attempt to read, modify, or create a synthesis from that path.
2. Search inside `20_Articles` for suitable source notes.
3. Recommend 1–3 candidates with brief reasons.
4. Ask Klao to confirm the source article before creating a derived note.

### Auto-Selection Mode

If Klao explicitly says “pick one article,” “choose a suitable article,” or “auto-select,” select one source article autonomously from `20_Articles`.

Selection priority:

1. AI agents, Hermes, Codex, automation, product strategy, behavioral economics, or operating systems.
2. Notes that are not very short.
3. Notes with a clear argument, mechanism, or operational structure.

Never modify the selected source article.

### Safe Synthesis Output

When creating a derived synthesis note:

- Never modify the source article.
- Create only one new Markdown note unless Klao explicitly asks for more.
- Check whether the output file already exists before creating it. Ask before overwriting.
- Default test synthesis output folder: `10_Preordic/`.
- Default workflow output folder: `60_Workflows/`.
- Default prompt output folder: `70_Prompts/`.
- Default system or MOC output folder: `00_SYSTEM/`.

Ask for explicit confirmation before:



- overwriting files
- deleting files
- permanently deleting files
- moving files
- renaming files
- batch-editing multiple notes
- restoring file history
- changing plugin settings
- enabling or disabling plugins
- installing or uninstalling plugins
- running developer commands
- running `eval`
- executing arbitrary Obsidian command IDs through `obsidian command`
- creating new top-level folders

Never permanently delete files unless Klao explicitly says permanent delete.

When Klao clearly asks for a new artifact, it is acceptable to create one new Markdown note in the correct existing folder.

## Core Read-Only Commands

Vault info:

    cd "$VAULT_PATH" && obsidian vault
    cd "$VAULT_PATH" && obsidian vault info=path
    cd "$VAULT_PATH" && obsidian vault info=files
    cd "$VAULT_PATH" && obsidian vault info=folders
    cd "$VAULT_PATH" && obsidian vault info=size

Files and folders:

    cd "$VAULT_PATH" && obsidian files
    cd "$VAULT_PATH" && obsidian files total
    cd "$VAULT_PATH" && obsidian folders
    cd "$VAULT_PATH" && obsidian folders total
    cd "$VAULT_PATH" && obsidian folder path="00_SYSTEM"
    cd "$VAULT_PATH" && obsidian folder path="10_Preordic"
    cd "$VAULT_PATH" && obsidian folder path="20_Articles"
    cd "$VAULT_PATH" && obsidian folder path="30_Area"
    cd "$VAULT_PATH" && obsidian folder path="31_Technical_Area"
    cd "$VAULT_PATH" && obsidian folder path="60_Workflows"
    cd "$VAULT_PATH" && obsidian folder path="70_Prompts"
    cd "$VAULT_PATH" && obsidian folder path="80_Templates"

Search:

    cd "$VAULT_PATH" && obsidian search query="Hermes"
    cd "$VAULT_PATH" && obsidian search query="Hermes" format=json
    cd "$VAULT_PATH" && obsidian search query="Hermes" path="31_Technical_Area" limit=20
    cd "$VAULT_PATH" && obsidian search query="agent" path="31_Technical_Area" limit=20
    cd "$VAULT_PATH" && obsidian search query="workflow" path="60_Workflows" limit=20
    cd "$VAULT_PATH" && obsidian search query="prompt" path="70_Prompts" limit=20
    cd "$VAULT_PATH" && obsidian search:context query="Hermes" limit=20
    cd "$VAULT_PATH" && obsidian search:context query="Hermes" format=json limit=20

Read notes:

    cd "$VAULT_PATH" && obsidian read path="00_SYSTEM/Hermes Obsidian Operating Protocol.md"
    cd "$VAULT_PATH" && obsidian read file="Hermes Obsidian Operating Protocol"

Tags:

    cd "$VAULT_PATH" && obsidian tags
    cd "$VAULT_PATH" && obsidian tags counts
    cd "$VAULT_PATH" && obsidian tags counts sort=count
    cd "$VAULT_PATH" && obsidian tags counts format=json
    cd "$VAULT_PATH" && obsidian tag name="project" verbose

Tasks:

    cd "$VAULT_PATH" && obsidian tasks
    cd "$VAULT_PATH" && obsidian tasks todo
    cd "$VAULT_PATH" && obsidian tasks done
    cd "$VAULT_PATH" && obsidian tasks todo verbose
    cd "$VAULT_PATH" && obsidian tasks total
    cd "$VAULT_PATH" && obsidian tasks daily

Links:

    cd "$VAULT_PATH" && obsidian backlinks path="31_Technical_Area/Hermes Agent Architecture.md"
    cd "$VAULT_PATH" && obsidian backlinks path="31_Technical_Area/Hermes Agent Architecture.md" counts
    cd "$VAULT_PATH" && obsidian backlinks path="31_Technical_Area/Hermes Agent Architecture.md" format=json
    cd "$VAULT_PATH" && obsidian links path="31_Technical_Area/Hermes Agent Architecture.md"
    cd "$VAULT_PATH" && obsidian links path="31_Technical_Area/Hermes Agent Architecture.md" total
    cd "$VAULT_PATH" && obsidian unresolved
    cd "$VAULT_PATH" && obsidian unresolved counts
    cd "$VAULT_PATH" && obsidian unresolved counts verbose
    cd "$VAULT_PATH" && obsidian orphans
    cd "$VAULT_PATH" && obsidian orphans total
    cd "$VAULT_PATH" && obsidian deadends
    cd "$VAULT_PATH" && obsidian deadends total

Outline:

    cd "$VAULT_PATH" && obsidian outline path="31_Technical_Area/Hermes Agent Architecture.md"
    cd "$VAULT_PATH" && obsidian outline path="31_Technical_Area/Hermes Agent Architecture.md" format=json
    cd "$VAULT_PATH" && obsidian outline path="31_Technical_Area/Hermes Agent Architecture.md" total

Properties:

    cd "$VAULT_PATH" && obsidian properties
    cd "$VAULT_PATH" && obsidian properties counts
    cd "$VAULT_PATH" && obsidian properties format=json
    cd "$VAULT_PATH" && obsidian properties path="31_Technical_Area/Hermes Agent Architecture.md"
    cd "$VAULT_PATH" && obsidian property:read path="31_Technical_Area/Hermes Agent Architecture.md" name=status

Recent files:

    cd "$VAULT_PATH" && obsidian recents
    cd "$VAULT_PATH" && obsidian recents total

## Write Commands

Create a short system note:

    cd "$VAULT_PATH" && obsidian create path="00_SYSTEM/Hermes Obsidian Operating Protocol.md" content="# Hermes Obsidian Operating Protocol\n\nContent here." open

Create a periodic review note:

    cd "$VAULT_PATH" && obsidian create path="10_Preordic/Weekly Review - YYYY-WW.md" content="# Weekly Review - YYYY-WW\n\nContent here." open

Create an article synthesis note (in the current year subfolder):

    cd "$VAULT_PATH" && obsidian create path="20_Articles/2026_Article/Article Title.md" content="# Article Title\n\nContent here." open

Create an area note:

    cd "$VAULT_PATH" && obsidian create path="30_Area/Product Strategy.md" content="# Product Strategy\n\nContent here." open

Create a technical note:

    cd "$VAULT_PATH" && obsidian create path="31_Technical_Area/Hermes Agent Architecture.md" content="# Hermes Agent Architecture\n\nContent here." open

Create a workflow note:

    cd "$VAULT_PATH" && obsidian create path="60_Workflows/Hermes Weekly Vault Review Workflow.md" content="# Hermes Weekly Vault Review Workflow\n\nContent here." open

Create a prompt note:

    cd "$VAULT_PATH" && obsidian create path="70_Prompts/Hermes Vault Audit Prompt.md" content="# Hermes Vault Audit Prompt\n\nContent here." open

Create a template note:

    cd "$VAULT_PATH" && obsidian create path="80_Templates/Article Synthesis Template.md" content="# Article Synthesis Template\n\nContent here." open

Append:

    cd "$VAULT_PATH" && obsidian append path="10_Preordic/Weekly Review - YYYY-WW.md" content="\n\nAdditional note."

Prepend after frontmatter:

    cd "$VAULT_PATH" && obsidian prepend path="10_Preordic/Weekly Review - YYYY-WW.md" content="Summary paragraph."

Set property:

    cd "$VAULT_PATH" && obsidian property:set path="10_Preordic/Weekly Review - YYYY-WW.md" name=status value=active type=text

Open a note:

    cd "$VAULT_PATH" && obsidian open path="10_Preordic/Weekly Review - YYYY-WW.md"

For long generated Markdown, prefer writing with shell redirection or Python, then open with Obsidian CLI:

    mkdir -p "$VAULT_PATH/10_Preordic"
    cat > "$VAULT_PATH/10_Preordic/Hermes Vault Learning Baseline - YYYY-MM-DD.md" <<'MARKDOWN'
    # Hermes Vault Learning Baseline - YYYY-MM-DD

    Content here.
    MARKDOWN

    cd "$VAULT_PATH" && obsidian open path="10_Preordic/Hermes Vault Learning Baseline - YYYY-MM-DD.md"

## Routing Rules

When creating or updating notes, route content by function:

| Content Type | Destination |
|---|---|
| Vault rules, indexes, MOCs, taxonomy, agent protocol | `00_SYSTEM/` |
| Daily, weekly, monthly, periodic review | `10_Periodic/` |
| Raw articles, article summaries, source notes | `20_Articles/` |
| Product, behavioral, strategy, marketing, game publishing domains | `30_Area/` |
| Conversational Q&A captures, chat travel guides, ad-hoc Q&A notes | `30_Area/chatGPT Conversations/` |
| Hermes, Codex, AI agents, n8n, Firebase, OpenAI, technical systems | `31_Technical_Area/` |
| Repeatable execution loops and SOPs | `60_Workflows/` |
| Reusable prompts and Telegram command templates | `70_Prompts/` |
| Reusable note templates | `80_Templates/` |

If unsure where a note belongs, ask Klao before creating it.

## Vault Learning Audit Workflow

When Klao asks Hermes to learn from the vault:

1. Resolve and verify `VAULT_PATH`.
2. Run read-only commands first.
3. Inspect:
   - top-level folder structure
   - total files
   - total folders
   - tags and tag counts
   - unresolved links
   - orphan notes
   - dead-end notes
   - incomplete tasks
   - recent files if relevant
4. Search for active strategic domains:
   - Hermes
   - Codex
   - agent
   - automation
   - NotebookLM
   - Obsidian
   - behavioral economics
   - product strategy
   - game publishing
5. Create one synthesis note only if requested.
6. Default output location:

       10_Preordic/Hermes Vault Learning Baseline - YYYY-MM-DD.md

7. Do not modify source notes unless Klao explicitly approves.
8. Report what was read, created, modified, and skipped.

The baseline note should include:

- vault map
- folder semantics
- main knowledge domains
- active projects
- recurring tags
- naming patterns
- weak taxonomy signals
- candidate MOCs
- orphan/dead-end/unresolved-link signals
- recommended weekly review workflow
- compact Hermes memory candidates
- items that should remain only in Obsidian

## MOC Creation Workflow

When creating a Map of Content:

1. Search relevant notes.
2. Read only the most relevant files.
3. Create MOCs in:

       00_SYSTEM/

4. Use Obsidian wikilinks.
5. Mark uncertain links as possible forward references.
6. Do not claim a note exists unless verified by search or file listing.

Example MOC destinations:

    00_SYSTEM/MOC - Hermes.md
    00_SYSTEM/MOC - Codex.md
    00_SYSTEM/MOC - Product Strategy.md
    00_SYSTEM/MOC - Behavioral Economics.md
    00_SYSTEM/MOC - Game Publishing.md

## Article Processing Workflow

When Klao provides an article or requests an article written into the vault:

1. Route into `20_Articles/<YYYY>_Article/` matching the current year (e.g. `20_Articles/2026_Article/`).
2. Verify target note path does not already exist before creating; prompt before overwriting.
3. Prepend standard YAML frontmatter (`title`, `description`, `date`, `categories`, `keywords`, `slug`) and temporal wikilink breadcrumbs (`Created date: [[...]]`, `Created month: [[...]]`, `Created quarter: [[...]]`, `Created year: [[...]]`, `Tags: [[...]]`).
4. Treat raw articles as source material; synthesize with concrete mechanisms, empirical evidence, and clear structural implications.
5. Extract durable concepts into `30_Area/` or `31_Technical_Area/` only if requested.
6. Create workflows in `60_Workflows/` only when the article contains repeatable execution logic.
7. Create prompts in `70_Prompts/` only when the article contains reusable prompt patterns.
8. Verify creation by checking note outline via Obsidian CLI (`obsidian outline path="..."`). Avoid piping large files through `obsidian read` during verification as Obsidian CLI IPC can time out on long notes.

### Visual and Infographic Knowledge Ingestion

When the source input is an image, infographic, or slide deck:

1. **Extract complete data points first:** Transcribe exact metrics, percentages, salary bands, dates, sector trends, and source attributions into markdown tables before drawing conclusions.
2. **Distinguish claims from verified data:** Third-party graphics frequently cite secondary reports. Include a `## Verification Status` section stating whether original publications were checked or if data reflects the infographic's self-reported figures.
3. **Analyze mechanisms, not just data points:** Connect observed statistics to underlying causal drivers (e.g., task substitution vs complementarity, entry-level career compression, margin pressure).
4. **Link to relevant domains:** Connect labor, behavioral economics, or agent trends to active vault areas (`30_Area/`, `31_Technical_Area/`). After a direct filesystem write to an already open note, `obsidian read` may briefly return the cached old content; run `obsidian open path="..."` and read again, then compare with the on-disk file before concluding the edit failed.

Default article note structure:

    # Article Title

    ## Source Context

    ## Core Thesis

    ## Mechanism

    ## Strategic Implication

    ## Technical / Operational Implication

    ## Behavioral Economics Angle

    ## Weak Assumptions

    ## Links Into Vault

    ## Tags

## Workflow Creation Rules

Create workflow notes in `60_Workflows/`.

Workflow notes should use:

    # Workflow Name

    ## Purpose

    ## Trigger

    ## Inputs

    ## Process

    ## Outputs

    ## Tools

    ## Failure Modes

    ## Review Cadence

    ## Related Notes

## Prompt Creation Rules

Create prompt notes in `70_Prompts/`.

Prompt notes should use:

    # Prompt Name

    ## Use Case

    ## Prompt

    ## Variables

    ## Expected Output

    ## Failure Modes

    ## Related Workflows

## Template Creation Rules

Create template notes in `80_Templates/`.

Template notes should be reusable and generic.

Do not mix templates with actual project content.

## Reporting Format

After every Obsidian operation, report:

- resolved vault path
- whether Obsidian CLI was available
- source article used, if applicable
- commands run
- files read
- output file created, if applicable
- files modified
- files skipped for safety
- recommended next action

## Failure Handling

If Obsidian CLI fails:

1. Check whether Obsidian app is installed and running.
2. Check whether CLI is enabled in Obsidian settings.
3. Check:

       command -v obsidian
       ls -l /usr/local/bin/obsidian

4. On macOS, suggest:

       sudo ln -sf /Applications/Obsidian.app/Contents/MacOS/obsidian-cli /usr/local/bin/obsidian

If the vault path fails:

1. Check:

       ls -ld "/Users/klao-pro/Documents/sundayhalfob"

2. Ask Klao whether the vault was moved.
3. Do not guess another vault path.
