# Hermes Agent Skills Catalog

Welcome to the **Hermes Skills Catalog**. This directory contains the operational skills, procedures, domain workflows, and agent capabilities that extend the Hermes Agent runtime.

Skills provide structured, step-by-step guidance, decision rubrics, tool recipes, and specialized prompts enabling Hermes to perform complex engineering, automation, research, design, and operations autonomously and reliably.

---

## 📑 Table of Contents

1. [Skill Architecture & Conventions](#-skill-architecture--conventions)
2. [Workflow & Engineering Skills (Matt Pocock Suite)](#-workflow--engineering-skills)
3. [Software Development & Debugging](#-software-development--debugging)
4. [Autonomous AI & Multi-Agent Operations](#-autonomous-ai--multi-agent-operations)
5. [MLOps & AI Engineering](#-mlops--ai-engineering)
6. [OpenClaw & Firecrawl Web Scraping](#-openclaw--firecrawl-web-scraping)
7. [Productivity & Office Automation](#-productivity--office-automation)
8. [Creative, Design & Media](#-creative-design--media)
9. [DevOps, Systems & Infrastructure](#-devops-systems--infrastructure)
10. [Social Media, Communication & Email](#-social-media-communication--email)
11. [Desktop, Theming & UI](#-desktop-theming--ui)
12. [MCP (Model Context Protocol) & Tooling](#-mcp--tooling)
13. [Gaming & Leisure](#-gaming--leisure)
14. [Security & Red Teaming](#-security--red-teaming)
15. [How to Author a New Skill](#-how-to-author-a-new-skill)

---

## 🧩 Skill Architecture & Conventions

Every skill is packaged either as a directory containing a `SKILL.md` file (with YAML frontmatter) or as a symlink pointing to an upstream skill package:

```
skills/
├── category-name/
│   ├── DESCRIPTION.md           # Category overview & routing guide
│   └── specific-skill/
│       ├── SKILL.md             # Core skill instructions & frontmatter
│       └── scripts/             # Optional automation scripts & templates
└── alias-name -> target         # Symlink shortcut for top-level discovery
```

### Frontmatter Schema
```yaml
---
name: skill-name
description: Clear, concise summary of what this skill does and when to activate it.
---
```

---

## 🚀 Workflow & Engineering Skills

These skills (aliased at root from `.agents/skills/`) drive structured software design, specification, stress-testing, implementation, and review.

| Skill | Purpose | When to Use / Triggers |
|---|---|---|
| [`ask-matt`](file:///Users/klao-pro/.hermes/skills/ask-matt) | Router over engineering skills | When unsure which workflow or skill fits your current development situation. |
| [`to-spec`](file:///Users/klao-pro/.hermes/skills/to-spec) | Spec writer | Converts a conversation or feature idea into a formal spec and issues. |
| [`to-tickets`](file:///Users/klao-pro/.hermes/skills/to-tickets) | Task breakdown | Breaks a plan or specification down into dependency-aware tracer-bullet tickets. |
| [`wayfinder`](file:///Users/klao-pro/.hermes/skills/wayfinder) | Multi-session roadmapping | Maps multi-session work into discrete decision tickets until the route is clear. |
| [`grill-me`](file:///Users/klao-pro/.hermes/skills/grill-me) | Relentless plan interrogation | Stress-tests a proposal or design through an interactive interview before coding. |
| [`grill-with-docs`](file:///Users/klao-pro/.hermes/skills/grill-with-docs) | Interrogation with ADR generation | Conducts an in-depth interview to sharpen plans and creates ADRs and glossaries. |
| [`grilling`](file:///Users/klao-pro/.hermes/skills/grilling) | Idea stress-testing | Grills the user relentlessly on architectural decisions, assumptions, and edge cases. |
| [`wait-what`](file:///Users/klao-pro/.hermes/skills/wait-what) | Course-correction & reset | Pauses when an idea did not land properly and re-pitches the concept cleanly. |
| [`codebase-design`](file:///Users/klao-pro/.hermes/skills/codebase-design) | Deep module architecture | Designs deep module interfaces, abstractions, seams, and testable boundaries. |
| [`domain-modeling`](file:///Users/klao-pro/.hermes/skills/domain-modeling) | Ubiquitous language & models | Clarifies core domain concepts, entities, and domain boundaries. |
| [`improve-codebase-architecture`](file:///Users/klao-pro/.hermes/skills/improve-codebase-architecture) | Architecture refactoring audit | Scans codebase for deepening opportunities, generates visual reports, and guides refactoring. |
| [`prototype`](file:///Users/klao-pro/.hermes/skills/prototype) | Throwaway spike prototyping | Builds rapid, minimal prototypes to validate risky architectural or UX questions. |
| [`implement`](file:///Users/klao-pro/.hermes/skills/implement) | Spec-driven code execution | Implements features systematically from an approved spec or ticket list. |
| [`tdd`](file:///Users/klao-pro/.hermes/skills/tdd) | Test-driven development | Enforces red-green-refactor cycles when writing unit/integration tests first. |
| [`code-review`](file:///Users/klao-pro/.hermes/skills/code-review) | Rigorous code reviews | Reviews PRs/changes against architectural specs and code standards. |
| [`diagnosing-bugs`](file:///Users/klao-pro/.hermes/skills/diagnosing-bugs) | Root cause investigation | Systematic diagnosis loop for complex bugs, regressions, and race conditions. |
| [`resolving-merge-conflicts`](file:///Users/klao-pro/.hermes/skills/resolving-merge-conflicts) | Git conflict reconciliation | Resolves in-progress git merge or rebase conflicts safely. |
| [`triage`](file:///Users/klao-pro/.hermes/skills/triage) | Issue & PR triage pipeline | Triages inbound bug reports and PRs through a structured verification state machine. |
| [`teach`](file:///Users/klao-pro/.hermes/skills/teach) | Interactive tutoring | Explains code concepts, architectures, and libraries interactively. |
| [`wizard`](file:///Users/klao-pro/.hermes/skills/wizard) | Step-by-step manual setup | Guides complex human-required setup, credential provisioning, or database cutovers. |
| [`handoff`](file:///Users/klao-pro/.hermes/skills/handoff) | Agent session handoffs | Compacts conversation context into a structured handoff document for another agent. |
| [`writing-for-agents`](file:///Users/klao-pro/.hermes/skills/writing-for-agents) | Agent doc authoring | Best practices for authoring `SKILL.md`, `AGENTS.md`, and system prompts. |
| [`workspace-dispatch`](file:///Users/klao-pro/.hermes/skills/workspace-dispatch) | Workspace routing | Dispatches tasks across multi-workspace Hermes setups. |

---

## 🛠️ Software Development & Debugging

Location: [`software-development/`](file:///Users/klao-pro/.hermes/skills/software-development)

| Skill | Path | Purpose |
|---|---|---|
| **software-development-lifecycle** | [`software-development/software-development-lifecycle/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/software-development-lifecycle/SKILL.md) | End-to-end SDLC orchestration from scope definition to test verification. |
| **subagent-driven-development** | [`software-development/subagent-driven-development/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/subagent-driven-development/SKILL.md) | Executes complex implementation plans using subagents with 2-stage verification. |
| **writing-plans** | [`software-development/writing-plans/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/writing-plans/SKILL.md) | Drafts bite-sized, file-specific technical plans before writing code. |
| **software-quality-workflows** | [`software-development/software-quality-workflows/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/software-quality-workflows/SKILL.md) | Runs dedicated QA passes, dogfooding checklists, and code simplification audits. |
| **debugger-tooling** | [`software-development/debugger-tooling/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/debugger-tooling/SKILL.md) | Attaches runtime debuggers (`debugpy`, `pdb`, Node.js inspector / Chrome DevTools). |
| **debugging-hermes-tui-commands** | [`software-development/debugging-hermes-tui-commands/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/debugging-hermes-tui-commands/SKILL.md) | Debugs Hermes TUI slash commands, Gateway WebSocket bridge, and Ink UI. |
| **inspecting-hermes-desktop-dom** | [`software-development/inspecting-hermes-desktop-dom/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/inspecting-hermes-desktop-dom/SKILL.md) | Connects via Chrome DevTools Protocol (CDP) to inspect and debug Hermes Desktop DOM/CSS. |
| **hermes-s6-container-supervision** | [`software-development/hermes-s6-container-supervision/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/hermes-s6-container-supervision/SKILL.md) | Modifies and debugs the `s6-overlay` process supervision tree in Hermes Docker images. |
| **steipete-coding-skill** | [`software-development/steipete-coding-skill/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/steipete-coding-skill/SKILL.md) | Coding style and conventions inspired by @steipete for rapid, clean execution. |
| **github** | [`software-development/github/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/github/SKILL.md) | Manages GitHub PRs, issues, code reviews, and repo operations via `gh` CLI. |

---

## 🤖 Autonomous AI & Multi-Agent Operations

Location: [`autonomous-ai-agents/`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents)

| Skill | Path | Purpose |
|---|---|---|
| **autonomous-coding-agents** | [`autonomous-ai-agents/autonomous-coding-agents/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/autonomous-coding-agents/SKILL.md) | Autonomous multi-step coding loops with self-correction and continuous verification. |
| **kanban-codex-lane** | [`autonomous-ai-agents/kanban-codex-lane/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/kanban-codex-lane/SKILL.md) | Automates Kanban task transitions, background worker dispatch, and lane syncing. |
| **antigravity-cli** | [`autonomous-ai-agents/antigravity-cli/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/antigravity-cli/SKILL.md) | Integrates with Google Antigravity CLI (`agy`) for multi-agent workflows. |
| **hermes-agent** | [`autonomous-ai-agents/hermes-agent/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/hermes-agent/SKILL.md) | Core internal agent protocols, dispatch mechanisms, and background worker spawning. |
| **merge-reconciler** | [`autonomous-ai-agents/merge-reconciler/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/merge-reconciler/SKILL.md) | Automated reconciliation and resolution of concurrent agent changes and git branches. |
| **computer-use** | [`autonomous-ai-agents/computer-use/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/computer-use/SKILL.md) | OS-level GUI automation via mouse/keyboard control and screenshot recognition. |

---

## 🧠 MLOps & AI Engineering

Location: [`mlops/`](file:///Users/klao-pro/.hermes/skills/mlops)

### 1. Fine-Tuning & Training (`mlops/training/`)
- [`axolotl`](file:///Users/klao-pro/.hermes/skills/mlops/training/axolotl/SKILL.md): Declarative YAML-based LLM fine-tuning supporting LoRA, QLoRA, DPO, and GRPO.
- [`unsloth`](file:///Users/klao-pro/.hermes/skills/mlops/training/unsloth/SKILL.md): Ultra-fast 2–5x accelerated LoRA/QLoRA training with reduced VRAM usage.
- [`peft-fine-tuning`](file:///Users/klao-pro/.hermes/skills/mlops/training/peft/SKILL.md): Parameter-efficient fine-tuning via HuggingFace PEFT (LoRA, Prefix Tuning, IA3).
- [`trl-fine-tuning`](file:///Users/klao-pro/.hermes/skills/mlops/training/trl-fine-tuning/SKILL.md): RLHF training using SFT, DPO, GRPO, and Reward Modeling.
- [`grpo-rl-training`](file:///Users/klao-pro/.hermes/skills/mlops/training/grpo-rl-training/SKILL.md): Group Relative Policy Optimization (GRPO) reinforcement learning for reasoning models.
- [`pytorch-fsdp`](file:///Users/klao-pro/.hermes/skills/mlops/training/pytorch-fsdp/SKILL.md): PyTorch Fully Sharded Data Parallel multi-GPU/multi-node training.

### 2. Inference & Structured Generation (`mlops/inference/`)
- [`guidance`](file:///Users/klao-pro/.hermes/skills/mlops/inference/guidance/SKILL.md): Guaranteed valid JSON, grammar constraints, and structured output formatting.
- [`outlines`](file:///Users/klao-pro/.hermes/skills/mlops/inference/outlines/SKILL.md): High-speed structured JSON, Pydantic, and regex-guided LLM sampling.
- [`gguf-quantization`](file:///Users/klao-pro/.hermes/skills/mlops/inference/gguf/SKILL.md): GGUF conversion and llama.cpp quantization for CPU/GPU deployment.
- [`obliteratus`](file:///Users/klao-pro/.hermes/skills/mlops/inference/obliteratus/SKILL.md): LLM refusal abliteration via activation diff-in-means.

### 3. Models & Multimodal (`mlops/models/`)
- [`clip`](file:///Users/klao-pro/.hermes/skills/mlops/models/clip/SKILL.md): Zero-shot image classification and multimodal text-image embeddings.
- [`stable-diffusion-image-generation`](file:///Users/klao-pro/.hermes/skills/mlops/models/stable-diffusion/SKILL.md): Image generation and diffusion pipelines via Diffusers.
- [`whisper`](file:///Users/klao-pro/.hermes/skills/mlops/models/whisper/SKILL.md): Speech-to-text recognition, translation, and timestamps in 99 languages.

### 4. Operations, Research & Cloud
- [`mlops-model-operations`](file:///Users/klao-pro/.hermes/skills/mlops/mlops-model-operations/SKILL.md): Model lifecycle management, Hugging Face Hub operations, and serving.
- [`cron-model-evaluation`](file:///Users/klao-pro/.hermes/skills/mlops/cron-model-evaluation/SKILL.md): Automated benchmark evaluation of local models for cron tasks.
- [`dspy`](file:///Users/klao-pro/.hermes/skills/mlops/research/dspy/SKILL.md): Declarative LM programming and automatic prompt optimization.
- [`modal-serverless-gpu`](file:///Users/klao-pro/.hermes/skills/mlops/cloud/modal/SKILL.md): Serverless GPU cloud orchestration on Modal.

---

## 🕷️ OpenClaw & Firecrawl Web Scraping

Location: [`openclaw-imports/`](file:///Users/klao-pro/.hermes/skills/openclaw-imports)

Comprehensive suite for web crawling, AI web search, content extraction, and browser automation via Firecrawl.

| Skill | Path | Purpose |
|---|---|---|
| **firecrawl** | [`openclaw-imports/firecrawl/SKILL.md`](file:///Users/klao-pro/.hermes/skills/openclaw-imports/firecrawl/SKILL.md) | Central router for all Firecrawl scraping, crawling, search, and extraction tasks. |
| **firecrawl-agent** | [`openclaw-imports/firecrawl-agent/SKILL.md`](file:///Users/klao-pro/.hermes/skills/openclaw-imports/firecrawl-agent/SKILL.md) | Extracts complex structured schemas across multi-page web applications. |
| **firecrawl-scrape** | [`openclaw-imports/firecrawl-scrape/SKILL.md`](file:///Users/klao-pro/.hermes/skills/openclaw-imports/firecrawl-scrape/SKILL.md) | Clean markdown extraction from specific URLs. |
| **firecrawl-crawl** | [`openclaw-imports/firecrawl-crawl/SKILL.md`](file:///Users/klao-pro/.hermes/skills/openclaw-imports/firecrawl-crawl/SKILL.md) | Recursive deep crawling of full websites or documentation subtrees. |
| **firecrawl-search** | [`openclaw-imports/firecrawl-search/SKILL.md`](file:///Users/klao-pro/.hermes/skills/openclaw-imports/firecrawl-search/SKILL.md) | Web search that returns cleaned, LLM-ready markdown results. |
| **firecrawl-map** | [`openclaw-imports/firecrawl-map/SKILL.md`](file:///Users/klao-pro/.hermes/skills/openclaw-imports/firecrawl-map/SKILL.md) | Fast URL discovery and sitemap generation for a target domain. |
| **firecrawl-interact** | [`openclaw-imports/firecrawl-interact/SKILL.md`](file:///Users/klao-pro/.hermes/skills/openclaw-imports/firecrawl-interact/SKILL.md) | Performs clicks, form inputs, pagination, and auth logins on dynamic pages. |
| **firecrawl-download** | [`openclaw-imports/firecrawl-download/SKILL.md`](file:///Users/klao-pro/.hermes/skills/openclaw-imports/firecrawl-download/SKILL.md) | Downloads web pages and site sections to local files. |
| **firecrawl-build-*** | `openclaw-imports/firecrawl-build-*/SKILL.md` | Integration skills for embedding Firecrawl search/scrape/interact SDKs into codebases. |

---

## 📈 Productivity & Office Automation

Location: [`productivity/`](file:///Users/klao-pro/.hermes/skills/productivity)

| Skill | Path | Purpose |
|---|---|---|
| **docx** | [`productivity/docx/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/docx/SKILL.md) | Creates, edits, formats, templates, and parses Microsoft Word `.docx` documents. |
| **xlsx** | [`productivity/xlsx/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/xlsx/SKILL.md) | Reads, modifies, and generates Excel `.xlsx` spreadsheets and CSV data. |
| **pdf** | [`productivity/pdf/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/pdf/SKILL.md) | Handles PDF generation, OCR extraction, form filling, and page merging. |
| **linear** | [`productivity/linear/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/linear/SKILL.md) | Manages Linear projects, cycles, and issues via GraphQL API. |
| **box** | [`productivity/box/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/box/SKILL.md) | Manages Box cloud storage files, shared links, metadata, and folders. |
| **document-to-action-items** | [`productivity/document-to-action-items/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/document-to-action-items/SKILL.md) | Extracts actionable obligations, deadlines, and owners from documents. |
| **meeting-action-items** | [`productivity/meeting-action-items/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/meeting-action-items/SKILL.md) | Converts meeting transcripts and notes into structured decisions and action items. |
| **obsidian-vault-automation** | [`productivity/obsidian-vault-automation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/obsidian-vault-automation/SKILL.md) | Automates vault maintenance, daily notes, and note linking in Obsidian. |
| **obsidian-indexing-automation** | [`productivity/obsidian-indexing-automation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/obsidian-indexing-automation/SKILL.md) | Indexes, categorizes, and tags notes in Obsidian vaults. |
| **daily-story-memo** | [`productivity/daily-story-memo/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/daily-story-memo/SKILL.md) | Compiles daily Telegram/Hermes story memos and activity digests. |
| **periodic-story-synthesis** | [`productivity/periodic-story-synthesis/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/periodic-story-synthesis/SKILL.md) | Synthesizes weekly, monthly, and annual story memos into executive summaries. |
| **weekly-review-planning** | [`productivity/weekly-review-planning/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/weekly-review-planning/SKILL.md) | Conducts weekly productivity reviews, reviews stalled work, and plans the next sprint. |
| **diagmemo** | [`productivity/diagmemo/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/diagmemo/SKILL.md) | Saves and indexes Telegram diagnostic memos into Obsidian. |
| **session-librarian** | [`productivity/session-librarian/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/session-librarian/SKILL.md) | Indexes, searches, categorizes, and prunes Hermes agent session history. |
| **product-price-monitor** | [`productivity/product-price-monitor/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/product-price-monitor/SKILL.md) | Monitors e-commerce product or flight prices and triggers alerts. |
| **petdex** | [`productivity/petdex/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/petdex/SKILL.md) | Manages and customizes animated companion mascots in the Hermes TUI. |
| **tui-widgets** | [`productivity/tui-widgets/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/tui-widgets/SKILL.md) | Authors live dashboard widgets for the Hermes TUI dock. |
| **external-service-automation** | [`productivity/external-service-automation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/external-service-automation/SKILL.md) | Integrates and routes tasks across external APIs and webhook services. |

---

## 🎨 Creative, Design & Media

Location: [`creative/`](file:///Users/klao-pro/.hermes/skills/creative) & [`media/`](file:///Users/klao-pro/.hermes/skills/media)

| Skill | Path | Purpose |
|---|---|---|
| **creative-ideation** | [`creative/creative-ideation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/creative-ideation/SKILL.md) | Brainstorms novel creative concepts, brand narratives, and copy angles. |
| **web-design-prototyping** | [`creative/web-design-prototyping/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/web-design-prototyping/SKILL.md) | Prototypes modern, responsive, and visually stunning web interfaces. |
| **comfyui** | [`creative/comfyui/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/comfyui/SKILL.md) | Generates and edits ComfyUI node workflows for diffusion models. |
| **creative-coding-motion** | [`creative/creative-coding-motion/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/creative-coding-motion/SKILL.md) | Authors motion graphics, canvas animations, and generative visual art. |
| **baoyu-comic** | [`creative/baoyu-comic/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/baoyu-comic/SKILL.md) | Creates comic strips and storyboard layouts from textual narratives. |
| **baoyu-article-illustrator** | [`creative/baoyu-article-illustrator/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/baoyu-article-illustrator/SKILL.md) | Generates editorial illustrations and infographic covers for articles. |
| **pixel-art** | [`creative/pixel-art/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/pixel-art/SKILL.md) | Creates pixel art sprites, color palettes, and tile assets. |
| **creative-media-production** | [`creative/creative-media-production/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/creative-media-production/SKILL.md) | End-to-end media production workflows (scripting, video editing, audio). |
| **spotify** | [`media/spotify/SKILL.md`](file:///Users/klao-pro/.hermes/skills/media/spotify/SKILL.md) | Interacts with Spotify API for playlist management and playback control. |
| **audio-music-production** | [`media/audio-music-production/SKILL.md`](file:///Users/klao-pro/.hermes/skills/media/audio-music-production/SKILL.md) | Audio processing, MIDI generation, synth sound design, and mastering. |

---

## ⚡ DevOps, Systems & Infrastructure

| Skill | Path | Purpose |
|---|---|---|
| **cronjob-operations** | [`devops/cronjob-operations/SKILL.md`](file:///Users/klao-pro/.hermes/skills/devops/cronjob-operations/SKILL.md) | Configures, manages, and troubleshoots Hermes recurring cron jobs. |
| **webhook-subscriptions** | [`devops/webhook-subscriptions/SKILL.md`](file:///Users/klao-pro/.hermes/skills/devops/webhook-subscriptions/SKILL.md) | Sets up and tests inbound/outbound webhook event receivers. |
| **sdlc-review** | [`devops/sdlc-review/SKILL.md`](file:///Users/klao-pro/.hermes/skills/devops/sdlc-review/SKILL.md) | Evaluates CI/CD pipeline health and release automation. |
| **apple-automation** | [`apple/apple-automation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/apple/apple-automation/SKILL.md) | Automates macOS workflows via AppleScript, JXA, Shortcuts, and native apps. |
| **obsidian_cli** | [`obsidian_cli/SKILL.md`](file:///Users/klao-pro/.hermes/skills/obsidian_cli/SKILL.md) | Direct CLI control and querying of local Obsidian vault instances. |
| **workout-memory** | [`workout-memory/SKILL.md`](file:///Users/klao-pro/.hermes/skills/workout-memory/SKILL.md) | Logs fitness workouts, tracking progressive overload and routine history. |

---

## 🌐 Social Media, Communication & Email

| Skill | Path | Purpose |
|---|---|---|
| **reddit-reading** | [`social-media/reddit-reading/SKILL.md`](file:///Users/klao-pro/.hermes/skills/social-media/reddit-reading/SKILL.md) | Reads subreddits, posts, threads, and comments without requiring a browser. |
| **xitter** | [`social-media/xitter/SKILL.md`](file:///Users/klao-pro/.hermes/skills/social-media/xitter/SKILL.md) | Operates X/Twitter timelines, drafting posts, reading mentions, and direct messages. |
| **email-inbox-triage** | [`email/email-inbox-triage/SKILL.md`](file:///Users/klao-pro/.hermes/skills/email/email-inbox-triage/SKILL.md) | Categorizes incoming emails, drafts replies, and extracts high-priority action items. |

---

## 🖥️ Desktop, Theming & UI

| Skill | Path | Purpose |
|---|---|---|
| **hermes-desktop-plugins** | [`hermes-desktop-plugins/SKILL.md`](file:///Users/klao-pro/.hermes/skills/hermes-desktop-plugins/SKILL.md) | Develops, tests, and packages JavaScript plugins for the Hermes Desktop client. |
| **hermes-themes** | [`hermes-themes/SKILL.md`](file:///Users/klao-pro/.hermes/skills/hermes-themes/SKILL.md) | Authors and customizes YAML UI themes/skins for the Hermes TUI and Desktop apps. |

---

## 🔌 MCP & Tooling

Location: [`mcp/`](file:///Users/klao-pro/.hermes/skills/mcp)

| Skill | Path | Purpose |
|---|---|---|
| **mcporter** | [`mcp/mcporter/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mcp/mcporter/SKILL.md) | Discovers, inspects, and ports Model Context Protocol (MCP) servers. |
| **native-mcp** | [`mcp/native-mcp/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mcp/native-mcp/SKILL.md) | Configures and tests native MCP server connections for Hermes. |

---

## 🎮 Gaming & Leisure

| Skill | Path | Purpose |
|---|---|---|
| **minecraft-modpack-server** | [`gaming/minecraft-modpack-server/SKILL.md`](file:///Users/klao-pro/.hermes/skills/gaming/minecraft-modpack-server/SKILL.md) | Provisions, configures, and manages Minecraft modded server instances. |
| **pokemon-player** | [`gaming/pokemon-player/SKILL.md`](file:///Users/klao-pro/.hermes/skills/gaming/pokemon-player/SKILL.md) | Plays and strategizes Game Boy / emulator Pokémon game runs. |
| **find-nearby** | [`leisure/find-nearby/SKILL.md`](file:///Users/klao-pro/.hermes/skills/leisure/find-nearby/SKILL.md) | Discovers local spots, restaurants, events, and points of interest. |

---

## 🛡️ Security & Red Teaming

| Skill | Path | Purpose |
|---|---|---|
| **godmode** | [`red-teaming/godmode/SKILL.md`](file:///Users/klao-pro/.hermes/skills/red-teaming/godmode/SKILL.md) | LLM red-teaming, jailbreak research, and adversarial safety evaluations. |

---

## 📝 How to Author a New Skill

To add a new capability to Hermes:

1. **Create Directory**:
   ```bash
   mkdir -p skills/category-name/skill-name
   ```
2. **Create `SKILL.md`**:
   Add YAML frontmatter with `name` and `description`:
   ```markdown
   ---
   name: my-new-skill
   description: Explains what this skill does and the exact scenarios when Hermes should use it.
   ---

   # My New Skill

   ## Overview
   Detailed background.

   ## When to Use
   - Condition 1
   - Condition 2

   ## Workflow Steps
   1. Step 1...
   2. Step 2...
   ```
3. **Add to `.gitignore`**:
   Ensure any API keys, credentials, or local test logs generated in the skill folder are ignored via [`.gitignore`](file:///Users/klao-pro/.hermes/skills/.gitignore).
