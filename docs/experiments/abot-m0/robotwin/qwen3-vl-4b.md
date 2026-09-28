# ABot-M0 × Qwen3-VL-4B-Instruct · RoboTwin 2.0

**Run ID:** `PX_M0_robotwin_Qwen3-VL-4B` · **Status:** Training and 100-episode Clean/Randomized rollouts recorded.

## Official components and checkpoint provenance

- Action model: [ABot-M0 official code](https://github.com/amap-cvlab/ABot-Manipulation) and [paper](https://arxiv.org/abs/2602.11236). `PX` and `PX_M0` are the internal experiment names for ABot-M0 here.
- VLM: [official Qwen3-VL-4B-Instruct](https://huggingface.co/Qwen/Qwen3-VL-4B-Instruct); [backbone notes](../../../models/qwen3-vl-4b.md). The local `Qwen3-VL-4B-Action` starting point is a project derivative; **its exact HF revision is TODO**.
- Benchmark: [RoboTwin 2.0 official repository](https://github.com/RoboTwin-Platform/RoboTwin); [dataset notes](../../../datasets/robotwin.md).
- This run's starting action-base HF: **TODO: `https://huggingface.co/<ORG>/qwen3-vl-4b-action-base`**.
- This run's **fine-tuned final** HF: **TODO: `https://huggingface.co/<ORG>/abot-m0-qwen3-vl-4b-robotwin-s2`**.

## Training setup

| Parameter | Value |
|---|---|
| Training stage | S2 only; no project-trained S1 initialized |
| Initialization | Project-specific action-aware VLM derived from the official Qwen family; exact derivative HF repository and commit: **TODO** |
| Training data | RoboTwin-Randomized local mixture of Clean and Randomized; reported 27,500 trajectories, 6,075,103 transitions, ~75 GB; provenance/hash **TODO** |
| GPUs / precision | 4 × H200 NVL; bf16; DeepSpeed ZeRO-2, no CPU offload |
| Training steps / global batch | 150,000 / 64 (4 GPUs × 16 samples × 1 accumulation) |
| Optimizer | AdamW; β=(0.9, 0.95); ε=1e-8; weight decay=1e-8 |
| Learning rate / schedule | base=1e-5; qwen_vl_interface=1e-5; action_model=1e-4; cosine_with_min_lr, min_lr=5e-7, warmup=5,000 |
| Frozen / loaded | freeze `spatial_model`; load `qwen_vl_interface` and `action_model` |
| Action model | DiT-B; action horizon=50; output_dim=2560; repeated_diffusion_steps=4 |
| Data and saving | image 224 × 224; PyAV video backend; workers=4; save/eval every 5,000 steps |
| Training entry points | `examples/Robotwin/train_files/run_robotwin_train.sh`; `PX_robotwin.yaml` in upstream ABot-M0 derivative; exact code commit **TODO** |
| Cross-attention dimension | 2560 |
| VLM integration | Qwen3-VL integration; transformers 4.57.0 |

Recorded software: Python 3.12.3; PyTorch 2.8.0+cu128; accelerate 1.5.2; diffusers 0.39.0; NumPy 1.26.4. These are recorded run values, not installation instructions.

## Training process and artifacts

| Measure | Recorded value |
|---|---|
| Final action_dit_loss / mse_score | 0.00133165 / 0.000190013 |
| Final epoch / learning rate | 0.31 / 5e-7 |
| Mean / peak GPU memory | 83.26 / 83.93 GiB (mean / peak) |
| S2 wall time | 72:01:59 |
| Average training throughput | 0.578 step/s; 37.0 samples/s |
| Final model weight size | 12.58 GB (decimal GB) |
| Training loss curve / logs | **TODO: link to chart, W&B and raw logs** |

## Closed-loop rollout protocol

| Setting | Value |
|---|---|
| Simulator | RoboTwin 2.0 commit `13c3c47` (the record warns about incompatibility with current main) |
| Configs | `demo_clean.yml` and `demo_randomized.yml`; seed 0; domain_randomization differs |
| Deployment | `deploy_policy.yml`: action_mode=abs, unnorm_key=robotwin, instruction_type=unseen |
| Rollouts | 50 tasks × 100 episodes per condition = 5,000 episodes per condition |
| Parallel evaluator | `examples/Robotwin/eval_files/parallel_eval/eval_notebook_gpu_queue.sh` |
| GPU scheduling | 4 GPUs × 4 jobs |
| Evaluator implementation | Internal changes to `eval_policy.py`, `model2robotwin_interface.py`, `_base_task.py`; exact patch/commit **TODO** |
| Video logs | `eval_video_log=false`; rollout logs under `rollout_100/` on the training machine; public copy **TODO** |

## Rollout results

| Condition | Successful / total | Success rate | Wall time |
|---|---:|---:|---|
| Clean | 4285/5,000 | 85.70% | 6:23:04 |
| Randomized | 4267/5,000 | 85.34% | 6:46:13 |

Per-task outcome: [50-task results (CSV)](qwen3-vl-4b-task-results.csv). Reported per-task numbers are rates, not individual trajectories; episode manifests and failed-rollout traces: **TODO**.

## Interpretation and limits

Training time depends on hardware, concurrency and software environment; success rate is the fraction of completed episodes under the stated protocol. Cross-run comparisons use the same nominal training steps and 50-task, 100-episode evaluation setup, but the exact action-base weight revision and evaluator patch still need release. No claim is made for the 9B run until its results are available.

_Provenance: supplied `实验记录2-927.txt`; 4B comparison also cross-checked against the supplied S2 comparison report._
