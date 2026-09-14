---
name: steipete-coding-skill
description: "GitHub profile skill from @steipete. Use it when the task would benefit from mimicking this developer's repo choices, coding style, and implementation techniques."
---

## What they tend to build

- Small, sharp tools that remove one painful workflow step: token tracking, summaries, clipboard cleanup, menu-bar dashboards, MCP bridges, local crawlers.
- Products that are **agent-friendly by default**: CLI-first, local-first, scriptable, and often exposed both as a GUI and a terminal tool.
- Tools that sit in the middle of existing ecosystems instead of replacing them: browser cookies, provider CLIs, local SQLite archives, launchd/systemd tasks, GitHub releases, Homebrew taps.
- Reusable infrastructure for their own ecosystem is normal: shared agent scripts, shared rules, shared helpers, shared release tooling.
- The naming is often playful, but the implementation goal is practical: “show limits,” “get the gist,” “flatten paste,” “capture screenshots,” “call MCPs,” “crawl into SQLite.”

## Coding patterns to mirror

- Prefer **thin, operational surfaces** over abstraction-heavy layers. Most repos ship a clear command, a focused UI, or a narrow API.
- Keep workflows explicit and scriptable:
  - dedicated `Scripts/`, `scripts/`, `bin/`, or `release/` folders
  - install/packaging commands in README and `Makefile`/package scripts
  - config commands for enabling/disabling providers or toggling features
- Favor **local state and portability**:
  - config files in standard locations
  - restrictive file permissions when storing secrets
  - browser/session reuse instead of password collection
  - local caches, SQLite archives, and filesystem-backed workflows
- Expect strong repo hygiene:
  - format/lint/typecheck/test configs at the root
  - release notes, changelog, and docs alongside code
  - CI-friendly scripts and cross-platform packaging
- For agent-facing repos, keep instructions **short, pointer-based, and validated** rather than duplicating large rule blocks.
- Tests and build commands are usually part of the public contract, not an afterthought.

## Product and UI taste

- Strong preference for **minimal UI with high information density**:
  - menu bar items, popovers, side panels, dashboards
  - “at a glance” status over deep navigation
  - no Dock icon / reduced chrome when the app’s job is monitoring or routing
- The UI should feel like a utility, not a platform:
  - immediate status
  - clear reset/countdown/cost indicators
  - one-action commands
  - defaults that work without setup
- Visual tone is clean and slightly witty, but not decorative for its own sake.
- Privacy and control are part of the product promise, so avoid dark-pattern setup flows or opaque background behavior.

## Tech stack clues

- **Swift/macOS** is a major lane:
  - SwiftPM packages, macOS apps, menu bar apps, widget extensions
  - SwiftUI where it fits, plus native app integrations
  - tooling for CLI + GUI coexistence
- **TypeScript/Node** is the other major lane:
  - ESM-first packages
  - `pnpm`, workspace layouts, CLI binaries, browser extensions, daemon clients
  - type-aware linting/formatting and strict build scripts
- Common supporting tools:
  - shell scripts for automation and release
  - `vitest` for tests
  - `oxlint` / `oxfmt` in TS repos
  - `swiftformat` / `swiftlint` in Swift repos
  - release plumbing for Homebrew, GitHub Releases, and sometimes AUR
- MCP, agents, and provider integrations recur often, so code should assume multiple auth modes and multiple backends.

## When to inspect repos first

- Before editing anything **release-related**: packaging, versioning, appcast, Homebrew formulas, signing/notarization, tarballs, or install docs.
- Before changing **agent instructions or skills**: the repo may rely on pointer-style `AGENTS.md`, front matter, or validation scripts.
- Before touching **build/config plumbing**: root scripts, formatters, linters, TypeScript build entrypoints, SwiftPM layout, and cross-platform targets vary by repo.
- Before implementing **provider/auth integrations**: these repos often support several fallback paths, and the preferred order matters.
- Before changing **UI behavior in macOS apps**: menu bar apps here are opinionated about icons, reset timing, visibility, and minimal chrome.
- When a repo has explicit docs for a subsystem, read those first; Peter’s repos tend to document the intended workflow directly in README/docs rather than leaving it implicit.

