# 🔬 MedSAM2 — Educational Segmentation UI Simulation

[![Live Demo](https://img.shields.io/badge/🔗-Live_Demo-8b5cf6)](https://shadman19.github.io/medsam2/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![SAM2 Concept](https://img.shields.io/badge/Inspired_by-SAM2-blue)](https://github.com/facebookresearch/sam2)

> A browser-only educational simulation of a prompt-based medical-image segmentation interface. It does not load or run Meta's SAM2 model. The current JavaScript draws synthetic masks and generates sample Dice, IoU, area and latency values with random numbers.
>
> **Implementation scope:** masks and displayed scores are illustrative UI output, not model predictions, measured segmentation accuracy or clinical results. Some legacy UI labels use SAM2 terminology; this README states the actual implementation.

**[Try the Live Demo →](https://shadman19.github.io/medsam2/)**

---

## What This Does

Upload an image and place prompt points to explore the interface:

- Synthetic mask overlays drawn on canvas
- Random sample Dice and IoU display values; no ground-truth comparison is computed
- Illustrative organ labels and area values
- Simulated heatmap visualization; no SAM2 attention is extracted
- Multi-point prompting controls
- Random sample latency display; no model inference is timed

## Example Modality Labels

The labels below populate the simulation; they do not establish trained or validated model support.

| Modality | Organs/Structures |
|----------|-------------------|
| 🫁 Chest X-Ray | Lung-L, Lung-R, Heart, Trachea |
| 🧠 Brain MRI | Cortex, Ventricle, Cerebellum, Lesion |
| 🩻 Abdominal CT | Liver, Kidney-L, Kidney-R, Spleen |
| 👁️ Fundus | Optic Disc, Macula, Vessels, Lesion |

## Conceptual SAM2 Pipeline

This diagram is educational background, not the execution path of the browser simulation. No encoder, prompt encoder or mask decoder is run by the current JavaScript.

```
Medical Image
      │
      ▼
┌─────────────────┐
│  Hiera Encoder  │  Image → 256-dim patch features
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Prompt Encoder  │  Click points → sparse embeddings
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Mask Decoder   │  Two-way transformer attention
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Multi-Scale    │  FPN → high-resolution mask
│  Fusion (FPN)   │
└────────┬────────┘
         │
         ▼
  Mask + Dice + IoU
```

## Usage

Open `index.html` in any browser. No setup, no installation, no API key.

Or use the live demo: **https://shadman19.github.io/medsam2/**

## Research Context

- Ravi et al. (2024) — SAM 2: Segment Anything in Images and Videos (Meta FAIR)
- Ma et al. (2024) — Segment Anything in Medical Images (MedSAM, Nature Communications)
- Related: False Negative Induction in Brain Tumor Segmentation by Trained Noise Attack (IEEE, 2023)

---

*Built by Shadman Mahmood Khan Pathan · [GitHub](https://github.com/Shadman19) · [LinkedIn](https://linkedin.com/in/shadmanmahmood9)*
