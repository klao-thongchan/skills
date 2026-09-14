# Ollama Cron Comparison Reference

## Fixed test record

Record these values for every model:

- Ollama version
- Model name and tag
- Quantization
- Context length
- Temperature and other generation settings
- Hardware and available memory
- Prompt fixture version
- Tool access
- Start and finish timestamps
- Raw output path
- Error and retry count

## Comparison table

| Model | Correctness | Format | Evidence discipline | Latency | Failures | Resource load | Recommendation |
|---|---:|---:|---:|---:|---:|---:|---|
|  |  |  |  |  |  |  |  |

## Procedure

1. Warm up each model and record cold-start behavior separately.
2. Run the same fixture with the same timeout and prompt.
3. Repeat when output variance affects the decision.
4. Score against the real cron acceptance criteria.
5. Inspect unsupported claims and missed instructions.
6. Restore production configuration.
7. Save raw outputs before summarizing.

## Decision rule

Choose the least expensive model that clears the required quality and reliability threshold. Do not choose on latency alone when a bad scheduled output creates manual cleanup or reputational cost.
