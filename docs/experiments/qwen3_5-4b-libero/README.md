# ABot-M0 · Qwen3.5 4B · LIBERO

[← Home](../../../README.md) · [LIBERO](../../datasets/libero/README.md) · [Qwen3.5](../../models/qwen3_5/README.md)

## Input, training and output

| Field | Evidence from supplied reports |
| --- | --- |
| Base VLM family | Qwen3.5 4B; [official upstream card](https://huggingface.co/Qwen/Qwen3.5-4B) |
| Actual action-adapted input checkpoint and HF revision | **待核实 / 待补充**; do not assume it equals the RoboTwin run's local `Qwen3.5-4B-Action` |
| Training dataset and split | **待补充** |
| Actual steps, optimizer, hardware, loss curve and time | **待补充**; the checkpoint directory name alone does not establish the run history |
| Evaluated checkpoint label | 40,000-step checkpoint in supplied LIBERO summary |
| Output model HF repository and immutable revision | **待补充** |

## Closed-loop evaluation

The supplied success summary counts video filenames tagged success/failure, with 50 trials for each of 40 tasks in four suites. Seed, simulator commit, exact evaluation code and raw videos: **待补充**.

| Suite | Successes / episodes | Success rate |
| --- | ---: | ---: |
| Goal | 488/500 | 97.6% |
| Spatial | 487/500 | 97.4% |
| Object | 500/500 | 100.0% |
| LIBERO-10 | 460/500 | 92.0% |
| **All four** | **1,935/2,000** | **96.75%** |

[All 40 task-level counts](../../datasets/libero/task_results.md). This is the observed closed-loop outcome; training metrics should be added when the actual training log is supplied.
