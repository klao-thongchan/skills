---
name: software-development-lifecycle
description: "Guide implementation from scope through verification."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [software-development, planning, tdd, debugging, spikes, code-review]
    related_skills: [github-workflows, autonomous-coding-agents]
---

# Software Development Lifecycle

## Overview

This umbrella covers the class-level workflow for building reliable software with Hermes: plan only enough to act, validate uncertainty with spikes, use tests to drive behavior, debug from evidence, and review before committing or handing off. It replaces narrow phase-specific triggers with one lifecycle map.

## When to Use

- Turning a user request into an actionable implementation plan.
- Running a throwaway spike to validate a risky approach.
- Applying RED-GREEN-REFACTOR test-driven development.
- Debugging failures systematically before patching.
- Requesting or performing pre-commit code review.
- Coordinating implementation, verification, and handoff.

## Lifecycle Map

1. **Understand and scope.** Identify files, constraints, acceptance criteria, and risks.
2. **Plan.** Write bite-sized tasks only when the job is multi-step or needs coordination.
3. **Spike when uncertain.** Build disposable experiments to answer technical questions.
4. **TDD where practical.** Add or update failing tests before implementation.
5. **Implement.** Make focused changes with file tools, preserving user work.
6. **Debug from evidence.** Reproduce, instrument, isolate, fix, and prevent regressions.
7. **Review.** Check security, correctness, edge cases, maintainability, and docs.
8. **Verify and report.** Run real commands/tests; state exact blockers if any.

## Planning

Plans should name concrete files, commands, risks, and validation steps. Avoid plans that merely restate goals. For small tasks, act directly instead of over-planning.

## Spikes

Use spikes to validate unknown APIs, performance assumptions, data formats, or integration behavior. Keep them isolated and throw them away or explicitly promote only the proven parts.

## Test-Driven Development

Follow RED-GREEN-REFACTOR when behavior can be tested:

1. Write/adjust a failing test that captures the desired behavior.
2. Run it and confirm the expected failure.
3. Implement the smallest fix.
4. Run the targeted test, then broader suites.
5. Refactor while keeping tests green.

## Systematic Debugging

Do not patch before understanding the failure. Reproduce, collect logs/error messages, inspect relevant code paths, form hypotheses, and test one variable at a time. Add regression coverage when possible.

## Code Review

Before handoff, inspect diffs for secrets, unsafe shell/SQL, authz/authn mistakes, race conditions, test gaps, and accidental generated/vendor changes. Use external reviewers/agents as advisory only; verify their claims.

## Common Pitfalls

1. **Ending with a plan instead of a result.** If tools can build/verify, keep going.
2. **Skipping RED.** Without a failing test, you may not know the fix is meaningful.
3. **Shotgun debugging.** Multiple untested changes hide the root cause.
4. **No diff review.** Generated files, secrets, and broad refactors can sneak in.
5. **Fabricated verification.** Only report commands that actually ran.

## Verification Checklist

- [ ] Acceptance criteria mapped to tests/checks.
- [ ] Relevant commands actually ran, or blockers are explicit.
- [ ] Diff reviewed for correctness and safety.
- [ ] User-facing summary includes what changed and how it was verified.
