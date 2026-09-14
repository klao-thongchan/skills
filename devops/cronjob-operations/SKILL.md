---
name: cronjob-operations
description: "Manage and validate Hermes cron jobs."
version: 1.0.0
license: MIT
platforms: [macos, linux, windows]
metadata:
  hermes:
    tags: [hermes, cron, scheduling, validation, telegram]
---

# Cron Job Operations

## Mission

Create, inspect, validate, run, and maintain Hermes scheduled jobs without duplicate schedules, silent failures, or unverified delivery.

## Trigger

Use for requests to create, modify, inspect, test, pause, resume, run, or troubleshoot Hermes cron jobs.

## Safety rules

- List jobs before updating, pausing, resuming, removing, or running one. Never guess an ID.
- Treat financial actions, external messages, and public publishing as approval-gated.
- Make prompts self-contained because cron runs in a fresh session.
- Prefer `deliver="origin"` for this user's Telegram requests unless another destination is explicitly specified.
- Use `attach_to_session` only when an ongoing conversational thread is intended.
- Do not create near-duplicate jobs.

## Workflow

1. Inspect current jobs and scheduler status.
2. Clarify schedule, timezone, scope, output, delivery, retry behavior, and verification.
3. Write a self-contained prompt with explicit success criteria.
4. Choose skills and toolsets narrowly enough to reduce failure surface.
5. Create or update the job with explicit fields.
6. Read the job back and verify schedule, prompt, delivery, skills, and state.
7. If requested, run it immediately in the background and report the handle without polling unnecessarily.
8. Verify the completed output or failure notification when it returns.

## Prompt design

Every recurring prompt should state:

- Objective
- Inputs and source locations
- Exact output format
- Date and timezone assumptions
- Deduplication rule
- Failure behavior
- Delivery expectation
- Completion evidence

For incremental scouts, use `continuity=true` only when prior output is useful and the prompt explains how to continue without duplicating work.

## Common commands

```bash
hermes cron list --all
hermes cron status
```

Use the `cronjob` tool for creation and lifecycle changes where available. Use CLI commands only when the user explicitly needs a terminal workflow.

## Verification

A job creation response is not proof of correct operation. Read the job back, then perform a safe immediate run when practical. Confirm output destination and content. For external delivery, verify the exact target message or record when the platform supports read-back.

## Failure modes

- **Duplicate job:** pause or remove only after listing and identifying the exact duplicate.
- **Wrong timezone:** state the timezone explicitly and use an unambiguous schedule.
- **Prompt too vague:** rewrite it self-contained.
- **Silent run:** add explicit output and failure reporting.
- **Stale job:** inspect continuity and last-run output before changing it.

## Completion standard

A cron task is complete only when its exact job ID, schedule, prompt scope, delivery, and verification state are known.
