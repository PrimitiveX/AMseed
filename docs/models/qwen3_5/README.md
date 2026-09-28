# Qwen3.5 base VLMs

[← Home](../../../README.md)

[Qwen3.5](https://huggingface.co/Qwen) is Qwen's multimodal model family. Its official model cards describe integrated vision-language processing and a hybrid of Gated DeltaNet and attention blocks. The robot-policy results below belong to the locally trained action model, not to the upstream VLM cards.

| Scale | Upstream model | Action-adapted input recorded in supplied reports | Run |
| --- | --- | --- | --- |
| 0.8B | [Official model](https://huggingface.co/Qwen/Qwen3.5-0.8B) | `Qwen3.5-0.8B-Action`; HF/revision pending | [RoboTwin](../../experiments/qwen3_5-0_8b-robotwin/README.md) |
| 4B | [Official model](https://huggingface.co/Qwen/Qwen3.5-4B) | `Qwen3.5-4B-Action`; HF/revision pending | [RoboTwin](../../experiments/qwen3_5-4b-robotwin/README.md) · [LIBERO](../../experiments/qwen3_5-4b-libero/README.md) |
| 9B | [Official model](https://huggingface.co/Qwen/Qwen3.5-9B) | `Qwen3.5-9B-Action`; HF/revision pending | [RoboTwin record; no result](../../experiments/qwen3_5-9b-robotwin/README.md) |

The supplied 4B RoboTwin report attributes higher memory use and longer runtime to unavailable acceleration kernels in that environment; this is an observation about that runtime, not a general 4B model ranking.
