---
name: autonomous-coding-agents
description: "Delegate software work to external coding-agent CLIs."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [coding-agents, claude-code, codex, opencode, delegation, worktrees]
    related_skills: [hermes-agent, github-workflows]
---

# Autonomous Coding Agents

## Overview

This umbrella covers running external autonomous coding CLIs from Hermes. The class-level workflow is the same across Claude Code, Codex, and OpenCode: run inside a clean git repo/worktree, use a PTY for interactive CLIs, give a self-contained prompt, monitor long-running sessions, and verify resulting diffs/tests yourself before reporting success.

## When to Use

- Implementing features, refactors, test suites, or PR review drafts with a specialist coding agent.
- Running several independent issue fixes in parallel worktrees.
- Asking a second model/CLI to inspect code while Hermes orchestrates verification.
- Scratch prototyping, provided you initialize a temporary git repo if the CLI requires one.

Do not use for trivial file edits Hermes can perform directly, tasks requiring user secrets, or unverified claims about external side effects.

## Universal Workflow

1. Inspect the repo state (`git status`, branch, remotes) before delegation.
2. Create an isolated worktree/branch for each agent if there is any chance of conflict.
3. Run interactive CLIs with `pty=true`.
4. For long jobs, use `background=true` with `notify_on_complete=true`, then `process` to monitor.
5. After completion, verify with `git diff`, tests, linters, and/or manual review.
6. Commit only after verifying the change and preserving user constraints.

## CLI Profiles

### Claude Code

Best for large codebase edits, complex refactors, and implementation tasks where Claude's code reasoning is preferred. Keep prompts concrete: files, acceptance criteria, test commands, and explicit boundaries.

### Codex

Install with `npm install -g @openai/codex`. Codex requires a git repository; for scratch work use `mktemp -d && git init`. Use `codex exec "prompt"` for one-shots and `--full-auto` only when workspace-scoped auto-approval is safe.

```bash
codex exec 'Add dark mode toggle to settings'
codex exec --full-auto 'Refactor the auth module and run tests'
```

Codex auth may be via `OPENAI_API_KEY`, Codex OAuth under `~/.codex/auth.json`, or Hermes-managed OpenAI Codex auth for Hermes itself; do not equate a missing env var with missing auth.

### OpenCode

Use OpenCode when that CLI is installed/configured or when the task benefits from its model/provider setup. Treat it like the others: PTY, git repo, bounded prompt, independent verification.

## Parallel Worktrees

```bash
git worktree add -b fix/issue-78 /tmp/issue-78 main
git worktree add -b fix/issue-99 /tmp/issue-99 main
# launch one agent per worktree, then verify and PR separately
```

Avoid running two agents in the same worktree unless one is strictly read-only.

## PR Review Pattern

Clone or checkout the PR in a disposable directory, ask the agent for review notes, then independently inspect the diff before posting comments. Agent output is an advisory draft, not proof.

## Common Pitfalls

1. **No PTY for interactive CLIs.** Use `pty=true` or commands can hang.
2. **No git repo.** Some CLIs refuse to run outside git; initialize scratch repos.
3. **Believing self-reports.** Always verify files, tests, commits, PR URLs, and CI yourself.
4. **Unsafe auto-approval.** `--yolo`/broad auto modes can damage unrelated files; isolate in worktrees.
5. **Prompt under-specification.** Include acceptance criteria and test commands in the delegated prompt.

## Verification Checklist

- [ ] Work ran in the intended repo/worktree.
- [ ] Diff only contains intended changes.
- [ ] Tests/lints/builds ran or blockers are stated plainly.
- [ ] Any PR/comment/push side effect has a verified URL/status.
