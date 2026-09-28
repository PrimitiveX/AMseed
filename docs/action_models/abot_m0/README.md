# ABot-M0 · action model index

[← Home](../../../README.md)

The official [ABot-M0 project](https://amap-cvlab.github.io/ABot-Manipulation/m0/index.html) introduces a vision-language-action model for robotic manipulation using Action Manifold Learning and 3D perception. See its [paper](https://arxiv.org/abs/2602.11236) and [official implementation](https://github.com/amap-cvlab/ABot-Manipulation). the official [ABot-M0 RoboTwin2 checkpoint](https://huggingface.co/acvlab/ABot-M0-RoboTwin2) must not be mistaken for one of our output checkpoints.

| Training path | Dataset | Evidence |
| --- | --- | --- |
| Direct S2, four backbone sizes | RoboTwin | [Four run records](../../datasets/robotwin/README.md) |
| Direct S2, Qwen3.5 4B | LIBERO | [Run record](../../experiments/qwen3_5-4b-libero/README.md) |
| Local S1 → S2 and upstream initialization diagnostics | RoboTwin | [Separate diagnostic record](../../experiments/robotwin-s1-diagnostics/README.md) |

The exact input checkpoint and output artifact for each local run are specified or marked pending on that run page. An official reference model is not evidence that a particular local run initialized from it.
