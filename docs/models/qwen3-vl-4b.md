# Qwen3-VL-4B-Instruct · VLM backbone

## Official model

Qwen3-VL provides image, text and video understanding across several dense model scales; here it is used as the perception-language backbone for the ABot-M0 action policy. See the [official model card](https://huggingface.co/Qwen/Qwen3-VL-4B-Instruct) and [ABot-M0 architecture](https://github.com/amap-cvlab/ABot-Manipulation).

| Field | Value |
|---|---|
| Official Qwen model | [Qwen3-VL-4B-Instruct](https://huggingface.co/Qwen/Qwen3-VL-4B-Instruct) |
| Nominal scale | 4B |
| Role in this repository | VLM backbone within ABot-M0 |
| Action-aware initialization | Project-specific `*-Action` derivative; **not** the stock Qwen checkpoint. Exact tokenizer additions, initialization script and hash: **TODO**. |
| RoboTwin cross-attention dimension | 2560 |
| Our Hugging Face action-base checkpoint | **TODO: `https://huggingface.co/<ORG>/qwen3-vl-4b-action-base`** (placeholder; do not download until released) |

The official model link establishes the source family, not the exact local action-aware checkpoint. Record the exact base revision and action-token conversion when publishing weights.

## ABot-M0 experiments

- [ABot-M0 × RoboTwin 2.0](../experiments/abot-m0/robotwin/qwen3-vl-4b.md)
- [Earlier S1 → S2 reproduction diagnostic](../experiments/abot-m0/robotwin/s1-to-s2-diagnostic.md)

The experiment page contains the training configuration, rollout protocol, metrics and task-level results. Our fine-tuned weights are linked there once uploaded.
