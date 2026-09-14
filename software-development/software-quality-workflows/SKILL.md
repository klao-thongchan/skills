---
name: software-quality-workflows
description: "Run explicit QA, dogfooding, or simplification reviews."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [software-quality, qa, dogfood, browser-testing, code-review, refactor, simplification, verification]
    related_skills: []
---

# Software Quality Workflows

## Overview

Use this umbrella for finding, documenting, and fixing quality problems in software. It covers two common lanes that used to live as separate skills: browser-based exploratory QA/dogfooding and parallel reviewer-driven code simplification.

The shared pattern is: define the surface, gather real evidence, classify issues, apply only justified fixes, and verify with tests or reproduction steps.

## When to Use

- The user asks to dogfood a web app, find bugs, test flows, or produce a QA report.
- The user asks to simplify recent code changes, review for reuse/quality/efficiency, or clean up after a feature.
- The task needs evidence-driven bug reports, screenshots/logs/console output, or reviewer-style engineering findings.

## Exploratory Web QA / Dogfooding

1. **Map the app:** identify primary flows, auth state, navigation, forms, error boundaries, responsive states, and integration points.
2. **Interact like a user:** use browser snapshots, clicks, typing, scrolling, and console/network checks. Do not rely only on DOM inspection.
3. **Capture evidence:** reproduction steps, expected vs actual behavior, screenshots when useful, console errors, URL/state, and severity.
4. **Classify issues:** functional bug, UX confusion, accessibility issue, performance problem, data loss risk, security/privacy concern, or test gap.
5. **Report concisely:** prioritize the highest-impact issues first and include enough detail for an engineer to reproduce.

## Code Simplification / Parallel Review

Use three focused review lenses rather than one broad pass:

- **Reuse reviewer:** finds duplicate logic, existing utilities not used, over-specialized abstractions, and dead compatibility layers.
- **Quality reviewer:** finds confusing control flow, missing error handling, brittle tests, naming problems, and maintainability risks.
- **Efficiency reviewer:** finds needless I/O, extra API calls, quadratic loops, large allocations, and slow tests/build steps.

Run reviewers in parallel with `delegate_task` when the codebase is large or the review would flood context. Aggregate findings, reject speculative changes, patch only the fixes worth applying, and run the relevant tests.

## Evidence Standards

- A bug report should include steps to reproduce and a current observation, not just a suspicion.
- A simplification should reduce complexity without changing behavior; verify with tests or targeted runtime checks.
- Do not apply style churn unless it removes a real maintenance burden.
- If a reviewer claim cannot be verified, label it as unverified or drop it.

## Verification Checklist

- [ ] QA issues include reproduction evidence and severity.
- [ ] Code fixes are backed by diffs and tests/commands.
- [ ] Browser console/network errors were checked for web apps.
- [ ] Final report separates confirmed issues from suggestions.
- [ ] No destructive or public side effects were performed without clear scope.
