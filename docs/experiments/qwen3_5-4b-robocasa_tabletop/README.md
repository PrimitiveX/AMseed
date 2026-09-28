# PX · Qwen3.5 4B · RoboCasa Tabletop

[← All experiments](../../../README.md#navigate-the-results) · [Model family](../../models/qwen3_5/README.md) · [Dataset](../../datasets/robocasa_tabletop/README.md)

> Documentation status: **待补充**. The team-provided image lists this combination under 鑫龙. It does not contain metric values, logs or weights. Replace every placeholder with the run's actual records before announcing a release.

## 1. Input models and dataset

| Item | Exact artifact / revision |
| --- | --- |
| Input VLM (Qwen3.5 4B) | HF: 待补充（repo URL + commit SHA/revision） |
| Input PX initialization / S2 checkpoint | HF: 待补充（repo URL + commit SHA/revision; if trained from scratch, state explicitly） |
| Training dataset | RoboCasa Tabletop; source, exact snapshot and split: 待补充 |
| Dataset size | Episodes / trajectories / steps / task count: 待补充 |
| Processing and normalization | Converter version, modality mapping, action/state normalization stats: 待补充 |

Dataset note: Existing guide points to GR00T-X-Embodiment-Sim; actual selected folders, split and versions: 待补充.

## 2. Training setup

| Setting | Actual run value |
| --- | --- |
| Code revision | 待补充（Git SHA） |
| Resolved config and launch command | 待补充（include CLI overrides; link logs or config snapshot） |
| GPUs, precision and distributed strategy | 待补充 |
| Batch size × GPUs × accumulation | 待补充（effective global batch） |
| Steps/epochs, learning rates and schedule | 待补充 |
| Frozen/trainable modules, S1/S2 scope | 待补充 |
| Action horizon, image resolution, observations | 待补充 |
| Random seed | 待补充 |

Existing example only, **not verified as this run's configuration**: Example command: 8 processes × batch 16, max 50,000 steps (YAML says 100,000; command overrides it), save every 5,000; confirm for this run.

## 3. Training trace and checkpoint selection

| Step | Train loss (action / VLM if applicable) | Validation loss or metric | LR | Wall time | Checkpoint |
| ---: | ---: | ---: | ---: | ---: | --- |
| 待补充 | 待补充 | 待补充 | 待补充 | 待补充 | 待补充 |

- Training logs / W&B or tensorboard (link, access instructions): 待补充
- Final step and **selected evaluation checkpoint**: 待补充
- Selection rule (last / best validation / rollout-selected; avoid test-set tuning): 待补充
- Interrupted/restarted runs and total compute: 待补充

## 4. Test and rollout setup

| Setting | Actual run value |
| --- | --- |
| Evaluation code + simulator version | 待补充 |
| Test checkpoint / HF revision | 待补充 |
| Split, tasks and evaluation mode | 待补充 |
| Seeds and trials per task | 待补充 |
| Inference steps, action chunk and unnormalization key | 待补充 |
| Episode horizon and success criterion | 待补充 |
| Test logs, videos and exact command | 待补充 |

Existing example only: Example batch eval: 50 episodes per environment, max 720 steps, 12 action steps; document exact environment list, seeds and successes.

## 5. Rollout results

| Split / task | Successes | Trials | Success rate | Seed(s) | Evidence |
| --- | ---: | ---: | ---: | --- | --- |
| 待补充 | 待补充 | 待补充 | 待补充 | 待补充 | 待补充 |
| **Overall (define weighting)** | **待补充** | **待补充** | **待补充** | — | — |

Compute per-task success as `successes / trials`; state whether overall is micro-averaged across episodes or macro-averaged across tasks. List any excluded/failed runs and attach raw evaluation records before filling a score.

## 6. Release artifacts

| Artifact | Link |
| --- | --- |
| Input VLM checkpoint (HF) | 待补充 |
| Input PX/S2 checkpoint (HF) | 待补充 |
| **Trained output PX checkpoint (HF)** | **待补充** |
| Output model card and commit revision | 待补充 |
| Normalization stats, processor/tokenizer and action head | 待补充（state whether included in output repo） |
| Resolved config, train/test logs, rollout videos | 待补充 |

## Reproduction pointers

- [Existing guide](../../../examples/Robocasa_tabletop/README.md)
- [Training command template](../../../examples/Robocasa_tabletop/train_files/run_robocasa.sh)
- [YAML template](../../../examples/Robocasa_tabletop/train_files/PX_robocasa_gr1.yaml)
- [Evaluation command template](../../../examples/Robocasa_tabletop/eval_files/batch_eval_args.sh)

Run from the repository root after configuring the exact input artifacts and paths. Example files are starting points; compare resolved parameters to the run-specific fields above.
