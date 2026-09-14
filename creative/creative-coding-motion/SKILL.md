---
name: creative-coding-motion
description: "Use when producing programmable visual media: p5.js sketches, Manim explainer videos, TouchDesigner networks, ASCII video, generative animation, and export pipelines."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [creative-coding, animation, video, p5js, manim, touchdesigner, ascii]
    related_skills: [web-design-prototyping, comfyui]
---

# Creative Coding & Motion

## Overview

This umbrella covers code-driven visual media. Whether the target is a p5.js sketch, Manim educational animation, TouchDesigner network, or ASCII-video render, the class-level process is: plan the scene, build a minimal runnable artifact, render/export real output, inspect it, and iterate for visual quality and performance.

## When to Use

- Generative art, simulations, shaders, interactive canvases, and p5.js sketches.
- 3Blue1Brown-style math/algorithm explainers in Manim.
- TouchDesigner MCP work: operators, networks, GLSL, audio-reactive visuals, projection mapping.
- Converting video/audio to stylized ASCII MP4/GIF outputs.
- Any creative animation where rendering and verification matter.

## Shared Production Workflow

1. Define the visual goal, aspect ratio, duration, and delivery format.
2. Build the smallest runnable scene/network/sketch first.
3. Add motion timing, color, typography, camera/composition, and effects in layers.
4. Render/export a sample.
5. Inspect actual output; fix readability, pacing, aliasing, framing, and performance.
6. Deliver both the source artifact and exported media when appropriate.

## Subsections by Medium

### p5.js

Use for browser-native generative art and interactive sketches. Keep a `viewer.html` or equivalent harness, separate controls from drawing state, and test export paths for frame capture or video encoding.

### Manim

Use for precise educational animation. Write scene plans before code, use clear object naming, preview low quality first, then render final quality. Prioritize mathematical readability over decorative effects.

### TouchDesigner MCP

Use for live visual systems and node networks. Work incrementally: create operators, wire them, set parameters, verify the network, then add animation, audio/MIDI/OSC, post-FX, or projection mapping.

### ASCII Video

Use for stylized conversions. Confirm input dimensions, frame rate, palette, glyph density, and audio handling. Render short samples before full-length export.

## Common Pitfalls

1. **Skipping a preview render.** Visual bugs are only obvious in output.
2. **Too much complexity at once.** Layer effects after a working core scene.
3. **Unreadable text/math.** Slow down pacing and increase contrast/size.
4. **Ignoring export constraints.** Aspect ratio, codec, duration, and file size shape implementation.
5. **Performance collapse.** Profile particle counts, shader cost, and frame export time early.

## Verification Checklist

- [ ] Source artifact runs in the intended runtime.
- [ ] A preview render/export was generated and inspected.
- [ ] Final output matches requested aspect ratio/duration/format.
- [ ] Motion is legible and not merely decorative.
- [ ] Dependencies/setup steps are documented.
