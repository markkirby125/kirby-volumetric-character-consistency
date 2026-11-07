# Dispatcher: Volumetric AI Character Consistency

Comprehensive standard operating procedure for engineering high-continuity AI video characters across multi-shot sequences (20–100+ shots). Eliminates facial drift, asymmetrical mirroring, and textural melting by replacing static 2D multi-angle reference sheets with **Volumetric 360° Turntable Video Conditioning** coupled with high-frequency 2D turnaround sheets.

---

## 🏷️ Canonical Asset Tag Register

To prevent prompt drift and undefined variable references across scene generations, all downstream prompts and instructions MUST strictly adhere to this standardized tag register:

| Asset Variable | Data Type | Canonical Description | Role in Diffusion Engine |
|---|---|---|---|
| `@master_video` | Video (.mp4) | Master 360° locked turntable video (5–10s, 1 full rotation). | Supplies 3D volume, rotational lighting curvature, and continuous geometry. |
| `@turnaround_sheet` | Image (.png) | 3-angle informational turnaround sheet (Front, Profile, Back). | Supplies frozen high-frequency edge sharpness, micro-markings, and ear textures. |
| `@last_scene_frame` | Image (.png) | High-res still frame from the most recently approved scene (`N-1`). | Anchors progressive wardrobe wear, direct lighting continuity, and composition. |
| `@charA_video` / `@charB_video` | Video (.mp4) | Turntable video references for distinct characters in multi-actor scenes. | Isolates independent volumes to prevent character-bleed and feature blending. |

---

## 🧭 Operational Routing Matrix

Consult the specialized module matching your current production phase:

| Module | Purpose & Scope | Target Output |
|---|---|---|
| [`01_volumetric_asset_pipeline.md`](01_volumetric_asset_pipeline.md) | 4-Phase Protocol: Base character, split-frame canvas, turnaround sheet, and locked turntable compile. | Master `@master_video` and `@turnaround_sheet` assets. |
| [`02_dual_reference_prompting.md`](02_dual_reference_prompting.md) | Scene construction syntax, dual ingestion rules, conditional spatial locks, and anti-rotation clauses. | Narrative scene shots with zero facial drift. |
| [`03_advanced_production_workflows.md`](03_advanced_production_workflows.md) | Wardrobe decoupling with persistent anatomy, multi-actor spatial isolation, and iterative scene chaining. | Complex costume changes and multi-character scenes. |
| [`04_tooling_and_economics.md`](04_tooling_and_economics.md) | Model capability benchmarks, tooling re-validation, and high-compute vs daily workhorse economics. | Optimized budget allocation across shot types. |
| [`05_failure_modes_and_mitigations.md`](05_failure_modes_and_mitigations.md) | The Dirty Turntable QA Gate, camera drift triage, unilateral mirroring cures, and divergence recovery. | Defect-free final outputs. |
| [`06_source_video_summary.md`](06_source_video_summary.md) | Timestamped evidence breakdown from AI Samson's benchmark masterclass. | Foundational research context and citations. |

---

## 🛑 When NOT to Use This Skill

Do not deploy this volumetric workflow under any of the following conditions:
* **Single-Shot Stills**: If the deliverable is a single static poster or illustration, a standard high-detail image prompt or single LoRA/image reference is sufficient.
* **Short 1–2 Cut Micro-Clips**: For non-narrative shorts where the character is never seen from side or rear angles, the overhead of rendering a 360° turntable outweighs the consistency benefits.
* **Text-Only Video Engines**: If the target platform does not support video conditioning files (`@video` inputs), this skill cannot execute.

---

## ⚡ The Architectural Paradigm Shift

```text
TRADITIONAL 2D REFERENCE SHEET (FAILURE PRONE)
┌────────────────────────────────────────────────────────┐
│  • Multiple tiny 2D poses crammed on one 16:9 canvas  │
│  • Low pixel density per facial coordinate             │
│  • Generative video model interpolates blind angles    │
└───────────────────────────┬────────────────────────────┘
                            │
                            ▼ Produces Morphing & Inconsistencies
┌────────────────────────────────────────────────────────┐
│  • Facial drift across shots                           │
│  • Missing back/side micro-details (ears, hairstyles)  │
│  • Left/Right asymmetrical features flip randomly      │
└───────────────────────────┘

VOLUMETRIC 360° TURNTABLE METHOD (HYBRID DUAL-INGESTION)
┌────────────────────────────────────────────────────────┐
│  Step 1: High-detail base character synthesis          │
│  Step 2: 16:9 Split-Frame (Full Body Left / Face Right)│
│  Step 3: Informational Turnaround Sheet (Back & Sides) │
│  Step 4: Locked 360° Turntable Video Conditioning      │
└───────────────────────────┬────────────────────────────┘
                            │
                            ▼ Dual Ingestion (@turnaround_sheet + @master_video)
┌────────────────────────────────────────────────────────┐
│  • Razor-sharp facial tattoos & ear markings preserved │
│  • Exact 3D volume, lighting curvature & anatomy       │
│  • Persistent identity across complete wardrobe swaps  │
└────────────────────────────────────────────────────────┘
```

### Why 2D Reference Sheets Inevitably Fail:
1. **The Canvas Real Estate Penalty**: Cramming 5 to 8 poses into a single 16:9 image limits the face to a tiny fraction of total pixels. Diffusion models lack sufficient detail to resolve micro-markings or subtle iris/bone structures.
2. **The Temporal Interpolation Gap**: Video diffusion models cannot accurately deduce intermediate rotations between disparate static angles. As a character turns, intermediate geometry melts and reshapes.
3. **The Occlusion Blindspot**: Standard front-facing reference sheets hide posterior and lateral details (neck tattoos, ear shape, hair ties). When the video model pans around the character, it is forced to invent features on the fly.

### The Volumetric Breakthrough:
Modern generative video engines accept native video files as conditioning inputs. A continuous 360° in-place turntable gives the neural network a temporal, frame-by-frame map of the character's geometry in three-dimensional space. Pairing this video reference (`@master_video`) with a high-resolution 2D turnaround sheet (`@turnaround_sheet`) provides both **spatial volumetric volume** and **high-frequency textural sharpness**.

---

## 🔗 Related Skills in the Kirby Ecosystem

* [Kirby YT Faceless Formula](../../kirby-yt-faceless-formula/SKILL.md) — Multi-shot video production pipelines, script breakdown, and faceless channel automation.
* [Kirby AI Design System](../../kirby-ai-design-system/SKILL.md) — DOM-native Paper MCP + Higgsfield toolstack for vector assets and consistent branding.
* [Kirby Skills Collection](../../kirby-skills-collection/SKILL.md) — Master registry and dispatcher for all specialized AI skills.
