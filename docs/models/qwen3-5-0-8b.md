# Qwen3.5-0.8B · VLM backbone

## Official model

Qwen3.5 is a natively multimodal model family; here its vision-language representation is adapted to an ABot-M0 action policy. See the [official model card](https://huggingface.co/Qwen/Qwen3.5-0.8B) and [ABot-M0 architecture](https://github.com/amap-cvlab/ABot-Manipulation).

| Field | Value |
|---|---|
| Official Qwen model | [Qwen3.5-0.8B](https://huggingface.co/Qwen/Qwen3.5-0.8B) |
| Nominal scale | 0.8B |
| Role in this repository | VLM backbone within ABot-M0 |
| Action-aware initialization | Project-specific `*-Action` derivative; **not** the stock Qwen checkpoint. Exact tokenizer additions, initialization script and hash: **TODO**. |
| RoboTwin cross-attention dimension | 1024 |
| Our Hugging Face action-base checkpoint | **TODO: `https://huggingface.co/<ORG>/qwen3-5-0-8b-action-base`** (placeholder; do not download until released) |

The official model link establishes the source family, not the exact local action-aware checkpoint. Record the exact base revision and action-token conversion when publishing weights.

## ABot-M0 experiments

- [ABot-M0 × RoboTwin 2.0](../experiments/abot-m0/robotwin/qwen3-5-0-8b.md)

The experiment page contains the training configuration, rollout protocol, metrics and task-level results. Our fine-tuned weights are linked there once uploaded.
