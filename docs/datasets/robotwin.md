# RoboTwin 2.0 · benchmark and dataset

## Official introduction

A scalable simulator, demonstration generator and benchmark for bimanual manipulation. The official benchmark includes 50 dual-arm tasks and structured domain randomization. Our evaluated setup uses a specific repository revision; results should be compared only under the same tasks and rollout protocol. See the [official repository](https://github.com/RoboTwin-Platform/RoboTwin) and [project page](https://robotwin-platform.github.io/).

The description above concerns the upstream benchmark; the configurations and outcomes below are **our own** ABot-M0 runs.

## Experiments

- [ABot-M0 × Qwen3-VL-2B-Instruct](../experiments/abot-m0/robotwin/qwen3-vl-2b.md)
- [ABot-M0 × Qwen3-VL-4B-Instruct](../experiments/abot-m0/robotwin/qwen3-vl-4b.md)
- [ABot-M0 × Qwen3.5-0.8B](../experiments/abot-m0/robotwin/qwen3-5-0-8b.md)
- [ABot-M0 × Qwen3.5-4B](../experiments/abot-m0/robotwin/qwen3-5-4b.md)
- [ABot-M0 × Qwen3.5-9B](../experiments/abot-m0/robotwin/qwen3-5-9b.md)

## Reproduction details

| Item | This release |
|---|---|
| Benchmark revision and dataset release | `13c3c47` for our RoboTwin simulator; processed training-set release ID: TODO |
| Data license and access | Follow the license and download guidance of the official repository |
| Split / evaluation protocol | 50 tasks × 100 episodes in Clean and Randomized, seed 0 |

Training logs, processed-dataset checksums and inference traces: **TODO: public artifact links**.
