# ABot-M0 × Qwen3.5-4B · LIBERO

## Official components

- [ABot-M0](https://github.com/amap-cvlab/ABot-Manipulation), [official Qwen3.5-4B](https://huggingface.co/Qwen/Qwen3.5-4B), [LIBERO official benchmark](https://github.com/Lifelong-Robot-Learning/LIBERO).
- Read [Qwen3.5-4B](../../../models/qwen3-5-4b.md) and [LIBERO dataset](../../../datasets/libero.md) before comparing against a different protocol.
- Starting action-aware base HF: **TODO: `https://huggingface.co/<ORG>/qwen3-5-4b-action-base`**.
- Fine-tuned `steps_40000` HF: **TODO: `https://huggingface.co/<ORG>/abot-m0-qwen3-5-4b-libero`**. [Official ABot-M0 LIBERO weights](https://huggingface.co/acvlab/ABot-M0-LIBERO) are an upstream reference, **not** this project's fine-tuned checkpoint.

## Training setup and process

| Parameter | Value |
|---|---|
| Recorded run | `PX_M0_libero_Qwen3.5-4B-Action` / `steps_40000` |
| ABot-M0 stage | **TODO: confirm stage and whether S1 initialization was used** |
| Dataset source, split, number of trajectories | **TODO: exact dataset revision and split** |
| Image and action processing, normalization | **TODO** |
| Optimizer, learning rates, batch, GPUs, training duration | **TODO: supply from training config and logs** |
| Checkpoint recorded | `steps_40000`; this does not establish whether 40,000 is the final selected step |
| Loss curve / training logs | **TODO: links** |

## Closed-loop rollout

The supplied summary states that each of the 10 tasks in each suite was rolled out **50 times**. Success/failure was counted from each rollout video's filename. Exact evaluator commit, seeds, episode horizon and whether rollouts followed an official evaluation script: **TODO**. Preserve video manifests to independently audit these counts.

| Suite | Successful / episodes | Success rate |
|---|---:|---:|
| LIBERO-Goal | 488/500 | 97.6% |
| LIBERO-Spatial | 487/500 | 97.4% |
| LIBERO-Object | 500/500 | 100.0% |
| LIBERO-10 | 460/500 | 92.0% |
| **All four suites** | **1,935/2,000** | **96.75%** |

The table below retains every task result in the supplied file:

## libero_goal

| # | Task | 成功/总数 | 成功率 |
|---:|---|---:|---:|
| 0 | open the middle drawer of the cabinet | 50/50 | 100.0% |
| 1 | turn on the stove | 50/50 | 100.0% |
| 2 | put the bowl on the stove | 48/50 | 96.0% |
| 3 | put the cream cheese in the bowl | 49/50 | 98.0% |
| 4 | put the wine bottle on the rack | 50/50 | 100.0% |
| 5 | open the top drawer and put the bowl inside | 44/50 | 88.0% |
| 6 | put the wine bottle on top of the cabinet | 50/50 | 100.0% |
| 7 | push the plate to the front of the stove | 49/50 | 98.0% |
| 8 | put the bowl on the plate | 50/50 | 100.0% |
| 9 | put the bowl on top of the cabinet | 48/50 | 96.0% |

**Suite 总体成功率：488/500 = 97.6%**


## libero_spatial

| # | Task | 成功/总数 | 成功率 |
|---:|---|---:|---:|
| 0 | pick up the black bowl in the top drawer of the wooden cabinet and place it on the plate | 47/50 | 94.0% |
| 1 | pick up the black bowl between the plate and the ramekin and place it on the plate | 49/50 | 98.0% |
| 2 | pick up the black bowl on the wooden cabinet and place it on the plate | 48/50 | 96.0% |
| 3 | pick up the black bowl on the ramekin and place it on the plate | 47/50 | 94.0% |
| 4 | pick up the black bowl next to the plate and place it on the plate | 50/50 | 100.0% |
| 5 | pick up the black bowl next to the cookie box and place it on the plate | 50/50 | 100.0% |
| 6 | pick up the black bowl from table center and place it on the plate | 49/50 | 98.0% |
| 7 | pick up the black bowl on the cookie box and place it on the plate | 48/50 | 96.0% |
| 8 | pick up the black bowl next to the ramekin and place it on the plate | 49/50 | 98.0% |
| 9 | pick up the black bowl on the stove and place it on the plate | 50/50 | 100.0% |

**Suite 总体成功率：487/500 = 97.4%**


## libero_object

| # | Task | 成功/总数 | 成功率 |
|---:|---|---:|---:|
| 0 | pick up the butter and place it in the basket | 50/50 | 100.0% |
| 1 | pick up the bbq sauce and place it in the basket | 50/50 | 100.0% |
| 2 | pick up the tomato sauce and place it in the basket | 50/50 | 100.0% |
| 3 | pick up the chocolate pudding and place it in the basket | 50/50 | 100.0% |
| 4 | pick up the salad dressing and place it in the basket | 50/50 | 100.0% |
| 5 | pick up the orange juice and place it in the basket | 50/50 | 100.0% |
| 6 | pick up the cream cheese and place it in the basket | 50/50 | 100.0% |
| 7 | pick up the milk and place it in the basket | 50/50 | 100.0% |
| 8 | pick up the alphabet soup and place it in the basket | 50/50 | 100.0% |
| 9 | pick up the ketchup and place it in the basket | 50/50 | 100.0% |

**Suite 总体成功率：500/500 = 100.0%**


## libero_10

| # | Task | 成功/总数 | 成功率 |
|---:|---|---:|---:|
| 0 | pick up the book and place it in the back compartment of the caddy | 46/50 | 92.0% |
| 1 | put both moka pots on the stove | 36/50 | 72.0% |
| 2 | put both the cream cheese box and the butter in the basket | 49/50 | 98.0% |
| 3 | put the black bowl in the bottom drawer of the cabinet and close it | 47/50 | 94.0% |
| 4 | put the white mug on the left plate and put the yellow and white mug on the right plate | 49/50 | 98.0% |
| 5 | put the white mug on the plate and put the chocolate pudding to the right of the plate | 42/50 | 84.0% |
| 6 | put the yellow and white mug in the microwave and close it | 47/50 | 94.0% |
| 7 | put both the alphabet soup and the cream cheese box in the basket | 49/50 | 98.0% |
| 8 | put both the alphabet soup and the tomato sauce in the basket | 46/50 | 92.0% |
| 9 | turn on the stove and put the moka pot on it | 49/50 | 98.0% |

**Suite 总体成功率：460/500 = 92.0%**




_Provenance: supplied `libero_success_rate_summary.md`. These results are recorded for `steps_40000`; they are not the official ABot-M0 paper baseline._
