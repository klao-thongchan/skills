---
name: thananon-coding-skill
description: "GitHub profile skill from @thananon. Use it when the task would benefit from mimicking this developer's repo choices, coding style, and implementation techniques."
---

## What they tend to build

- Practical tooling for a specific community/workflow, not generic libraries: Twitch bot utilities, Discord/Twitch integrations, JIRA dashboards, and “skills” for agentic workflows.
- Projects are often operational rather than exploratory: bots, admin tools, dashboards, migration scripts, performance benchmarks, and repo automation.
- They like packaging real usage paths up front: install, run, env setup, Docker, database migration, and tests are usually documented in the repo root.
- Newer work often separates “old stable” from “v2 / work in progress” instead of forcing one code path to do everything.

## Coding patterns to mirror

- Prefer explicit orchestration through scripts over hidden conventions. Top-level `package.json` commands are used heavily to make common tasks one-liners.
- Keep workflows reproducible:
  - env vars are spelled out in README examples
  - migrations are separate from schema changes
  - dev/test/db-studio commands are distinct
- Use clear repo partitioning when a product has multiple parts:
  - backend/frontend split
  - old bot/new bot split
  - scripts and generated artifacts separated from app code
- Strong validation habits show up in config choices and docs:
  - strict TypeScript settings in `tsconfig`
  - test commands wired into scripts
  - migration steps documented as plan → generate → inspect → migrate → commit
- Docs are practical and direct. They often include:
  - exact commands
  - example `.env` snippets
  - Docker Compose diffs
  - small “how to run” walkthroughs
- When writing code for this style, favor small, explicit functions and operational naming over clever abstractions.

## Product and UI taste

- Utility-first, dashboard-heavy UI: summary cards, filters, grouped tables, detail side panels, and clear status breakdowns.
- Functional over decorative, but not bare: they use established UI kits and templates when they speed up delivery.
- Good docs matter. They like:
  - shields/badges
  - screenshots or logos
  - concise feature lists
  - direct links to live demos or issue trackers
- Product framing is usually “help a specific user do a specific job fast,” not “showcase a platform.”

## Tech stack clues

- Strong signal for JavaScript/TypeScript, especially Node.js backend work.
- Common stack pieces across repos:
  - TypeScript
  - Node.js
  - Express
  - Prisma
  - Jest
  - React / Create React App
  - Svelte + Vite
  - CoreUI
  - Docker / docker-compose
- Utility and automation work also leans on shell scripting, Perl, gnuplot, and repo scripts.
- They seem comfortable with monorepo-style layouts and multiple runtime entrypoints in one project.
- Tooling is pragmatic: `nodemon`, `ts-node-dev`, `concurrently`, `dotenv-flow`, and test-specific DB setup scripts.

## When to inspect repos first

- Before changing bot behavior, command handling, or state storage in `twitch_tools`: the repo has both legacy and newer implementations, plus DB/migration assumptions.
- Before touching any data model or persistence code: schema/migrations are treated as a workflow, not an afterthought.
- Before editing shared scripts or install commands: the repo relies on them for day-to-day usage and deployment.
- Before making UI changes in `vibejira` or `covidth`: inspect existing component structure and UI kit usage so the result matches the app’s dashboard-oriented, practical layout.
- Before naming new env vars, commands, or directories: this style favors explicit, documented conventions, and consistency matters more than cleverness.

## Repo Map

- [thananon/9arm-skills](https://github.com/thananon/9arm-skills) (2894 stars, Shell)
- [thananon/twitch_tools](https://github.com/thananon/twitch_tools) (116 stars, TypeScript)
- [thananon/vibejira](https://github.com/thananon/vibejira) (52 stars, JavaScript)
- [thananon/covidth](https://github.com/thananon/covidth) (27 stars, Svelte)
- [thananon/vibepoll](https://github.com/thananon/vibepoll) (7 stars, TypeScript)
- [thananon/vibecontrol](https://github.com/thananon/vibecontrol) (4 stars, TypeScript)
- [thananon/.dotfiles](https://github.com/thananon/.dotfiles) (4 stars, Perl)
- [thananon/class_project](https://github.com/thananon/class_project): This is a cabinet of all my class project. Please feel free to use it (Given you can read my code) and correct me if I made something wrong. (3 stars, C)
- [thananon/benchmark](https://github.com/thananon/benchmark) (1 stars, C++)
- [thananon/results](https://github.com/thananon/results): This is a repo for performance result of several project (0 stars, Gnuplot)

## How To Use This Skill

- Reach for this skill when the user asks for Arm Patinyasakdikul's style, when the repo stack matches this person's ecosystem, or when studying their real code would reduce made-up output.
- Pick one or more relevant repositories from the list above based on the current task.
- Clone the most relevant repository or repositories into `/tmp` for temporary inspection.
- Study the implementation details, naming patterns, architecture, UI taste, and tooling choices there.
- Return to the main task and apply the useful patterns you observed instead of copying blindly.
- Treat the upstream repositories as reference material for style and technique, then adapt them to the current codebase responsibly.
