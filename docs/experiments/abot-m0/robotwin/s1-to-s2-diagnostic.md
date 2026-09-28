# ABot-M0 · S1 → S2 reproduction diagnostic (RoboTwin)

This earlier two-stage branch uses **50 tasks × 10 Clean episodes (500 total)**, unlike the S2-only branch's 100-episode Clean and Randomized protocol. Internal `PX`/`PX_M0` names refer to ABot-M0. This result is published to expose a reproducibility failure, not to recommend these weights.

## Model origins and release slots

Original VLM families: [Qwen3-VL-2B](https://huggingface.co/Qwen/Qwen3-VL-2B-Instruct), [4B](https://huggingface.co/Qwen/Qwen3-VL-4B-Instruct), [8B](https://huggingface.co/Qwen/Qwen3-VL-8B-Instruct). Action-aware derivatives: **TODO: exact HF repos and hashes**. ABot-M0 [upstream repository](https://github.com/amap-cvlab/ABot-Manipulation) and [upstream RoboTwin S2 checkpoint](https://huggingface.co/acvlab/ABot-M0-RoboTwin2). The relation between that upstream S2 checkpoint and the upstream S1 is **unverified in the supplied record**. Project-trained S1/S2 HF checkpoints: **TODO**.

## Training and evaluation

| Configuration | Recorded setup |
|---|---|
| Project S1 | UniACT mixture, 100,000 steps; action horizon 16 (2B variant also 50); global batches 40/32/48/64 for 2B/2B-h50/4B/8B |
| Project S2 | RoboTwin-Randomized, 100,000 steps; action horizon 50; freeze spatial_model; load qwen and action_model |
| Upstream S1 + local S2 controls | Two 4B local S2 runs with output_dim 1024 and 2560 |
| Simulator | RoboTwin 2.0 commit `13c3c47`; `demo_clean.yml`; seed 0; 50 tasks × 10 episodes |
| Logs, scripts and precise S1 corpus manifest | **TODO: release links, revisions and hashes** |

The supplied record's full 50-task table is reproduced below; the 4B local-S1 column was **not evaluated**, so it is absent. Labels remain the original run IDs in the source report.

|     序号 | RoboTwin 任务      | PX_M0_robotwin_pretrain_Qwen3-VL-2B_100000steps | PX_M0_robotwin_pretrain_Qwen3-VL-2B_100000steps_action50 |  PX_M0_robotwin_pretrain_Qwen3-VL-8B_100000steps |  PX-M0-RoboTwin2 | PX_M0_robotwin | PX_M0_robotwin_2560 |
| -------: | ------------------------- | -------------------: | -------------------: | -------------------: | --------------------: | --------------------: | --------------------:  |
|        1 | adjust_bottle             |          6/10（60%） |          4/10（40%） |          7/10（70%） |         10/10（100%） |         10/10（100%） |         10/10（100%）  |
|        2 | beat_block_hammer         |          4/10（40%） |           0/10（0%） |          1/10（10%） |           9/10（90%） |           7/10（70%） |         10/10（100%）  |
|        3 | blocks_ranking_rgb        |           0/10（0%） |           0/10（0%） |           0/10（0%） |           8/10（80%） |           9/10（90%） |           8/10（80%）  |
|        4 | blocks_ranking_size       |           0/10（0%） |          1/10（10%） |           0/10（0%） |           7/10（70%） |           2/10（20%） |           4/10（40%）  |
|        5 | click_alarmclock          |          2/10（20%） |           0/10（0%） |           0/10（0%） |           7/10（70%） |            0/10（0%） |            0/10（0%）  |
|        6 | click_bell                |          5/10（50%） |          3/10（30%） |           0/10（0%） |           9/10（90%） |           1/10（10%） |           4/10（40%）  |
|        7 | dump_bin_bigbin           |          1/10（10%） |          3/10（30%） |          5/10（50%） |         10/10（100%） |           9/10（90%） |         10/10（100%）  |
|        8 | grab_roller               |          4/10（40%） |          3/10（30%） |          4/10（40%） |         10/10（100%） |         10/10（100%） |         10/10（100%）  |
|        9 | handover_block            |           0/10（0%） |          1/10（10%） |           0/10（0%） |           5/10（50%） |           5/10（50%） |           6/10（60%）  |
|       10 | handover_mic              |          4/10（40%） |          2/10（20%） |          8/10（80%） |         10/10（100%） |         10/10（100%） |         10/10（100%）  |
|       11 | hanging_mug               |           0/10（0%） |           0/10（0%） |           0/10（0%） |           2/10（20%） |           3/10（30%） |            0/10（0%）  |
|       12 | lift_pot                  |           0/10（0%） |          1/10（10%） |          4/10（40%） |         10/10（100%） |           9/10（90%） |         10/10（100%）  |
|       13 | move_can_pot              |           0/10（0%） |           0/10（0%） |          4/10（40%） |           8/10（80%） |           8/10（80%） |           6/10（60%）  |
|       14 | move_pillbottle_pad       |           0/10（0%） |           0/10（0%） |           0/10（0%） |           8/10（80%） |           8/10（80%） |           9/10（90%）  |
|       15 | move_playingcard_away     |          1/10（10%） |          1/10（10%） |           0/10（0%） |         10/10（100%） |         10/10（100%） |           9/10（90%）  |
|       16 | move_stapler_pad          |           0/10（0%） |           0/10（0%） |           0/10（0%） |           6/10（60%） |           1/10（10%） |           5/10（50%）  |
|       17 | open_laptop               |          4/10（40%） |          4/10（40%） |          4/10（40%） |         10/10（100%） |         10/10（100%） |           9/10（90%）  |
|       18 | open_microwave            |          3/10（30%） |          5/10（50%） |          3/10（30%） |           8/10（80%） |           8/10（80%） |         10/10（100%）  |
|       19 | pick_diverse_bottles      |           0/10（0%） |           0/10（0%） |           0/10（0%） |           9/10（90%） |           7/10（70%） |           7/10（70%）  |
|       20 | pick_dual_bottles         |           0/10（0%） |           0/10（0%） |           0/10（0%） |           7/10（70%） |           4/10（40%） |           6/10（60%）  |
|       21 | place_a2b_left            |           0/10（0%） |           0/10（0%） |           0/10（0%） |           9/10（90%） |           9/10（90%） |           9/10（90%）  |
|       22 | place_a2b_right           |           0/10（0%） |           0/10（0%） |           0/10（0%） |           9/10（90%） |           5/10（50%） |           6/10（60%）  |
|       23 | place_bread_basket        |          2/10（20%） |          1/10（10%） |           0/10（0%） |         10/10（100%） |         10/10（100%） |         10/10（100%）  |
|       24 | place_bread_skillet       |           0/10（0%） |           0/10（0%） |           0/10（0%） |           8/10（80%） |           9/10（90%） |         10/10（100%）  |
|       25 | place_burger_fries        |           0/10（0%） |          3/10（30%） |          2/10（20%） |         10/10（100%） |           8/10（80%） |           9/10（90%）  |
|       26 | place_can_basket          |           0/10（0%） |           0/10（0%） |          1/10（10%） |           8/10（80%） |           6/10（60%） |           8/10（80%）  |
|       27 | place_cans_plasticbox     |          1/10（10%） |          1/10（10%） |           0/10（0%） |         10/10（100%） |         10/10（100%） |         10/10（100%）  |
|       28 | place_container_plate     |          4/10（40%） |          4/10（40%） |          7/10（70%） |         10/10（100%） |           9/10（90%） |         10/10（100%）  |
|       29 | place_dual_shoes          |           0/10（0%） |           0/10（0%） |           0/10（0%） |           7/10（70%） |           7/10（70%） |           5/10（50%）  |
|       30 | place_empty_cup           |          1/10（10%） |           0/10（0%） |           0/10（0%） |         10/10（100%） |         10/10（100%） |         10/10（100%）  |
|       31 | place_fan                 |           0/10（0%） |           0/10（0%） |           0/10（0%） |           9/10（90%） |           9/10（90%） |         10/10（100%）  |
|       32 | place_mouse_pad           |           0/10（0%） |           0/10（0%） |           0/10（0%） |           6/10（60%） |           5/10（50%） |           3/10（30%）  |
|       33 | place_object_basket       |           0/10（0%） |          3/10（30%） |          2/10（20%） |           9/10（90%） |           9/10（90%） |           9/10（90%）  |
|       34 | place_object_scale        |           0/10（0%） |           0/10（0%） |           0/10（0%） |           8/10（80%） |           8/10（80%） |           9/10（90%）  |
|       35 | place_object_stand        |           0/10（0%） |           0/10（0%） |          3/10（30%） |         10/10（100%） |           9/10（90%） |         10/10（100%）  |
|       36 | place_phone_stand         |           0/10（0%） |           0/10（0%） |           0/10（0%） |           9/10（90%） |           9/10（90%） |           5/10（50%）  |
|       37 | place_shoe                |          1/10（10%） |          1/10（10%） |          1/10（10%） |         10/10（100%） |           9/10（90%） |           9/10（90%）  |
|       38 | press_stapler             |          5/10（50%） |          8/10（80%） |          3/10（30%） |           9/10（90%） |           9/10（90%） |           8/10（80%）  |
|       39 | put_bottles_dustbin       |           0/10（0%） |          1/10（10%） |           0/10（0%） |           7/10（70%） |           4/10（40%） |           5/10（50%）  |
|       40 | put_object_cabinet        |           0/10（0%） |          2/10（20%） |          1/10（10%） |           9/10（90%） |           9/10（90%） |           9/10（90%）  |
|       41 | rotate_qrcode             |           0/10（0%） |          1/10（10%） |           0/10（0%） |           8/10（80%） |           8/10（80%） |           8/10（80%）  |
|       42 | scan_object               |           0/10（0%） |           0/10（0%） |           0/10（0%） |           9/10（90%） |           9/10（90%） |           9/10（90%）  |
|       43 | shake_bottle              |          4/10（40%） |          4/10（40%） |          3/10（30%） |         10/10（100%） |         10/10（100%） |         10/10（100%）  |
|       44 | shake_bottle_horizontally |          5/10（50%） |          5/10（50%） |          5/10（50%） |         10/10（100%） |         10/10（100%） |         10/10（100%）  |
|       45 | stack_blocks_three        |           0/10（0%） |           0/10（0%） |           0/10（0%） |           6/10（60%） |           4/10（40%） |           8/10（80%）  |
|       46 | stack_blocks_two          |           0/10（0%） |          1/10（10%） |           0/10（0%） |         10/10（100%） |           8/10（80%） |           9/10（90%）  |
|       47 | stack_bowls_three         |          1/10（10%） |          1/10（10%） |           0/10（0%） |           7/10（70%） |           9/10（90%） |           8/10（80%）  |
|       48 | stack_bowls_two           |          2/10（20%） |          7/10（70%） |          4/10（40%） |         10/10（100%） |         10/10（100%） |           9/10（90%）  |
|       49 | stamp_seal                |           0/10（0%） |           0/10（0%） |           0/10（0%） |           8/10（80%） |           7/10（70%） |           7/10（70%）  |
|       50 | turn_switch               |          5/10（50%） |          3/10（30%） |          1/10（10%） |           8/10（80%） |           6/10（60%） |           5/10（50%）  |
| **合计** | **50 tasks**              | **65/500（13.00%）** | **74/500（14.80%）**  | **73/500（14.60%）** | **426/500（85.20%）** | **375/500（75.00%）** | **390/500（78.00%）**  |

## Readout

The project S1 → S2 runs reached **13.0% (2B horizon 16), 14.8% (2B horizon 50), 14.6% (8B horizon 16)**, versus **85.2%** for the tested upstream RoboTwin checkpoint. Two local S2 controls initialized from upstream S1 reached **75.0%** and **78.0%**. The observations point to the local S1 path as a likely source of the gap; they do not identify a proven root cause. The untested 4B local-S1 run has no success rate. Comparing these small 10-episode estimates with the separate 100-episode table requires care.

_Provenance: supplied `实验记录1.txt`; outcome and control configurations retain the original source's limitations._
