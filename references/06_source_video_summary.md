# Primary Source Summary: AI Samson

* **Title**: The NEW Way To Get Perfect AI Character Consistency
* **Creator**: AI Samson
* **Video URL**: [https://www.youtube.com/watch?v=v-r-SWMiRo4](https://www.youtube.com/watch?v=v-r-SWMiRo4)

---

## Executive Overview

AI Samson presents a breakthrough methodology for maintaining strict facial, anatomical, and wardrobe continuity across 20 to 100+ AI-generated video shots [[00:21](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=21)], [[00:43](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=43)]. The traditional industry standard—feeding static 2D character reference sheets into generative models—consistently breaks down because diffusion models must hallucinate what lies between discrete, low-resolution static poses [[00:36](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=36)], [[00:56](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=56)].

By taking advantage of modern video model architectures that accept video-based conditioning inputs, this pipeline generates a **volumetric 360° turntable reference video** [[00:21](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=21)], [[01:04](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=64)]. When paired with an informational character turnaround sheet, it enables near-perfect character persistence across complex facial tattoos, asymmetrical robotic plating, hybrid biological textures, and complete wardrobe changes [[00:06](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=6)], [[11:37](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=697)].

---

## Core Benchmark Findings

Stress-tested against complex graphic anomalies (asymmetrical creature eye patches, ear dots, and full-body Japanese koi tattoos) [[07:24](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=444)], [[09:26](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=566)]:

| Metric | Single Image Reference [[08:30](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=510)] | 2D Character Sheet [[08:44](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=524)] | Hybrid: 360° Video + 2D Sheet [[09:04](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=544)] |
|---|---|---|---|
| **Frontal Sharpness** | Moderate; loses subtle details | Good; retains basic shapes | **Maximum; cleanest, sharpest line art** [[09:17](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=557)] |
| **Rear/Side Visibility** | **Fails completely**; hallucinates back details | Moderate; preserves general layout | **High; captures complex rear ear/skin patterns** [[09:09](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=549)] |
| **Micro-Tattoos & Markings** | Blurred, smudged, or missing entirely | Visible, but lacks fine textural edges | **Exact line reproduction (e.g., bird wings, koi fish)** [[06:40](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=400)], [[10:00](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=600)] |
| **Asymmetrical Features** | High error rate; frequently mirrors | Occasional mirroring glitches | **Retains orientation when backed by prompt locks** [[05:12](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=312)], [[07:43](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=463)] |
| **Iteration Overhead** | Extreme; requires dozens of rerolls | High reroll frequency | **Significantly reduced reroll requirement** [[10:57](https://www.youtube.com/watch?v=v-r-SWMiRo4&t=657)] |

---

## Key Timestamp Index

* **[00:21]**: Introduction of volumetric 360° turntable conditioning.
* **[00:56]**: Explanation of the interpolation gap in 2D sheets.
* **[01:20]**: Base character creation via GPT Image 2.5 Sunburst on Higgsfield.
* **[02:02]**: 16:9 Split-Frame layout (full body left / facial portrait right).
* **[03:06]**: 3-angle character turnaround sheet (front, profile, back).
* **[03:29]**: Locked-off camera invariant prompt for turntable compilation.
* **[03:40]**: Video compilation in Cance 2.5 and Kling 4.
* **[04:56]**: Dual ingestion technique (`@Turntable_Video` + `@Character_Sheet`).
* **[05:12]**: Asymmetry prompt locking protocol for unilateral features.
* **[09:17]**: Benchmark results: micro-tattoo clarity comparison.
* **[10:13]**: The Dirty Turntable trap and inspection protocol.
* **[11:08]**: Multi-character interaction and spatial coordinate isolation.
* **[11:37]**: Wardrobe swapping while preserving facial geometry.
* **[12:34]**: Model comparisons: Sunburst vs Nano Banana; Cance 2.5 vs Kling 4 vs Hailuo 3.
