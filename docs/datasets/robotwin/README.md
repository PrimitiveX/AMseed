# RoboTwin

[← Home](../../../README.md)

The official [RoboTwin 2.0](https://robotwin-platform.github.io/) project provides a simulated dual-arm manipulation benchmark with 50 tasks and domain randomization. Its [documentation](https://robotwin-platform.github.io/doc/) and [leaderboard](https://robotwin-platform.github.io/leaderboard) define official evaluation and training protocols. The supplied experiments used about 75 GB of mixed Clean and Randomized trajectories (27,500 trajectories, 6,075,103 transitions); exact dataset revision and split are pending. Their training data differ from the leaderboard's clean-only training setting.

| Base VLM | Clean successes / 5,000 | Randomized successes / 5,000 | Detailed record |
| --- | --- | --- | --- |
| Qwen3-VL 2B | 4183/5000 (83.66%) | 4195/5000 (83.90%) | [Run](../../experiments/qwen3-2b-robotwin/README.md) |
| Qwen3-VL 4B | 4285/5000 (85.70%) | 4267/5000 (85.34%) | [Run](../../experiments/qwen3-4b-robotwin/README.md) |
| Qwen3.5 0.8B | 4038/5000 (80.76%) | 4025/5000 (80.50%) | [Run](../../experiments/qwen3_5-0_8b-robotwin/README.md) |
| Qwen3.5 4B | 4294/5000 (85.88%) | 4256/5000 (85.12%) | [Run](../../experiments/qwen3_5-4b-robotwin/README.md) |
| Qwen3.5 9B | Pending | Pending | [Run record](../../experiments/qwen3_5-9b-robotwin/README.md) |

The four completed direct-S2 runs used 150,000 steps and were evaluated on 50 tasks × 100 episodes in each setting, seed 0, with RoboTwin commit `13c3c47` and an altered video-frame interface. See [50-task per-model results](task_results.md). The earlier [S1 → S2 diagnostics](../../experiments/robotwin-s1-diagnostics/README.md) used 10 Clean episodes per task, and their percentages must be read separately.