## Repo Map

- [steipete/speaking](https://github.com/steipete/speaking): Upcoming and past speaking engagements for Peter Steinberger @steipete (215 stars, topics: speaking, ai, schedule)
- [openclaw/Peekaboo](https://github.com/openclaw/Peekaboo): Peekaboo is a macOS CLI & optional MCP server that enables AI agents to capture screenshots of applications, or the entire system, with optional visual question answering through local or remote AI models. (4785 stars, Swift, topics: ai, macos, mcp, screenshots)
- [openclaw/mcporter](https://github.com/openclaw/mcporter): Call MCPs via TypeScript, masquerading as simple TypeScript API. Or package them as cli. (4697 stars, TypeScript, topics: cli, mcp, ts-api)
- [steipete/oracle](https://github.com/steipete/oracle): Ask the oracle when you're stuck. Invoke GPT-5 Pro with a custom context and files. (2991 stars, TypeScript, topics: agents, ai, gpt-5-pro, anthropic)
- [steipete/Trimmy](https://github.com/steipete/Trimmy): "Paste once, run once." — Trimmy flattens those multi-line shell snippets you copy so they actually paste and run. (718 stars, Swift, topics: swift, clipboard)
- [steipete/CodexBar](https://github.com/steipete/CodexBar): Show usage stats for OpenAI Codex and Claude Code, without having to login. (15361 stars, Swift, topics: ai, codex, swift, claude-code)
- [steipete/Aspects](https://github.com/steipete/Aspects): Delightful, simple library for aspect oriented programming in Objective-C and Swift. (8423 stars, Objective-C, topics: objectivec, aspects, objective-c, hooks)
- [steipete/summarize](https://github.com/steipete/summarize): Point at any URL/YouTube/Podcast or file. Get the gist. CLI and Chrome Extension. (6253 stars, TypeScript, topics: ai, cli, summarize, typescript)
- [steipete/agent-rules](https://github.com/steipete/agent-rules): Rules and Knowledge to work better with agents such as Claude Code or Cursor (5691 stars, Shell, topics: agent, claudecode, cursor, llms)
- [steipete/agent-scripts](https://github.com/steipete/agent-scripts): Scripts for agents, shared between my repositories. (5182 stars, Shell, topics: ai-agents)
- [steipete/PSTCollectionView](https://github.com/steipete/PSTCollectionView): Open Source, 100% API compatible replacement of UICollectionView for iOS4.3+ (2535 stars, Objective-C)
- [steipete/RepoBar](https://github.com/steipete/RepoBar): Show status of GitHub Repos right in your menu bar and terminal: CI, Issues, Pull Requests, Latest Release. (2100 stars, Swift, topics: github, macos, statistics)
- [steipete/PSStackedView](https://github.com/steipete/PSStackedView): open source implementation of Twitter/iPad stacked ui - done right. (1947 stars, Objective-C)
- [steipete/birdclaw](https://github.com/steipete/birdclaw): Stores all your tweets nicely claw-able for agents. (1309 stars, TypeScript)
- [steipete/claude-code-mcp](https://github.com/steipete/claude-code-mcp): Claude Code as one-shot MCP server to have an agent in your agent. (1305 stars, JavaScript, topics: agent, claude, mcp)
- [steipete/AFDownloadRequestOperation](https://github.com/steipete/AFDownloadRequestOperation): A progressive download operation for AFNetworking. (1050 stars, Objective-C)

## How To Use This Skill

- Reach for this skill when the user asks for Peter Steinberger's style, when the repo stack matches this person's ecosystem, or when studying their real code would reduce made-up output.
- Pick one or more relevant repositories from the list above based on the current task.
- Clone the most relevant repository or repositories into `/tmp` for temporary inspection.
- Study the implementation details, naming patterns, architecture, UI taste, and tooling choices there.
- Return to the main task and apply the useful patterns you observed instead of copying blindly.
- Treat the upstream repositories as reference material for style and technique, then adapt them to the current codebase responsibly.
