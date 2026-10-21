# Hermes Agent Skills Catalog

Welcome to the **Hermes Skills Catalog**. This directory contains the operational skills, procedures, domain workflows, and agent capabilities that extend the Hermes Agent runtime.

Skills provide structured, step-by-step guidance, decision rubrics, tool recipes, and specialized prompts enabling Hermes to perform complex engineering, automation, research, design, and operations autonomously and reliably.

---

## 📑 Table of Contents

1. [Skill Architecture & Conventions](#-skill-architecture--conventions)
2. [Workflow & Engineering Skills (Matt Pocock Suite & System Routing)](#-workflow--engineering-skills)
3. [Pstack & Advanced Engineering Protocols](#-pstack--advanced-engineering-protocols)
4. [Core Engineering Principles](#-core-engineering-principles)
5. [Software Development, Debugging & GitHub](#-software-development-debugging--github)
6. [Autonomous AI & Multi-Agent Operations](#-autonomous-ai--multi-agent-operations)
7. [MLOps & AI Engineering](#-mlops--ai-engineering)
8. [Productivity & Office Automation](#-productivity--office-automation)
9. [Creative, Design & Media](#-creative-design--media)
10. [DevOps, Systems & Infrastructure](#-devops-systems--infrastructure)
11. [Social Media & Communication](#-social-media--communication)
12. [Desktop, Theming & UI](#-desktop-theming--ui)
13. [MCP (Model Context Protocol) & Tooling](#-mcp--tooling)
14. [Security & Red Teaming](#-security--red-teaming)
15. [Archived Skills (`.archive/`)](#-archived-skills)
16. [How to Author a New Skill](#-how-to-author-a-new-skill)

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

These skills (aliased at root from `.agents/skills/`) drive structured software design, specification, stress-testing, implementation, research, and review.

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **ask-matt** | [`ask-matt`](file:///Users/klao-pro/.hermes/skills/ask-matt) | Router over engineering skills | When unsure which workflow or skill fits your current development situation. |
| **find-skills** | [`find-skills`](file:///Users/klao-pro/.hermes/skills/find-skills) | Agent skill discovery | Discovers and installs skills from the open agent skills ecosystem when new capabilities are needed. |
| **research** | [`research`](file:///Users/klao-pro/.hermes/skills/research) | Primary source research | Investigates questions against primary sources and official documentation, saving cited findings. |
| **setup-matt-pocock-skills** | [`setup-matt-pocock-skills`](file:///Users/klao-pro/.hermes/skills/setup-matt-pocock-skills) | Engineering workflow config | Scaffolds and configures per-repo settings assumed by bundled engineering workflows. |
| **to-spec** | [`to-spec`](file:///Users/klao-pro/.hermes/skills/to-spec) | Spec writer | Converts a conversation or feature idea into a formal spec and issues. |
| **to-tickets** | [`to-tickets`](file:///Users/klao-pro/.hermes/skills/to-tickets) | Task breakdown | Breaks a plan or specification down into dependency-aware tracer-bullet tickets. |
| **to-questionnaire** | [`to-questionnaire`](file:///Users/klao-pro/.hermes/skills/to-questionnaire) | Gap discovery questionnaire | Turns an incomplete decision into a structured questionnaire for external stakeholders. |
| **wayfinder** | [`wayfinder`](file:///Users/klao-pro/.hermes/skills/wayfinder) | Multi-session roadmapping | Maps multi-session work into discrete decision tickets until the route is clear. |
| **grill-me** | [`grill-me`](file:///Users/klao-pro/.hermes/skills/grill-me) | Relentless plan interrogation | Stress-tests a proposal or design through an interactive interview before coding. |
| **grill-with-docs** | [`grill-with-docs`](file:///Users/klao-pro/.hermes/skills/grill-with-docs) | Interrogation with ADR generation | Conducts an in-depth interview to sharpen plans and creates ADRs and glossaries. |
| **grilling** | [`grilling`](file:///Users/klao-pro/.hermes/skills/grilling) | Idea stress-testing | Grills the user relentlessly on architectural decisions, assumptions, and edge cases. |
| **wait-what** | [`wait-what`](file:///Users/klao-pro/.hermes/skills/wait-what) | Course-correction & reset | Pauses when an idea did not land properly and re-pitches the concept cleanly. |
| **codebase-design** | [`codebase-design`](file:///Users/klao-pro/.hermes/skills/codebase-design) | Deep module architecture | Designs deep module interfaces, abstractions, seams, and testable boundaries. |
| **domain-modeling** | [`domain-modeling`](file:///Users/klao-pro/.hermes/skills/domain-modeling) | Ubiquitous language & models | Clarifies core domain concepts, entities, and domain boundaries. |
| **improve-codebase-architecture** | [`improve-codebase-architecture`](file:///Users/klao-pro/.hermes/skills/improve-codebase-architecture) | Architecture refactoring audit | Scans codebase for deepening opportunities, generates visual reports, and guides refactoring. |
| **prototype** | [`prototype`](file:///Users/klao-pro/.hermes/skills/prototype) | Throwaway spike prototyping | Builds rapid, minimal prototypes to validate risky architectural or UX questions. |
| **implement** | [`implement`](file:///Users/klao-pro/.hermes/skills/implement) | Spec-driven code execution | Implements features systematically from an approved spec or ticket list. |
| **tdd** | [`tdd`](file:///Users/klao-pro/.hermes/skills/tdd) | Test-driven development | Enforces red-green-refactor cycles when writing unit/integration tests first. |
| **code-review** | [`code-review`](file:///Users/klao-pro/.hermes/skills/code-review) | Rigorous code reviews | Reviews PRs/changes against architectural specs and code standards. |
| **diagnosing-bugs** | [`diagnosing-bugs`](file:///Users/klao-pro/.hermes/skills/diagnosing-bugs) | Root cause investigation | Systematic diagnosis loop for complex bugs, regressions, and race conditions. |
| **resolving-merge-conflicts** | [`resolving-merge-conflicts`](file:///Users/klao-pro/.hermes/skills/resolving-merge-conflicts) | Git conflict reconciliation | Resolves in-progress git merge or rebase conflicts safely. |
| **triage** | [`triage`](file:///Users/klao-pro/.hermes/skills/triage) | Issue & PR triage pipeline | Triages inbound bug reports and PRs through a structured verification state machine. |
| **teach** | [`teach`](file:///Users/klao-pro/.hermes/skills/teach) | Interactive tutoring | Explains code concepts, architectures, and libraries interactively. |
| **wizard** | [`wizard`](file:///Users/klao-pro/.hermes/skills/wizard) | Step-by-step manual setup | Guides complex human-required setup, credential provisioning, or database cutovers. |
| **handoff** | [`handoff`](file:///Users/klao-pro/.hermes/skills/handoff) | Agent session handoffs | Compacts conversation context into a structured handoff document for another agent. |
| **writing-for-agents** | [`writing-for-agents`](file:///Users/klao-pro/.hermes/skills/writing-for-agents) | Agent doc authoring | Best practices for authoring SKILL.md, AGENTS.md, and system prompts. |
| **workspace-dispatch** | [`workspace-dispatch`](file:///Users/klao-pro/.hermes/skills/workspace-dispatch) | Workspace routing | Dispatches tasks across multi-workspace Hermes setups. |

---

## ⚡ Pstack & Advanced Engineering Protocols

Advanced collaborative agent modes, multi-candidate tournament execution, adversarial review, and verification protocols.

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **poteto-mode** | [`poteto-mode/SKILL.md`](file:///Users/klao-pro/.hermes/skills/poteto-mode/SKILL.md) | Poteto agent style for concise, detailed responses, deliberate subagents, and verified work. | Use for /poteto-mode, 'poteto', or requests to work in this style. |
| **poteto-help** | [`poteto-help/SKILL.md`](file:///Users/klao-pro/.hermes/skills/poteto-help/SKILL.md) | Interactive guidance for pstack setup, /poteto-mode, and picking the right skill/principle. | Use for /poteto-help or questions on navigating pstack. |
| **setup-pstack** | [`setup-pstack/SKILL.md`](file:///Users/klao-pro/.hermes/skills/setup-pstack/SKILL.md) | Configures models per role and reasoning budget for pstack workflows. | Use for /setup-pstack, 'configure pstack models', or tuning model budgets. |
| **arena** | [`arena/SKILL.md`](file:///Users/klao-pro/.hermes/skills/arena/SKILL.md) | Spawns N parallel candidates at the same task, picks a base, and grafts the strongest parts. | Use for /arena, 'arena this', or when one attempt at a non-trivial artifact is not enough. |
| **swarm** | [`swarm/SKILL.md`](file:///Users/klao-pro/.hermes/skills/swarm/SKILL.md) | Fans out N parallel workers, drains them, and returns a unified report. | Use for /swarm, 'swarm this', or parallel coverage, races, and gauntlets. |
| **figure-it-out** | [`figure-it-out/SKILL.md`](file:///Users/klao-pro/.hermes/skills/figure-it-out/SKILL.md) | Designs an auditable playbook when no narrower one fits (large migrations, ambitious changes). | Use for /figure-it-out or 'figure it out'. |
| **show-me-your-work** | [`show-me-your-work/SKILL.md`](file:///Users/klao-pro/.hermes/skills/show-me-your-work/SKILL.md) | Maintains an auditable TSV decision log for long-running or autonomous runs. | Use for /show-me-your-work, autonomous runs, or reviewable decision trails. |
| **recall** | [`recall/SKILL.md`](file:///Users/klao-pro/.hermes/skills/recall/SKILL.md) | Reconstructs recent working context from chat history, live state, and shared records. | Use for 'recall my work on X', 'catch me up', or 'where did I leave off'. |
| **reflect** | [`reflect/SKILL.md`](file:///Users/klao-pro/.hermes/skills/reflect/SKILL.md) | Spawns 3 parallel review subagents over active transcript to extract learnings and edits. | Use when the user invokes /reflect or asks to extract session learnings. |
| **automate-me** | [`automate-me/SKILL.md`](file:///Users/klao-pro/.hermes/skills/automate-me/SKILL.md) | Turns working preferences, repeated workflows, or styles into custom agent modes. | Use for 'automate me', 'create my -mode skill', or capturing custom working style. |
| **architect** | [`architect/SKILL.md`](file:///Users/klao-pro/.hermes/skills/architect/SKILL.md) | Sketches types, signatures, and module structure before code, keeping human in the loop. | Use for /architect, 'architect this', or before non-trivial implementation jumps. |
| **interrogate** | [`interrogate/SKILL.md`](file:///Users/klao-pro/.hermes/skills/interrogate/SKILL.md) | Multi-model adversarial review to challenge code assumptions and stress-test designs. | Use for 'interrogate', 'adversarial review', 'challenge this', or /interrogate. |
| **correct** | [`correct/SKILL.md`](file:///Users/klao-pro/.hermes/skills/correct/SKILL.md) | Finds recurring agent mistakes in the repo and makes them structurally impossible. | Use for /correct or eliminating repeat agent footguns. |
| **blast-radius** | [`blast-radius/SKILL.md`](file:///Users/klao-pro/.hermes/skills/blast-radius/SKILL.md) | Finds what a change could break elsewhere before it ships, proving safety. | Use for 'blast radius of X', 'what could this break', or auditing risky diffs. |
| **create-verification-skill** | [`create-verification-skill/SKILL.md`](file:///Users/klao-pro/.hermes/skills/create-verification-skill/SKILL.md) | Generates a project-local verification skill driving the app like a real user. | Use for /create-verification-skill or scaffolding repo test harnesses. |
| **maintain-verification-skill** | [`maintain-verification-skill/SKILL.md`](file:///Users/klao-pro/.hermes/skills/maintain-verification-skill/SKILL.md) | Audits and refreshes project verification skills and feature coverage maps. | Use for /maintain-verification-skill or 'audit the verify skill'. |
| **benchmark-checklist** | [`benchmark-checklist/SKILL.md`](file:///Users/klao-pro/.hermes/skills/benchmark-checklist/SKILL.md) | Vets benchmark rigor, tuning limits, repeatability, and relevance before trusting perf data. | Use when running benchmarks or reporting speedups/regressions. |
| **how** | [`how/SKILL.md`](file:///Users/klao-pro/.hermes/skills/how/SKILL.md) | Walks through code architecture, ownership, and layering before making changes. | Use for 'how does X work', code walkthroughs, or architectural placement queries. |
| **why** | [`why/SKILL.md`](file:///Users/klao-pro/.hermes/skills/why/SKILL.md) | Uncovers design rationale, past trade-offs, regressions, postmortems, or thresholds. | Use for 'why does X work this way', 'why did we pick Y', or postmortems. |
| **no-comments** | [`no-comments/SKILL.md`](file:///Users/klao-pro/.hermes/skills/no-comments/SKILL.md) | Spawns Comment Sicko to prune useless comments and encode constraints in code/types. | Use for /no-comments or stripping AI comment clutter. |
| **bro** | [`bro/SKILL.md`](file:///Users/klao-pro/.hermes/skills/bro/SKILL.md) | Restates the last technical message in plain human language with no jargon. | Use for /bro or when complex technical explanations need radical simplification. |
| **ketchup** | [`ketchup/SKILL.md`](file:///Users/klao-pro/.hermes/skills/ketchup/SKILL.md) | Catches the user up on recent chat developments with plain text and concise visuals. | Use for /ketchup or summarizing missed progress. |
| **in-your-own-words** | [`in-your-own-words/SKILL.md`](file:///Users/klao-pro/.hermes/skills/in-your-own-words/SKILL.md) | Restates user goals and problem framing to verify mutual alignment before execution. | Use for /in-your-own-words to validate intent before heavy execution. |
| **technical-writing** | [`technical-writing/SKILL.md`](file:///Users/klao-pro/.hermes/skills/technical-writing/SKILL.md) | Authors high-clarity documentation adhering to Diataxis framework and Google style. | Use for /technical-writing, RFCs, READMEs, PR writeups, and documentation passes. |
| **unslop** | [`unslop/SKILL.md`](file:///Users/klao-pro/.hermes/skills/unslop/SKILL.md) | Cuts AI tells, filler buzzwords, and marketing fluff from writing. | Use for /unslop or polishing agent-generated prose. |

---

## 📐 Core Engineering Principles

A codified body of 24 software engineering principles applied during design, implementation, debugging, and refactoring.

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **principle-attack-the-premise** | [`principle-attack-the-premise/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-attack-the-premise/SKILL.md) | Identify and challenge the shared false assumption behind failing fixes. | Apply when two or more fixes that share one premise have failed the same gate. |
| **principle-boundary-discipline** | [`principle-boundary-discipline/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-boundary-discipline/SKILL.md) | Concentrate validation and error handling strictly at system boundaries. | Apply when wiring validation, error handling, or framework adapters at boundaries. |
| **principle-build-the-lever** | [`principle-build-the-lever/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-build-the-lever/SKILL.md) | Build the tool that performs or verifies non-trivial work instead of manual toil. | Apply to non-trivial edits, migrations, analyses, and checks to build leverage. |
| **principle-encode-lessons-in-structure** | [`principle-encode-lessons-in-structure/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-encode-lessons-in-structure/SKILL.md) | Encode recurring feedback into lint rules, types, or assertions. | Apply when catching yourself writing the same instruction or correction a second time. |
| **principle-exhaust-the-design-space** | [`principle-exhaust-the-design-space/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-exhaust-the-design-space/SKILL.md) | Build 2-3 competing minimal prototypes when facing novel UI/architectural problems. | Apply when facing novel UI interactions or architectures with no existing precedent. |
| **principle-experience-first** | [`principle-experience-first/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-experience-first/SKILL.md) | Prioritize user delight and interaction ergonomics over implementation convenience. | Apply when product, UX, or feature-scope trade-offs arise. |
| **principle-explain-the-number** | [`principle-explain-the-number/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-explain-the-number/SKILL.md) | Verify and mathematically reconcile performance numbers before reporting them. | Apply before trusting, reporting, or acting on measured speedups, throughputs, or latencies. |
| **principle-fix-root-causes** | [`principle-fix-root-causes/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-fix-root-causes/SKILL.md) | Trace defects to their point of origin and fix them permanently instead of patching symptoms. | Apply when debugging; trace symptom to where system first went wrong. |
| **principle-foundational-thinking** | [`principle-foundational-thinking/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-foundational-thinking/SKILL.md) | Model core data types and sequencing before writing business logic. | Apply before writing logic: choose core types, structures, and sequence scaffolding first. |
| **principle-guard-the-context-window** | [`principle-guard-the-context-window/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-guard-the-context-window/SKILL.md) | Protect LLM context by routing bulk data and exploration to subagents. | Apply when context fills up: large outputs, long files, repeated reads, or fan-out. |
| **principle-laziness-protocol** | [`principle-laziness-protocol/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-laziness-protocol/SKILL.md) | Bias toward small, direct diffs; avoid speculative abstractions and premature layers. | Apply when refactoring, evaluating diff size, or tempted to add abstractions. |
| **principle-make-operations-idempotent** | [`principle-make-operations-idempotent/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-make-operations-idempotent/SKILL.md) | Design processing loops, commands, and migrations to safely survive retries and restarts. | Apply when designing lifecycle steps, commands, or processing loops that retry. |
| **principle-migrate-callers-then-delete-legacy-apis** | [`principle-migrate-callers-then-delete-legacy-apis/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-migrate-callers-then-delete-legacy-apis/SKILL.md) | Migrate all callers to new internal APIs and delete the deprecated path in the same change. | Apply when introducing a new internal API while old callers still exist. |
| **principle-minimize-reader-load** | [`principle-minimize-reader-load/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-minimize-reader-load/SKILL.md) | Reduce cognitive load by eliminating indirection, hidden state, and excess layers. | Apply when reviewing or shaping complex code that is difficult to trace. |
| **principle-model-the-domain** | [`principle-model-the-domain/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-model-the-domain/SKILL.md) | Represent domain rules directly in explicit data structures rather than branching flags. | Apply when writing stateful logic or code branching on shape assumptions. |
| **principle-never-block-on-the-human** | [`principle-never-block-on-the-human/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-never-block-on-the-human/SKILL.md) | Execute reversible actions proactively without halting for unnecessary confirmations. | Apply when tempted to ask 'should I do X?' on low-risk or reversible work. |
| **principle-outcome-oriented-execution** | [`principle-outcome-oriented-execution/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-outcome-oriented-execution/SKILL.md) | Keep explicit phase boundaries during rewrites and converge cleanly on target architecture. | Apply during planned rewrites and migrations with explicit phase milestones. |
| **principle-prove-it-works** | [`principle-prove-it-works/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-prove-it-works/SKILL.md) | Demonstrate working proof via real execution artifacts before declaring completion. | Apply after completing any task, before declaring done; verify against live artifacts. |
| **principle-redesign-from-first-principles** | [`principle-redesign-from-first-principles/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-redesign-from-first-principles/SKILL.md) | Re-evaluate the entire design when integrating major requirements rather than bolting them on. | Apply when integrating a major new requirement into an existing architecture. |
| **principle-separate-before-serializing-shared-state** | [`principle-separate-before-serializing-shared-state/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-separate-before-serializing-shared-state/SKILL.md) | Eliminate shared mutable state between concurrent actors before applying locks/serialization. | Apply when concurrent actors write to the same file, branch, key, or shared state. |
| **principle-sequence-verifiable-units** | [`principle-sequence-verifiable-units/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-sequence-verifiable-units/SKILL.md) | Decompose work into small, independently testable commits and PRs. | Apply to multi-step work, migrations, sweeps, and PR/commit stacking. |
| **principle-subtract-before-you-add** | [`principle-subtract-before-you-add/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-subtract-before-you-add/SKILL.md) | Prune obsolete code, stubs, and redundant validators before adding new functionality. | Apply when sequencing additions, refactors, or feature rewrites. |
| **principle-test-behavior-not-implementation** | [`principle-test-behavior-not-implementation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-test-behavior-not-implementation/SKILL.md) | Assert observable public behavior so tests survive internal refactors. | Apply when writing, modifying, or reviewing test assertions. |
| **principle-type-system-discipline** | [`principle-type-system-discipline/SKILL.md`](file:///Users/klao-pro/.hermes/skills/principle-type-system-discipline/SKILL.md) | Make illegal states unrepresentable using strict type design. | Apply when designing types, function signatures, or data contracts in typed languages. |

---

## 🛠️ Software Development, Debugging & GitHub

Location: [`software-development/`](file:///Users/klao-pro/.hermes/skills/software-development) & [`github/`](file:///Users/klao-pro/.hermes/skills/github)

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **software-development-lifecycle** | [`software-development/software-development-lifecycle/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/software-development-lifecycle/SKILL.md) | End-to-end SDLC orchestration from scope definition to test verification. | Scope definition, implementation planning, architecture spikes, or complete SDLC execution. |
| **subagent-driven-development** | [`software-development/subagent-driven-development/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/subagent-driven-development/SKILL.md) | Executes complex implementation plans using subagents with 2-stage verification. | When you have an approved implementation plan and want subagents to execute task by task. |
| **writing-plans** | [`software-development/writing-plans/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/writing-plans/SKILL.md) | Drafts bite-sized, file-specific technical plans before writing code. | Before implementing multi-step features or non-trivial architectural changes. |
| **software-quality-workflows** | [`software-development/software-quality-workflows/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/software-quality-workflows/SKILL.md) | Runs dedicated QA passes, dogfooding checklists, and code simplification audits. | When asked to dogfood an app, run QA, review UX edge cases, or simplify complex code. |
| **debugger-tooling** | [`software-development/debugger-tooling/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/debugger-tooling/SKILL.md) | Attaches runtime debuggers (`debugpy`, `pdb`, Node.js inspector / Chrome DevTools). | When tests/processes fail and logs alone do not expose the corrupted state. |
| **debugging-hermes-tui-commands** | [`software-development/debugging-hermes-tui-commands/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/debugging-hermes-tui-commands/SKILL.md) | Debugs Hermes TUI slash commands, Gateway WebSocket bridge, and Ink UI. | When debugging slash commands across Python, Gateway, or Ink frontend. |
| **hermes-s6-container-supervision** | [`software-development/hermes-s6-container-supervision/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/hermes-s6-container-supervision/SKILL.md) | Modifies and debugs the `s6-overlay` process supervision tree in Hermes Docker images. | When adding, modifying, or debugging background services in Hermes containers. |
| **steipete-coding-skill** | [`software-development/steipete-coding-skill/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/steipete-coding-skill/SKILL.md) | Coding style and conventions inspired by @steipete for rapid, clean execution. | When working on projects following Peter Steinberger's swift/clean engineering patterns. |
| **github** | [`software-development/github/SKILL.md`](file:///Users/klao-pro/.hermes/skills/software-development/github/SKILL.md) | Consolidated GitHub CLI suite: PR lifecycle, issue delivery, code review, repos, and CI. | Operating GitHub via `gh` CLI: PR creation, review, issue checks, and repo administration. |
| **github-issue-to-pr** | [`github/github-issue-to-pr/SKILL.md`](file:///Users/klao-pro/.hermes/skills/github/github-issue-to-pr/SKILL.md) | Carries a GitHub issue all the way to a verified pull request with verified CI status. | Resolving GitHub issues from triage to PR creation and CI green status. |
| **github-workflows** | [`github/github-workflows/SKILL.md`](file:///Users/klao-pro/.hermes/skills/github/github-workflows/SKILL.md) | Operates GitHub issues, PR creation/management, CI tracking, and release management. | Cloning, forking, managing releases, or automating GitHub Actions CI. |

---

## 🤖 Autonomous AI & Multi-Agent Operations

Location: [`autonomous-ai-agents/`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents)

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **autonomous-coding-agents** | [`autonomous-ai-agents/autonomous-coding-agents/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/autonomous-coding-agents/SKILL.md) | Autonomous multi-step coding loops with self-correction and continuous verification. | Delegating software development to external coding agent CLIs. |
| **kanban-codex-lane** | [`autonomous-ai-agents/kanban-codex-lane/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/kanban-codex-lane/SKILL.md) | Automates Kanban task transitions, background worker dispatch, and lane syncing. | Running isolated coding tasks or refactors via the Hermes Kanban Codex lane. |
| **antigravity-cli** | [`autonomous-ai-agents/antigravity-cli/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/antigravity-cli/SKILL.md) | Integrates with Google Antigravity CLI (`agy`) for multi-agent workflows. | Installing, updating, driving, or debugging the Google Antigravity CLI. |
| **hermes-agent** | [`autonomous-ai-agents/hermes-agent/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/hermes-agent/SKILL.md) | Core internal agent protocols, dispatch mechanisms, and background worker spawning. | Extending Hermes agent runtime, configuring dispatch, or contributing to core. |
| **merge-reconciler** | [`autonomous-ai-agents/merge-reconciler/SKILL.md`](file:///Users/klao-pro/.hermes/skills/autonomous-ai-agents/merge-reconciler/SKILL.md) | Automated reconciliation and resolution of concurrent agent changes and git branches. | When concurrent agent worktrees or branches collide during multi-agent campaigns. |

---

## 🧠 MLOps & AI Engineering

Location: [`mlops/`](file:///Users/klao-pro/.hermes/skills/mlops)

### 1. Fine-Tuning & Training (`mlops/training/`)

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **axolotl** | [`mlops/training/axolotl/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/training/axolotl/SKILL.md) | Declarative YAML-based LLM fine-tuning supporting LoRA, QLoRA, DPO, and GRPO. | Working with Axolotl fine-tuning runs, datasets, or YAML configs. |
| **unsloth** | [`mlops/training/unsloth/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/training/unsloth/SKILL.md) | Ultra-fast 2–5x accelerated LoRA/QLoRA training with reduced VRAM usage. | Fine-tuning open-weights models (Llama, Mistral, Gemma) on single GPUs. |
| **peft-fine-tuning** | [`mlops/training/peft/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/training/peft/SKILL.md) | Parameter-efficient fine-tuning via HuggingFace PEFT (LoRA, Prefix Tuning, IA3). | Fine-tuning 7B-70B models on consumer/cloud GPUs with PEFT. |
| **trl-fine-tuning** | [`mlops/training/trl-fine-tuning/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/training/trl-fine-tuning/SKILL.md) | RLHF training using SFT, DPO, GRPO, and Reward Modeling. | Aligning models with human preference data via DPO, PPO, or SFT. |
| **grpo-rl-training** | [`mlops/training/grpo-rl-training/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/training/grpo-rl-training/SKILL.md) | Group Relative Policy Optimization (GRPO) reinforcement learning for reasoning models. | Enforcing strict reasoning chains, JSON/XML outputs, or task-specific RL without critic models. |
| **pytorch-fsdp** | [`mlops/training/pytorch-fsdp/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/training/pytorch-fsdp/SKILL.md) | PyTorch Fully Sharded Data Parallel multi-GPU/multi-node training. | Distributed training of large models across multiple GPUs or nodes. |

### 2. Inference & Structured Generation (`mlops/inference/`)

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **guidance** | [`mlops/inference/guidance/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/inference/guidance/SKILL.md) | Guaranteed valid JSON, grammar constraints, and structured output formatting. | Enforcing strict regex, CFGs, or schema constraints during LLM token sampling. |
| **outlines** | [`mlops/inference/outlines/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/inference/outlines/SKILL.md) | High-speed structured JSON, Pydantic, and regex-guided LLM sampling. | Constrained generation requiring Pydantic models or regular expression guidance. |
| **gguf-quantization** | [`mlops/inference/gguf/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/inference/gguf/SKILL.md) | GGUF conversion and llama.cpp quantization for CPU/GPU deployment. | Quantizing models for Apple Silicon, CPU inference, or Ollama/llama.cpp deployment. |
| **obliteratus** | [`mlops/inference/obliteratus/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/inference/obliteratus/SKILL.md) | LLM refusal abliteration via activation diff-in-means. | Abliterating refusal vectors or uncensoring open-weights LLMs for safety research. |

### 3. Models & Multimodal (`mlops/models/`)

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **clip** | [`mlops/models/clip/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/models/clip/SKILL.md) | Zero-shot image classification and multimodal text-image embeddings. | Zero-shot image classification, visual search, or computing multimodal similarity. |
| **stable-diffusion-image-generation** | [`mlops/models/stable-diffusion/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/models/stable-diffusion/SKILL.md) | Image generation and diffusion pipelines via HuggingFace Diffusers. | Generating images, SDXL/Flux pipelines, inpainting, or controlnet workflows. |
| **whisper** | [`mlops/models/whisper/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/models/whisper/SKILL.md) | Speech-to-text recognition, translation, and timestamps in 99 languages. | Transcribing audio/video files, generating subtitles, or multilingual speech translation. |

### 4. Operations, Research & Cloud

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **mlops-model-operations** | [`mlops/mlops-model-operations/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/mlops-model-operations/SKILL.md) | Model lifecycle management, Hugging Face Hub operations, and serving. | Uploading/downloading HF models, benchmarks, tracking via W&B, or serving via vLLM. |
| **cron-model-evaluation** | [`mlops/cron-model-evaluation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/cron-model-evaluation/SKILL.md) | Automated benchmark evaluation of local models for cron tasks. | Benchmarking and evaluating local models for automated cron operations. |
| **dspy** | [`mlops/research/dspy/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/research/dspy/SKILL.md) | Declarative LM programming and automatic prompt optimization. | Building multi-component LM pipelines, DSPy teleprompters, or self-optimizing prompts. |
| **modal-serverless-gpu** | [`mlops/cloud/modal/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mlops/cloud/modal/SKILL.md) | Serverless GPU cloud orchestration on Modal. | Deploying serverless GPU jobs, running containerized ML inference, or distributed fine-tuning. |

---

## 📈 Productivity & Office Automation

Location: [`productivity/`](file:///Users/klao-pro/.hermes/skills/productivity)

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **document-office-automation** | [`productivity/document-office-automation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/document-office-automation/SKILL.md) | Unified office suite: PDF/OCR extraction, edits, PowerPoint (`.pptx`) decks, and meeting artifact processing. | Processing PDFs, converting office documents, generating presentations, or OCR tasks. |
| **linear** | [`productivity/linear/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/linear/SKILL.md) | Manages Linear projects, cycles, and issues via GraphQL API. | Querying, creating, or updating Linear issues and projects. |
| **box** | [`productivity/box/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/box/SKILL.md) | Manages Box cloud storage files, shared links, metadata, and folders. | Managing, uploading, sharing, or searching enterprise files on Box. |
| **document-to-action-items** | [`productivity/document-to-action-items/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/document-to-action-items/SKILL.md) | Extracts actionable obligations, deadlines, and owners from documents. | Extracting contract terms, action items, or deliverables from lengthy docs. |
| **obsidian-vault-automation** | [`productivity/obsidian-vault-automation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/obsidian-vault-automation/SKILL.md) | Automates vault maintenance, daily notes, and note linking in Obsidian. | Maintaining daily notes, linking concepts, and automating vault health in Obsidian. |
| **obsidian-indexing-automation** | [`productivity/obsidian-indexing-automation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/obsidian-indexing-automation/SKILL.md) | Indexes, categorizes, and tags notes in Obsidian vaults. | Indexing untagged notes, building MOCs, or reorganizing Obsidian vault schemas. |
| **daily-story-memo** | [`productivity/daily-story-memo/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/daily-story-memo/SKILL.md) | Compiles daily Telegram/Hermes story memos and activity digests. | Scheduled or manual compilation of daily activity notes and message digests. |
| **periodic-story-synthesis** | [`productivity/periodic-story-synthesis/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/periodic-story-synthesis/SKILL.md) | Synthesizes weekly, monthly, and annual story memos into executive summaries. | Synthesizing weekly/monthly story notes into high-level retrospectives. |
| **diagmemo** | [`productivity/diagmemo/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/diagmemo/SKILL.md) | Saves and indexes Telegram diagnostic memos into Obsidian. | Capturing and saving technical diagnostic memos directly into Obsidian. |
| **session-librarian** | [`productivity/session-librarian/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/session-librarian/SKILL.md) | Indexes, searches, categorizes, and prunes Hermes agent session history. | Finding previous session decisions, renaming sessions, or pruning chat logs. |
| **product-price-monitor** | [`productivity/product-price-monitor/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/product-price-monitor/SKILL.md) | Monitors e-commerce product or flight prices and triggers alerts. | Tracking price changes on products, flights, or rental listings. |
| **petdex** | [`productivity/petdex/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/petdex/SKILL.md) | Manages and customizes animated companion mascots in the Hermes TUI. | Installing, configuring, or switching Hermes TUI petdex desktop mascots. |
| **tui-widgets** | [`productivity/tui-widgets/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/tui-widgets/SKILL.md) | Authors live dashboard widgets for the Hermes TUI dock. | Building custom TUI status panels, clocks, metrics, or financial tickers. |
| **external-service-automation** | [`productivity/external-service-automation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/productivity/external-service-automation/SKILL.md) | Integrates and routes tasks across external APIs and webhook services. | Interacting with external third-party SaaS APIs, webhooks, or cloud services. |

---

## 🎨 Creative, Design & Media

Location: [`creative/`](file:///Users/klao-pro/.hermes/skills/creative) & [`media/`](file:///Users/klao-pro/.hermes/skills/media)

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **creative-ideation** | [`creative/creative-ideation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/creative-ideation/SKILL.md) | Brainstorms novel creative concepts, brand narratives, and copy angles. | Open-ended ideation, brainstorming campaign concepts, naming, or storytelling angles. |
| **web-design-prototyping** | [`creative/web-design-prototyping/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/web-design-prototyping/SKILL.md) | Prototypes modern, responsive, and visually stunning web interfaces. | Designing HTML/CSS mockups, modern landing pages, components, and dashboard prototypes. |
| **comfyui** | [`creative/comfyui/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/comfyui/SKILL.md) | Generates and edits ComfyUI node workflows for diffusion models. | Constructing or executing ComfyUI JSON workflows for Flux, SDXL, or video models. |
| **creative-coding-motion** | [`creative/creative-coding-motion/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/creative-coding-motion/SKILL.md) | Authors motion graphics, canvas animations, and generative visual art. | Generative art, p5.js sketches, shaders, Manim animations, or canvas simulations. |
| **baoyu-comic** | [`creative/baoyu-comic/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/baoyu-comic/SKILL.md) | Creates comic strips and storyboard layouts from textual narratives. | Generating educational comic strips, manga panels, or graphic explanations. |
| **baoyu-article-illustrator** | [`creative/baoyu-article-illustrator/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/baoyu-article-illustrator/SKILL.md) | Generates editorial illustrations and infographic covers for articles. | Creating consistent cover art, infographic diagrams, or illustrations for technical articles. |
| **pixel-art** | [`creative/pixel-art/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/pixel-art/SKILL.md) | Creates pixel art sprites, color palettes, and tile assets. | Creating retro sprites, NES/PICO-8 palette conversions, or game assets. |
| **creative-media-production** | [`creative/creative-media-production/SKILL.md`](file:///Users/klao-pro/.hermes/skills/creative/creative-media-production/SKILL.md) | End-to-end media production workflows (scripting, video editing, audio). | Routing multi-step media production: scripts, audio cuts, video compilation, and diagrams. |
| **spotify** | [`media/spotify/SKILL.md`](file:///Users/klao-pro/.hermes/skills/media/spotify/SKILL.md) | Interacts with Spotify API for playlist management and playback control. | Controlling playback, queueing tracks, creating playlists, or searching music on Spotify. |
| **audio-music-production** | [`media/audio-music-production/SKILL.md`](file:///Users/klao-pro/.hermes/skills/media/audio-music-production/SKILL.md) | Audio processing, MIDI generation, synth sound design, and mastering. | Songwriting lyrics, AI music prompt crafting, MIDI composition, or audio mastering. |

---

## ⚡ DevOps, Systems & Infrastructure

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **cronjob-operations** | [`devops/cronjob-operations/SKILL.md`](file:///Users/klao-pro/.hermes/skills/devops/cronjob-operations/SKILL.md) | Configures, manages, and troubleshoots Hermes recurring cron jobs. | Managing, inspecting, creating, or fixing Hermes automated cron jobs. |
| **webhook-subscriptions** | [`devops/webhook-subscriptions/SKILL.md`](file:///Users/klao-pro/.hermes/skills/devops/webhook-subscriptions/SKILL.md) | Sets up and tests inbound/outbound webhook event receivers. | Configuring event-driven agent triggers or inbound webhook handlers. |
| **sdlc-review** | [`devops/sdlc-review/SKILL.md`](file:///Users/klao-pro/.hermes/skills/devops/sdlc-review/SKILL.md) | Evaluates CI/CD pipeline health and release automation. | Reviewing Kanban task handoffs and verifying CI release gates. |
| **apple-automation** | [`apple/apple-automation/SKILL.md`](file:///Users/klao-pro/.hermes/skills/apple/apple-automation/SKILL.md) | Automates macOS workflows via AppleScript, JXA, Shortcuts, and native apps. | Automating Apple Notes, Reminders, Calendar, Safari, or native macOS scripting. |
| **obsidian_cli** | [`obsidian_cli/SKILL.md`](file:///Users/klao-pro/.hermes/skills/obsidian_cli/SKILL.md) | Direct CLI control and querying of local Obsidian vault instances. | Executing local Obsidian vault queries and modifications via CLI. |
| **workout-memory** | [`workout-memory/SKILL.md`](file:///Users/klao-pro/.hermes/skills/workout-memory/SKILL.md) | Logs fitness workouts, tracking progressive overload and routine history. | Logging gym sets, tracking weights, or planning progressive overload workouts. |

---

## 🌐 Social Media & Communication

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **reddit-reading** | [`social-media/reddit-reading/SKILL.md`](file:///Users/klao-pro/.hermes/skills/social-media/reddit-reading/SKILL.md) | Reads subreddits, posts, threads, and comments without requiring a browser. | Reading subreddits, thread discussions, comments, or Reddit post analysis. |

> [!NOTE]
> `xitter` (formerly in `social-media/xitter/`) has been deprecated and retired from active dispatch.

---

## 🖥️ Desktop, Theming & UI

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **hermes-desktop-plugins** | [`hermes-desktop-plugins/SKILL.md`](file:///Users/klao-pro/.hermes/skills/hermes-desktop-plugins/SKILL.md) | Develops, tests, and packages JavaScript plugins for the Hermes Desktop client. | Developing custom desktop panes, statusbar widgets, or UI extensions. |
| **hermes-themes** | [`hermes-themes/SKILL.md`](file:///Users/klao-pro/.hermes/skills/hermes-themes/SKILL.md) | Authors and customizes YAML UI themes/skins for the Hermes TUI and Desktop apps. | Creating or editing custom color schemes, syntax highlighting, and themes for Hermes. |

---

## 🔌 MCP & Tooling

Location: [`mcp/`](file:///Users/klao-pro/.hermes/skills/mcp)

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **mcporter** | [`mcp/mcporter/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mcp/mcporter/SKILL.md) | Discovers, inspects, and ports Model Context Protocol (MCP) servers. | Using mcporter CLI to list, configure, auth, and call MCP tools directly. |
| **native-mcp** | [`mcp/native-mcp/SKILL.md`](file:///Users/klao-pro/.hermes/skills/mcp/native-mcp/SKILL.md) | Configures and tests native MCP server connections for Hermes. | Connecting Hermes to external MCP stdio or SSE servers and registering tools. |

---

## 🛡️ Security & Red Teaming

| Skill | Path | Purpose | Trigger |
|---|---|---|---|
| **godmode** | [`red-teaming/godmode/SKILL.md`](file:///Users/klao-pro/.hermes/skills/red-teaming/godmode/SKILL.md) | LLM red-teaming, jailbreak research, and adversarial safety evaluations. | Adversarial testing, jailbreak robustness checks, and safety evaluation prompts. |

---

## 📦 Archived Skills

Location: [`.archive/`](file:///Users/klao-pro/.hermes/skills/.archive)

Legacy or deprecated skills that were archived from active runtime dispatch are preserved in `.archive/` for reference and historical retrieval:

| Skill | Path | Archive Note | Trigger |
|---|---|---|---|
| **computer-use** | [`.archive/computer-use/SKILL.md`](file:///Users/klao-pro/.hermes/skills/.archive/computer-use/SKILL.md) | OS GUI mouse/keyboard automation via screenshot recognition. | Deprecated: use specialized CLIs or direct API automation. |
| **docx** | [`.archive/docx/SKILL.md`](file:///Users/klao-pro/.hermes/skills/.archive/docx/SKILL.md) | Microsoft Word document editing. | Superseded by `document-office-automation`. |
| **email-inbox-triage** | [`.archive/email-inbox-triage/SKILL.md`](file:///Users/klao-pro/.hermes/skills/.archive/email-inbox-triage/SKILL.md) | Email inbox triage and draft responses. | Archived: legacy email triage. |
| **inspecting-hermes-desktop-dom** | [`.archive/inspecting-hermes-desktop-dom/SKILL.md`](file:///Users/klao-pro/.hermes/skills/.archive/inspecting-hermes-desktop-dom/SKILL.md) | CDP DOM inspection for Hermes Desktop client. | Archived: internal desktop debugging. |
| **meeting-action-items** | [`.archive/meeting-action-items/SKILL.md`](file:///Users/klao-pro/.hermes/skills/.archive/meeting-action-items/SKILL.md) | Meeting action items extraction. | Superseded by `document-office-automation`. |
| **pdf** | [`.archive/pdf/SKILL.md`](file:///Users/klao-pro/.hermes/skills/.archive/pdf/SKILL.md) | PDF operations and OCR. | Superseded by `document-office-automation`. |
| **thananon-coding-skill** | [`.archive/thananon-coding-skill/SKILL.md`](file:///Users/klao-pro/.hermes/skills/.archive/thananon-coding-skill/SKILL.md) | Personalized coding style conventions. | Archived. |
| **weekly-review-planning** | [`.archive/weekly-review-planning/SKILL.md`](file:///Users/klao-pro/.hermes/skills/.archive/weekly-review-planning/SKILL.md) | Weekly productivity planning routines. | Archived: legacy productivity review. |
| **xlsx** | [`.archive/xlsx/SKILL.md`](file:///Users/klao-pro/.hermes/skills/.archive/xlsx/SKILL.md) | Excel spreadsheet manipulation. | Superseded by `document-office-automation`. |

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
