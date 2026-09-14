---
name: cron-model-evaluation
description: "Compare local models for Hermes cron jobs."
version: 1.0.0
license: MIT
platforms: [macos, linux, windows]
metadata:
  hermes:
    tags: [hermes, cron, ollama, local-models, evaluation]
---

# Cron Model Evaluation

## Mission

Compare local models for scheduled Hermes work using the same task, inputs, constraints, and evaluation rubric, then recommend a model based on quality, latency, reliability, and cost.

## Trigger

Use when evaluating or selecting local models for Hermes cron jobs, especially Ollama-served models.

## Protocol

1. Identify the real cron task and its acceptance criteria.
2. Record hardware, model names, quantization, context length, temperature, and tool access.
3. Confirm model availability and capture exact versions.
4. Create a fixed evaluation fixture with representative inputs and expected behaviors.
5. Run each model with identical prompt, timeout, tool budget, and output constraints.
6. Capture raw outputs, latency, token counts when available, errors, and resource observations.
7. Score with a task-specific rubric, not general impressions.
8. Compare quality against operational cost and failure rate.
9. Restore the original Hermes configuration after the experiment.
10. Save a concise recommendation and raw evidence in the designated reference location.

## Evaluation dimensions

- Task correctness
- Evidence discipline
- Instruction following
- Output format compliance
- Completeness
- Hallucination or unsupported-claim rate
- Latency
- Failure and retry rate
- Memory or CPU/GPU impact
- Cost and maintenance burden

## Experimental controls

Change one variable at a time. Warm-up behavior must be recorded. Separate cold-start latency from steady-state latency. Use multiple runs when variance matters. Do not select a model from one unusually good response.

## Safety

- Do not alter production cron jobs without explicit approval.
- Do not expose credentials in prompts or logs.
- Keep evaluation outputs separate from production outputs.
- Restore configuration even when a run fails.

## Deliverable

The evaluation memo should include:

- Test question
- Models and configuration
- Fixture and rubric
- Raw-result location
- Score table
- Failure analysis
- Recommended model by job type
- Confidence and limitations
- Configuration restored: yes/no

## Completion standard

The task is complete only when all selected models have been exercised under comparable conditions and the original configuration has been verified as restored.
