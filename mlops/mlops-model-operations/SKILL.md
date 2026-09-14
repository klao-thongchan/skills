---
name: mlops-model-operations
description: "Use when managing, evaluating, serving, tracking, or running ML/AI models and experiments: Hugging Face Hub, llama.cpp/GGUF, vLLM, lm-eval-harness, W&B, Jupyter exploration, SAM, AudioCraft, and similar model tooling."
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [mlops, models, huggingface, evaluation, inference, serving, gguf, vllm, wandb, jupyter, computer-vision, audio]
    related_skills: []
---

# MLOps Model Operations

## Overview

Use this umbrella for the operational lifecycle around ML/AI models: discover/download/upload models, run local inference, serve APIs, evaluate benchmarks, track experiments, iterate in notebooks, and operate model-specific toolkits. Choose the lane that matches the user's goal, verify real outputs, and record reproducibility details.

## When to Use

- The task mentions models, checkpoints, datasets, Hugging Face, GGUF, llama.cpp, vLLM, lm-eval, W&B, Jupyter kernels, SAM, AudioCraft/MusicGen, or model deployment/evaluation.
- The user asks to benchmark, serve, quantize, track, download, upload, or prototype with ML tooling.
- The task requires GPU/CPU capability checks, package installation, or long-running model commands.

## Universal Workflow

1. **Scope the objective:** discovery, inference, serving, evaluation, training tracking, data exploration, or model-specific processing.
2. **Check environment:** OS, Python/venv, GPU/CPU, RAM/VRAM, installed CLIs, auth tokens, and disk space as needed.
3. **Use the right backend:** official CLI/API first, local model runtime when requested, managed service when configured.
4. **Capture reproducibility:** model name/revision, command, flags, hardware, seed, output paths, and metrics.
5. **Verify output:** generated file, server health endpoint, benchmark JSON, W&B run URL, downloaded repo files, or notebook state.

## Labeled Lanes

### Hugging Face Hub

Use modern `hf` CLI, not deprecated `huggingface-cli`, for repository discovery, download/upload, datasets, Spaces, and auth. Use explicit repo IDs and revisions. Confirm license/access-gated status before downloads.

### llama.cpp / GGUF local inference

Use for CPU/edge/Apple Silicon/CUDA/ROCm local inference and GGUF quant selection. Pick quantization based on RAM/VRAM and quality target. For servers, verify `/health` or an OpenAI-compatible endpoint before testing prompts.

### vLLM serving

Use for high-throughput OpenAI-compatible LLM APIs and batch inference on GPU. Tune `--gpu-memory-utilization`, `--max-model-len`, tensor parallelism, quantization, prefix caching, and metrics. Verify with a real client request and inspect logs/metrics for OOM or slow TTFT.

### lm-evaluation-harness

Use for reproducible benchmarks such as MMLU, GSM8K, HellaSwag, TruthfulQA, ARC, HumanEval, or custom tasks. Record task names, few-shot count, model backend (`hf`, `vllm`, API), batch size, and output JSON. For speed, reduce tasks/few-shot or use vLLM.

### Weights & Biases

Use for experiment tracking, sweeps, artifacts, model registry, and collaborative dashboards. Check `WANDB_API_KEY`/login state, project/entity, offline vs online mode, and return run/artifact URLs after logging.

### Jupyter live kernel exploration

Use a stateful Jupyter kernel when iterative Python state matters: DataFrames, API probes, model inspection, plots, or hypothesis testing. Prefer one-shot scripts for deterministic automation; prefer live kernel for exploration and retained variables.

### Segment Anything Model (SAM)

Use SAM for zero-shot image segmentation with points, boxes, masks, automatic mask generation, annotation tools, and object extraction. Choose ViT-B/L/H by VRAM/quality, compute image embeddings once per image, and save/verify masks or RGBA outputs.

### AudioCraft / MusicGen / AudioGen

Use for local text-to-music, text-to-sound effects, melody-conditioned generation, and EnCodec examples. Record model size, duration, sample rate, prompt, and output path. Reduce duration/model size on OOM.

## Common Pitfalls

- Assuming GPU availability: check hardware and package compatibility first.
- Confusing model discovery with model serving: downloading a checkpoint is not a running endpoint.
- Reporting benchmark numbers without saving the exact config/output JSON.
- Starting long-running servers in foreground without background tracking and health checks.
- Printing tokens or private repo credentials.

## Verification Checklist

- [ ] Environment and credentials checked.
- [ ] Model/tool version and command/config recorded.
- [ ] Output artifact or endpoint was exercised.
- [ ] Metrics/logs/results were read back from disk/API.
- [ ] Final answer includes paths, URLs, model IDs, and any resource constraints.
