# RoboTwin · earlier S1 → S2 diagnostics

[← Home](../../../README.md) · [RoboTwin](../../datasets/robotwin/README.md)

The supplied `实验记录1.txt` documents local S1 pretraining followed by S2 and comparisons involving upstream released weights. This is **not** the direct-S2 experiment series: local S1/S2 runs used 100,000 steps per stage, and the recorded evaluation used 50 Clean tasks × 10 episodes (500 total) for each assessed checkpoint. The Qwen3-VL 4B local S1 → S2 run had no supplied evaluation result.

| Recorded initialization / route | Clean successes / 500 | Recorded S1 and S2 training time |
| --- | ---: | --- |
| Local Qwen3-VL 2B S1 → local S2, action horizon 16 in S1 | 65/500 (13.0%) | 64.86 h + 53.12 h |
| Local Qwen3-VL 2B S1 → local S2, action horizon 50 in S1 | 74/500 (14.8%) | 58.29 h + 42.85 h |
| Local Qwen3-VL 4B S1 → local S2 | Not evaluated | 47.68 h + 56.92 h |
| Local Qwen3-VL 8B S1 → local S2 | 73/500 (14.6%) | 80.35 h + 76.80 h |
| Upstream released RoboTwin model evaluated locally | 426/500 (85.2%) | Upstream training log not supplied |
| Upstream S1 → locally trained S2 (`output_dim=1024`) | 375/500 (75.0%) | Upstream S1 log absent; local S2 31.21 h |
| Upstream S1 → locally trained S2 (`output_dim=2560`) | 390/500 (78.0%) | Upstream S1 log absent; local S2 38.18 h |

The report names an official ABot-M0 pretraining checkpoint and [ABot-M0-RoboTwin2](https://huggingface.co/acvlab/ABot-M0-RoboTwin2) as upstream references, while explicitly saying that the exact upstream RoboTwin model initialization from the published S1 checkpoint is unverified. Input and output HF links/revisions for **locally trained** checkpoints: **待补充**. Its 8B evaluation needed reruns after GPU scheduling errors; do not interpret the diagnostic percentages as leaderboard results or compare them directly with the 100-trial direct-S2 series.
