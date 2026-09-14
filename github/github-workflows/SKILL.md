---
name: github-workflows
description: "Operate GitHub issues, pull requests, CI, and releases."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [github, git, gh, pull-requests, issues, code-review, ci]
    related_skills: [autonomous-coding-agents, requesting-code-review]
---

# GitHub Workflows

## Overview

This umbrella covers the GitHub operating class: authenticate, inspect a repository, manage issues, create/review PRs, monitor CI, merge safely, and fall back to REST/GraphQL when `gh` is unavailable. Prefer `gh` for ergonomics, but always know the `git` + API fallback.

## When to Use

- Cloning, creating, forking, configuring, or releasing GitHub repositories.
- Checking or fixing GitHub authentication.
- Creating, triaging, labeling, or closing issues.
- Branching, committing, opening, monitoring, and merging PRs.
- Reviewing PR diffs and posting review comments.
- Inspecting codebase size/language composition before planning work.

## Authentication and Repo Context

```bash
gh auth status
REMOTE_URL=$(git remote get-url origin)
OWNER_REPO=$(printf '%s\n' "$REMOTE_URL" | sed -E 's|.*github\.com[:/]||; s|\.git$||')
OWNER=${OWNER_REPO%%/*}; REPO=${OWNER_REPO#*/}
```

If `gh` is missing or unauthenticated, use `GITHUB_TOKEN` from the environment, Hermes env, or git credentials only if already configured. Never ask the user to paste a token into chat.

## Repository Management

- Clone/fork/create with `gh repo clone`, `gh repo fork`, `gh repo create` when available.
- Inspect remotes and default branch before making changes.
- For releases, verify tags and generated artifacts before publishing.

## Codebase Inspection

Use lightweight metrics before planning large changes:

```bash
pygount --format=summary .
git ls-files | wc -l
```

Summarize languages, generated/vendor directories, test locations, and likely risk areas.

## Issues

```bash
gh issue list --state open
gh issue create --title "..." --body "..." --label bug
gh issue edit 123 --add-label triage --assign @me
gh issue close 123 --comment "Fixed in #456"
```

Use structured bodies for bugs/features: summary, reproduction, expected/actual, context, acceptance criteria.

## Pull Request Lifecycle

```bash
git fetch origin
git checkout main && git pull origin main
git checkout -b feat/short-description
# edit files, test
git add <paths>
git commit -m "feat: short description"
git push -u origin HEAD
gh pr create --title "feat: short description" --body-file /tmp/pr.md
gh pr checks --watch
gh pr merge --squash --delete-branch
```

Fallbacks: create PRs with `POST /repos/{owner}/{repo}/pulls`, comments with `POST /issues/{number}/comments`, and merge with `PUT /pulls/{number}/merge`.

## Code Review

Review in this order:

1. Understand intent: PR description, linked issues, changed files.
2. Inspect diff with context (`gh pr diff`, `git diff base...head`).
3. Check correctness, security, tests, backwards compatibility, and maintainability.
4. Leave concise actionable comments; distinguish blockers from nits.
5. Verify line positions before posting inline comments.

## CI Troubleshooting Loop

1. `gh pr checks` or list runs by branch.
2. Read failed logs (`gh run view <id> --log-failed`).
3. Patch the root cause, commit, push.
4. Re-watch checks.
5. Repeat a bounded number of times; report blockers honestly.

## Common Pitfalls

1. **Assuming `gh` exists/authenticates.** Detect first and switch to API fallback.
2. **Dirty worktree before branch work.** Check `git status` and preserve user changes.
3. **Posting unverified review comments.** Confirm paths/lines against the current diff.
4. **Forgetting CI after push.** A PR is not complete until checks are known or blockers stated.
5. **Leaking credentials.** Tokens stay in env/config, never in messages or committed files.

## Verification Checklist

- [ ] Correct owner/repo and branch confirmed.
- [ ] Authentication path verified (`gh` or token fallback).
- [ ] Local changes/tests/CI status checked as relevant.
- [ ] Any issue/PR/comment/release side effect has a verified URL or ID.
