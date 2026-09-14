---
name: web-design-prototyping
description: "Use when creating browser-deliverable visual artifacts: HTML/CSS mockups, landing pages, design-system variants, diagrams, DESIGN.md tokens, and interactive web demos."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [web-design, html, css, prototypes, diagrams, design-systems, mockups]
    related_skills: [p5js, excalidraw]
---

# Web Design & Prototyping

## Overview

Use this umbrella for one-off browser artifacts and design prototypes. The common deliverable is a self-contained HTML/CSS/JS artifact or design-spec document that the user can view, compare, and iterate on. Favor tangible output over abstract description: create the file, open or screenshot it when possible, and refine from evidence.

## When to Use

- Designing landing pages, dashboards, cards, decks, or product mockups.
- Producing 2–3 visual variants for user comparison.
- Applying recognizable design-system references (Stripe, Linear, Vercel, Apple, Notion, etc.).
- Creating dark-themed architecture/cloud diagrams as HTML/SVG.
- Authoring or validating `DESIGN.md` token specs.
- Building interactive demos with small libraries or raw browser APIs.

## Workflow

1. Clarify constraints only when necessary: purpose, audience, brand/style, dimensions, and assets.
2. Pick a visual direction and write a self-contained artifact.
3. Keep dependencies minimal and CDN-safe unless the user asks for a framework.
4. Verify by rendering/screenshotting when browser tools are available.
5. Iterate based on visible evidence, not imagined aesthetics.

## Labeled Subsections

### Sketch-style mockups

For fast comparison, make 2–3 variants with obvious differences in layout, density, hierarchy, color, and typography. Label the variants so the user can choose a direction.

### Claude-design style artifacts

For polished one-off HTML artifacts, use strong visual hierarchy, real copy, responsive layout, and purposeful micro-interactions. Avoid placeholder gray boxes unless the task is explicitly wireframing.

### Popular web design references

When the user names or implies a brand style, translate the reference into design tokens: typography scale, spacing, border radii, color palette, depth, motion, and component rhythm. Do not copy logos or proprietary assets unless supplied.

### Architecture diagrams

Use SVG/HTML for crisp dark-mode diagrams. Show boundaries, data flow arrows, labels, protocols, and failure/observability paths. Prefer semantic grouping over decorative clutter.

### DESIGN.md token specs

When the deliverable is a design-system document, author valid token sections, example components, accessibility notes, and implementation guidance. Treat the spec as source-of-truth for later UI work.

### Pretext / interactive demos

For playful browser demos, keep the core interaction immediately visible, use requestAnimationFrame for animation, and include controls only if they help explore the concept.

## Common Pitfalls

1. **Only describing a design.** Produce an artifact file whenever asked to build/design.
2. **Overfitting to a named brand.** Capture principles without copying protected marks/assets.
3. **Invisible interactions.** Make hover/scroll/click affordances discoverable.
4. **No verification.** Render and inspect the result when tools are available.
5. **Too many dependencies.** A single HTML file is often the right prototype unit.

## Verification Checklist

- [ ] Artifact exists and opens without missing dependencies.
- [ ] Layout works at likely viewport sizes.
- [ ] Text contrast and hierarchy are acceptable.
- [ ] User-requested style references are visible.
- [ ] Any assets/fonts/scripts are available or gracefully degrade.
