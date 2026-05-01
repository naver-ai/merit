<!--
  MERIT — Decentralized Instruction Tuning
  Copyright (c) 2026-present NAVER Cloud Corp.
-->

# MERIT &mdash; Decentralized Instruction Tuning

**Conflict-Aware Splitting and Weight Merging**
*To appear at ICML 2026.*

[Project page](https://naver-ai.github.io/merit/)

<p align="center">
  <img src="https://raw.githubusercontent.com/naver-ai/merit/gh-pages/images/tsne.png" width="48%" alt="t-SNE of dataset-level gradients" />
  <img src="https://raw.githubusercontent.com/naver-ai/merit/gh-pages/images/pca_group.png" width="48%" alt="PCA-based groups" />
</p>

<p align="center">
  <em>Dataset-level gradients form sharp directional clusters &mdash; heterogeneity is structured, not noise.</em>
</p>

---

## Overview

MERIT is a decentralized merge-ready instruction-tuning pipeline. It estimates dataset-level
gradient conflicts on a small calibration set, extracts the dominant conflict axes via PCA,
partitions the mixture into K = 2<sup>r</sup> groups, fine-tunes each branch independently with
no cross-branch communication, and merges once via token-weighted averaging.

The pipeline is grounded in a local quadratic theory inside a shared flat basin: under that
geometry, merging is provably no worse than the weighted average of individual losses, with the
gain governed by curvature-weighted variance, and conflict-aware splitting is the choice that
maximizes that gain.

## Highlights

- **+2.7 average improvement** on an 8-benchmark multimodal suite (54.3 &rarr; 57.0) on
  Qwen2.5-VL-3B with 136 Vision-FLAN tasks.
- **0.8% wall-clock overhead** at 7B scale on a 176-source 1.6 M mixture.
- **Zero step-level synchronization** &mdash; branches train fully independently.
- **One-shot merge.** Token-weighted averaging, no retraining, no calibration after the fact.

## Status

Code coming soon.
