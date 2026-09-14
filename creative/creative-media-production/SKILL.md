---
name: creative-media-production
description: "Route multi-medium creative production workflows."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [creative, media, diagrams, infographics, ascii-art, gif, youtube, audio, comfyui, writing]
    related_skills: []
---

# Creative Media Production

## Overview

Use this umbrella for browser-deliverable, file-based, or model-generated creative output. The goal is to choose the right production lane, produce an artifact, and verify that it exists or renders before reporting completion.

Prefer one labeled subsection here over loading many narrow skills. If the task requires a complete legacy package, note that older package-level skills were archived unchanged and their operational detail was condensed here.

## When to Use

- The user asks for visual artifacts: diagrams, infographics, ASCII art, comic-style summaries, UI mockups, or image/video/audio generation.
- The user shares a YouTube/video URL and asks for transcript-derived summaries, posts, chapters, or blogs.
- The user asks for GIF search/download or reaction media.
- The user asks to humanize/edit prose so it sounds less generated.
- The user asks to run or build ComfyUI workflows.

## Routing by Medium

### ASCII art and terminal visuals

Use local tools first: `pyfiglet` for text banners, `cowsay` for speech bubbles, `boxes` for framed text, and image-to-ASCII converters for raster input. Keep width constraints explicit; many chat surfaces wrap at 80-100 columns.

### Infographics and knowledge visuals

Separate **content structure** from **visual style**. Pick a layout (timeline, matrix, dashboard, funnel, iceberg, comic strip, bento grid, hub-and-spoke, etc.) and a style (hand-drawn, corporate memphis, cyberpunk, chalkboard, technical schematic, pixel-art, watercolor, etc.). Ask for missing factual content only if it cannot be retrieved.

### Excalidraw diagrams

For architecture, flows, sequences, and concept maps, create `.excalidraw` JSON directly. Verify valid JSON and preserve editable elements rather than exporting a flat PNG unless the user asks for an image. Use consistent colors and include labels on arrows and groups.

### ComfyUI workflows

Use ComfyUI when the user needs controllable image/video/audio generation, node graphs, local workflows, or batch generation. Prefer official `comfy-cli` for install/lifecycle and direct REST/WebSocket execution for runs. Validate workflow JSON before execution, run health checks, and fetch outputs/logs rather than assuming success.

### AudioCraft / MusicGen / AudioGen

Use AudioCraft for text-to-music, melody-conditioned music, sound effects, and EnCodec examples. Choose smaller models for limited VRAM; document model size, duration, sample rate, and output path. For production music, consider whether a provider-backed audio tool is more appropriate.

### GIF search and reaction media

Use Tenor via `curl` + `jq` when a Tenor key is configured. Return a small set of candidates or download the chosen media. Verify URLs are reachable and safe to send.

### YouTube transcript-to-content

Fetch transcripts with the helper script or transcript libraries, then transform into the requested format: concise summary, chapter outline, quote extraction, thread, blog post, study notes, or action items. If transcript retrieval fails, try alternate transcript language/auto-generated tracks before giving up.

### Humanizing prose

Remove statistical AI-writing tells: generic transitions, inflated symmetry, overuse of em dashes/semicolons, boilerplate framing, excessive hedging, listy cadence, and vague intensifiers. Preserve meaning and the user's voice. Prefer targeted rewrites over wholesale personality injection.

## Verification Checklist

- [ ] The requested artifact exists: file path, URL, transcript text, generated media, or rewritten copy.
- [ ] The output format matches the medium and requested destination.
- [ ] Any generated JSON or code-backed artifact validates or opens.
- [ ] External downloads/API results were checked, not invented.
- [ ] The final answer includes the artifact or exact path/URL and any known limitations.
