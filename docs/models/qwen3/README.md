# Qwen3-VL base VLMs

[← Home](../../../README.md)

[Qwen3-VL](https://huggingface.co/collections/Qwen/qwen3-vl) is Qwen's multimodal model family for image, video and text understanding. The official cards discuss visual grounding, spatial reasoning and video understanding. They describe upstream VLM capabilities, not measured robotic rollout performance.

| Scale | Upstream model | Action-adapted input recorded in supplied reports | Run |
| --- | --- | --- | --- |
| 2B | [Official model](https://huggingface.co/Qwen/Qwen3-VL-2B-Instruct) | `Qwen3-VL-2B-Instruct-Action`; HF/revision pending | [RoboTwin direct S2](../../experiments/qwen3-2b-robotwin/README.md) |
| 4B | [Official model](https://huggingface.co/Qwen/Qwen3-VL-4B-Instruct) | `Qwen3-VL-4B-Instruct-Action`; HF/revision pending | [RoboTwin direct S2](../../experiments/qwen3-4b-robotwin/README.md) |

The earlier [S1 → S2 diagnostics](../../experiments/robotwin-s1-diagnostics/README.md) also include Qwen3-VL 8B. Their protocol differs from the direct-S2 comparison.
