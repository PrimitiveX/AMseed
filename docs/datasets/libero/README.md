# LIBERO

[← Home](../../../README.md)

The official [LIBERO repository](https://github.com/Lifelong-Robot-Learning/LIBERO) introduces a lifelong robot learning benchmark with vision-language manipulation tasks. Its Goal, Spatial and Object suites isolate different transfer factors; the LIBERO-10 suite is a subset of the larger task collection. See the [official dataset description](https://lifelong-robot-learning.github.io/LIBERO/html/algo_data/datasets.html). The original continual-learning protocol and a single model evaluated over four suites should be distinguished.

The supplied result uses the local 40,000-step ABot-M0 checkpoint. Success/failure was counted from video filenames for 10 tasks in each suite, 50 trials per task:

| Suite | Successful rollouts | Rate |
| --- | ---: | ---: |
| Goal | 488/500 | 97.6% |
| Spatial | 487/500 | 97.4% |
| Object | 500/500 | 100.0% |
| LIBERO-10 | 460/500 | 92.0% |
| **Total** | **1,935/2,000** | **96.75%** |

[Training/rollout record](../../experiments/qwen3_5-4b-libero/README.md) · [Per-task counts](task_results.md). The supplied material does not specify the training data version, hyperparameters, simulator revision, or seed; these remain pending.
