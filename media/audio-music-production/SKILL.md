---
name: audio-music-production
description: "Use when creating, prompting, analyzing, or transforming music/audio with songwriting craft, AI music systems, spectrogram tools, or local audio-generation models."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [audio, music, songwriting, ai-music, spectrogram, musicgen]
    related_skills: [youtube-content]
---

# Audio & Music Production

## Overview

Use this umbrella for music/audio tasks: writing lyrics, constructing Suno/HeartMuLa-style prompts, generating sounds with AudioCraft/MusicGen, and analyzing audio with spectrogram/features tools. The common workflow is to identify the intended listening experience, choose the right tool, produce or analyze a concrete artifact, and verify the output.

## When to Use

- Songwriting: lyrics, structure, rhyme, genre, arrangement notes.
- AI music prompts: tags, style descriptors, vocal/instrumentation constraints.
- HeartMuLa/Suno-like generation workflows.
- AudioCraft MusicGen/AudioGen local generation.
- Songsee/spectrogram/MFCC/chroma feature inspection.
- Converting analysis into practical production advice.

## Songwriting and Prompting

Start from intent: genre, mood, subject, POV, tempo, vocal type, era/reference, and constraints. Provide sections (`[Verse]`, `[Chorus]`, `[Bridge]`) and concise tags when the target system supports them. Avoid generic adjectives; specify arrangement and production details.

## AI Music Generation

For generation systems, treat prompt, seed, duration, model, and reference audio as reproducibility knobs. Render a short sample first when possible. Report provider/model limits honestly rather than inventing audio.

## AudioCraft / MusicGen

Use for local text-to-music or text-to-sound when dependencies and GPU/CPU resources are available. Confirm model size, sample rate, duration, and output path. Expect setup/runtime costs and verify by checking the generated audio file.

## Audio Feature Analysis

Use spectrograms, mel bands, chroma, MFCCs, tempo/onset, and waveform views to answer concrete questions: structure, timbre, rhythm, mixing issues, similarity, or transcription support.

## Common Pitfalls

1. **Prompt soup.** Long tag lists dilute direction; prioritize the defining sonic features.
2. **No artifact verification.** Check that generated files exist and play/analyze before claiming success.
3. **Ignoring licensing.** Do not imitate living artists' voices or copyrighted recordings beyond allowed stylistic references.
4. **Confusing analysis and production.** Translate features into actionable musical observations.

## Verification Checklist

- [ ] Requested lyrics/prompt/audio analysis format is satisfied.
- [ ] Generated or analyzed file path/URL is verified when applicable.
- [ ] Duration, style, instrumentation, and vocal constraints are explicit.
- [ ] Safety/licensing concerns are handled.
