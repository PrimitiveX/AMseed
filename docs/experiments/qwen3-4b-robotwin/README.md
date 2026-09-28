# ABot-M0 · Qwen3-VL 4B · RoboTwin

[← Home](../../../README.md) · [RoboTwin](../../datasets/robotwin/README.md) · [ABot-M0 overview](../../action_models/abot_m0/README.md)

## Checkpoint provenance

| Artifact | Value |
| --- | --- |
| Local action-adapted VLM input named in report | `Qwen3-VL-4B-Instruct-Action` |
| Input HF repository and immutable revision | **待补充** |
| S2 initialization beyond recorded input / exact module mapping | **待核实** |
| Output checkpoint | `final_model/pytorch_model.pt` in the experiment report; HF repository and immutable revision: **待补充** |
| Official upstream VLM | See [family page](../../models/qwen3/README.md); this is not the local `-Action` input |

## Training settings

| Field | Recorded setting |
| --- | --- |
| Training path | Direct S2, no locally pretrained S1 |
| GPUs / global batch | 4 × H200 NVL; 4 × 16 × 1 = 64 |
| Dataset | RoboTwin-Randomized, including Clean and Randomized; ~75 GB, 27,500 trajectories, 6,075,103 transitions |
| Steps / checkpoints | 150,000 steps; save and evaluation interval 5,000 |
| Images / actions | 224 × 224; action horizon 50; repeated diffusion steps 4; DiT-B action model |
| Distributed training | Accelerate 1.5.2, DeepSpeed ZeRO-2, bf16, no CPU offload; PyTorch 2.8.0+cu128 |
| Trainable modules | Load `qwen_vl_interface` and `action_model`; freeze `spatial_model` |
| Optimizer | AdamW, betas (0.9, 0.95), eps 1e-8, weight decay 1e-8 |
| Learning rates | base 1e-5; Qwen interface 1e-5; action model 1e-4 |
| Schedule | cosine with minimum LR 5e-7; warmup 5,000 steps |
| Model-specific interface | `cross_attention_dim=2560`; `transformers=4.57.0` |

## Training trace

| Measurement | Recorded result |
| --- | --- |
| Completed steps | 150,000; final epoch ~0.31, LR 5e-7 |
| Total wall time | 72:01:59 |
| Training throughput | ~0.578 steps/s |
| Reported peak GPU memory | ~83.93 GiB |
| Final action_dit_loss | 0.00133165 |
| Final mse_score | 0.000190013 |

These are end-of-run observations from the supplied reports. Raw loss charts and full optimizer logs are **待补充**.

## Evaluation and closed-loop rollouts

RoboTwin commit `13c3c47`; policy setting `action_mode=abs`, `unnorm_key=robotwin`, `instruction_type=unseen`; seed 0. Evaluation used a modified interface that reads only the first frame of each action chunk. Each setting covers 50 tasks × 100 trials (5,000 total), with GPU concurrency up to 4 per GPU. The input checkpoint during evaluation was the local final model; video logging was disabled.

| Setting | Successful / total | Wall time |
| --- | ---: | --- |
| Clean | 4285/5000 (85.70%) | 6:23:04 |
| Randomized | 4267/5000 (85.34%) | 6:46:13 |

[Task-level success fractions](../../datasets/robotwin/task_results.md) include difficult and failed tasks. These runs trained on mixed Clean/Randomized data; they do not implement the official leaderboard's clean-only training protocol. Exact dataset snapshot, simulator patches, raw logs and output HF revision are **待补充**.
