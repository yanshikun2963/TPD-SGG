# TPD-Net: Tail Prototype Drift for Long-tailed Scene Graph Generation

## Overview

TPD-Net identifies and corrects **Tail Prototype Drift (TPD)** in prototype-based scene graph generation — the phenomenon where tail predicate prototypes deviate more from their empirical relation-feature centers than head prototypes. We propose two complementary components built on [PE-Net](https://github.com/VL-Group/PENET):

- **TEPA (Tail-aware Empirical Prototype Alignment)**: calibrates tail prototypes toward class-wise empirical centers using EMA estimates, compensating for weakened tail-side attraction.
- **CPTR (Confusion-Pair Targeted Repulsion)**: separates tail prototypes from their most confusable head counterparts identified through subject-object distribution overlap.

## Installation

Check [INSTALL.md](INSTALL.md) for installation instructions.

## Dataset

Check [DATASET.md](DATASET.md) for dataset preparation (VG-150, GQA-200, Open Images V6).

## Training

TPD-Net training has two stages. See `scripts/` for all training commands.

```bash
# Stage 1: Train PE-Net baseline
bash scripts/stage1_pretrain_penet.sh

# Stage 2: Train TPD-Net (TEPA + CPTR)
bash scripts/train_tpdnet.sh
```

CPTR requires pre-computed confusion pairs. We provide these in the Model Zoo, or generate them from scratch:

```bash
python datasets/prepare_freq_table.py
python datasets/prepare_confusion_pairs.py
```

## Model Zoo

Check [MODEL_ZOO.md](MODEL_ZOO.md) for all pretrained checkpoints and training logs.

| Dataset | Task    | R@50/100    | mR@50/100   | F@50/100    | Checkpoint        |
| ------- | ------- | ----------- | ----------- | ----------- | ----------------- |
| VG-150  | PredCls | 58.84/60.59 | 40.94/43.16 | 48.28/50.41 | (link to be added) |
| VG-150  | SGCls   | 36.64/37.06 | 21.86/23.19 | 27.38/28.53 | (link to be added) |
| VG-150  | SGDet   | 27.75/31.54 | 15.68/18.00 | 20.04/22.92 | (link to be added) |
| GQA-200 | PredCls | 52.46/53.77 | 37.49/38.85 | 43.73/45.11 | (link to be added) |
| GQA-200 | SGCls   | 21.64/22.16 | 16.92/17.63 | 18.99/19.64 | (link to be added) |
| GQA-200 | SGDet   | 19.08/21.56 | 13.85/15.55 | 16.05/18.07 | (link to be added) |
| OIV6    | SGDet   | 77.10/–     | 43.40/–     | 55.50/–     | (link to be added) |

> OIV6 follows the official SGDet protocol; we additionally report wmAP<sub>rel</sub>=38.0, wmAP<sub>phr</sub>=38.6, and score<sub>wtd</sub>=45.9 (see paper Table 3). The protocol provides @50 metrics only.

## Acknowledgement

This codebase is built upon [Scene-Graph-Benchmark.pytorch](https://github.com/KaihuaTang/Scene-Graph-Benchmark.pytorch) and [PE-Net](https://github.com/VL-Group/PENET).

## Citation

```bibtex
@inproceedings{tpdnet2026,
  title={Tail Prototype Drift: Empirical Calibration and Confusion-guided Repulsion for Long-tailed Scene Graph Generation},
  year={2026}
}
```
