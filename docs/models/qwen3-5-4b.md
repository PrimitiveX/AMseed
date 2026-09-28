# Qwen3.5-4B · VLM backbone

## Official model

Qwen3.5 is a natively multimodal model family; here its vision-language representation is adapted to an ABot-M0 action policy. See the [official model card](https://huggingface.co/Qwen/Qwen3.5-4B) and [ABot-M0 architecture](https://github.com/amap-cvlab/ABot-Manipulation).

| Field | Value |
|---|---|
| Official Qwen model | [Qwen3.5-4B](https://huggingface.co/Qwen/Qwen3.5-4B) |
| Nominal scale | 4B |
| Role in this repository | VLM backbone within ABot-M0 |
| Action-aware initialization | Project-specific `*-Action` derivative; **not** the stock Qwen checkpoint. Exact tokenizer additions, initialization script and hash: **TODO**. |
| RoboTwin cross-attention dimension | 2560 |
| Our Hugging Face action-base checkpoint | **TODO: `https://huggingface.co/<ORG>/qwen3-5-4b-action-base`** (placeholder; do not download until released) |

The official model link establishes the source family, not the exact local action-aware checkpoint. Record the exact base revision and action-token conversion when publishing weights.

## ABot-M0 experiments

- [ABot-M0 × RoboTwin 2.0](../experiments/abot-m0/robotwin/qwen3-5-4b.md)
- [ABot-M0 × LIBERO](../experiments/abot-m0/libero/qwen3-5-4b.md)
- [ABot-M0 × RoboCasa tabletop](../experiments/abot-m0/robocasa-tabletop/qwen3-5-4b.md)
- [ABot-M0 × CALVIN](../experiments/abot-m0/calvin/qwen3-5-4b.md)

The experiment page contains the training configuration, rollout protocol, metrics and task-level results. Our fine-tuned weights are linked there once uploaded.
