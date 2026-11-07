# Volumetric AI Character Consistency 🥒🎥

> **Deterministic standard operating procedure (SOP) for maintaining strict facial, anatomical, and wardrobe continuity across 20 to 100+ AI-generated video shots.**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Architecture: Hollow Shell](https://img.shields.io/badge/Architecture-Hollow%20Shell-brightgreen.svg)](SKILL.md)
[![Compatibility](https://img.shields.io/badge/Agents-Antigravity%20%7C%20Cursor%20%7C%20Claude%20%7C%20Windsurf%20%7C%20Reasonix-orange.svg)](#-universal-agent-installation)

Traditional AI character consistency relies on static 2D reference sheets crammed with 5 to 8 poses onto a single canvas. When diffusion video models attempt to animate these flat images, they are forced to interpolate between discrete angles, resulting in **facial melting, distorted bone geometry, and unilateral mirroring glitches** (e.g., asymmetrical tattoos and eye patches randomly flipping sides).

This skill packages the breakthrough **Volumetric 360° Turntable Video Conditioning** methodology pioneered by creator AI Samson. By feeding generative video engines a continuous 360° turntable reference video paired with a high-resolution 2D turnaround sheet, this pipeline provides both **continuous 3D spatial volume** and **high-frequency textural sharpness**, enabling true cinematic character continuity across multi-scene productions.

---

## 🪄 Universal Agent Installation

Copy and paste this "Magic Prompt" into **any** AI coding assistant (Antigravity, Cursor, Windsurf, Claude Code, Grok, Kimi, Reasonix, Codex, Roo Code):

```markdown
@agent Install the Volumetric Character Consistency skill from: https://github.com/markkirby125/kirby-volumetric-character-consistency
1. Read `SKILL.md` and `references/` from the repository.
2. Place into your environment's skills/rules directory preserving the dispatcher structure.
3. Confirm when installation is complete.
```

### Manual Installation (Local Symlink)
To deploy locally across your AI coding environments:
```bash
git clone https://github.com/markkirby125/kirby-volumetric-character-consistency.git ~/.gemini/config/skills/kirby-volumetric-character-consistency
ln -sfn ~/.gemini/config/skills/kirby-volumetric-character-consistency ~/.cursor/skills/kirby-volumetric-character-consistency
ln -sfn ~/.gemini/config/skills/kirby-volumetric-character-consistency ~/.codeium/windsurf/skills/kirby-volumetric-character-consistency
ln -sfn ~/.gemini/config/skills/kirby-volumetric-character-consistency ~/.claude/skills/kirby-volumetric-character-consistency
```

---

## 🏛️ The Architectural Paradigm Shift

```text
TRADITIONAL 2D REFERENCE SHEET METHOD (FAILURE PRONE)
┌────────────────────────────────────────────────────────┐
│  • Multiple tiny 2D poses crammed on one 16:9 canvas  │
│  • Severe pixel starvation on facial coordinates       │
│  • Video model must guess/interpolate missing angles   │
└───────────────────────────┬────────────────────────────┘
                            │
                            ▼ Produces Morphing & Inconsistencies
┌────────────────────────────────────────────────────────┐
│  • Severe facial drift and changing bone structure     │
│  • Hallucinated back/side details (ears, hair ties)    │
│  • Left/Right asymmetrical features flip unpredictably │
└────────────────────────────────────────────────────────┘

NEW VOLUMETRIC 360° TURNTABLE METHOD (HYBRID DUAL-INGESTION)
┌────────────────────────────────────────────────────────┐
│  Phase 1: High-fidelity concept generation (Sunburst)  │
│  Phase 2: 16:9 Split-Frame (Full Body Left / Face Right│
│  Phase 3: Informational Turnaround Sheet (Back & Sides)│
│  Phase 4: Cance 2.5 / Kling 4 Locked Turntable Video   │
└───────────────────────────┬────────────────────────────┘
                            │
                            ▼ Dual Ingestion (@turnaround_sheet + @master_video)
┌────────────────────────────────────────────────────────┐
│  • Razor-sharp facial tattoos & ear markings preserved │
│  • Exact dimensional volume, lighting & anatomy        │
│  • Identity locked even during complete wardrobe swaps │
└────────────────────────────────────────────────────────┘
```

---

## 📊 Empirical Benchmark Analysis

Stress-tested against complex graphic anomalies (asymmetrical creature eye patches, ear dots, full-body Japanese koi tattoos):

| Evaluation Metric | Single Image Reference | Traditional 2D Character Sheet | Hybrid: 360° Video + 2D Sheet |
|---|---|---|---|
| **Frontal Sharpness** | Moderate; loses subtle details | Good; retains basic shapes | **Maximum; sharpest high-frequency line art** |
| **Rear/Side Visibility** | **Fails completely**; hallucinates back details | Moderate; preserves general layout | **High; captures complex rear ear/skin patterns** |
| **Micro-Tattoos & Markings** | Blurred, smudged, or missing entirely | Visible, but lacks fine textural edges | **Exact line reproduction (koi fish, bird wings)** |
| **Asymmetrical Features** | High error rate; frequently mirrors | Occasional mirroring glitches | **Retains orientation when backed by prompt locks** |
| **Iteration Overhead** | Extreme; requires dozens of re-rolls | High re-roll frequency | **Dramatically reduced re-rolls; predictable spend** |

---

## 🏷️ Canonical Asset Tag Register

To prevent prompt drift and undefined references across production scenes, all prompts adhere to this standard register:

| Asset Variable | Data Type | Canonical Purpose | Conditioning Role |
|---|---|---|---|
| `@master_video` | Video (.mp4) | Master 360° locked turntable video (5–10s, 1 full turn). | Continuous 3D volume, rotational lighting vectors, anatomical mass. |
| `@turnaround_sheet` | Image (.png) | 3-angle turnaround sheet (Front, Profile, Back). | Frozen high-frequency edge sharpness, micro-markings, ear textures. |
| `@last_scene_frame` | Image (.png) | High-res still frame from the previous approved scene (`N-1`). | Progressive wardrobe wear, direct lighting continuity, scene composition. |
| `@charA_video` / `@charB_video` | Video (.mp4) | Individual turntable video references for multi-actor scenes. | Isolates spatial coordinates to prevent character-bleed and feature blending. |

---

## 🚀 Core Workflows

### 1. The 4-Phase Asset Generation Pipeline
1. **Phase 1: Base Character Creation**: Synthesize the baseline design in **GPT Image 2.5 Sunburst** (via Higgsfield). Prioritizes anatomical realism and defined bone structure over stylized caricature.
2. **Phase 2: Split-Frame Start Canvas (16:9)**: Left 50% full-body standing pose; Right 50% extreme facial portrait. Eliminates pixel starvation by maximizing density on facial topology.
3. **Phase 3: Informational Turnaround Sheet**: Ingest Phase 1 & 2 references to generate Front, Side, and Back views documenting posterior assets (ear shapes, hair knots, rear jacket seams).
4. **Phase 4: Volumetric 360° Turntable Video**:
   * Condition **Cance 2.5** or **Kling 4** on the cropped full-body subject and turnaround sheet.
   * Enforce strict kinetic camera invariants:
     ```text
     Locked-off static camera, stationary tripod, zero camera movement, no zoom, no pan, no tilt, zero cuts, clean studio turntable character reference. The single character smoothly and slowly rotates 360 degrees once in place on a neutral dark grey studio backdrop. Constant rotational speed, stable lighting, zero morphing, pristine anatomical consistency throughout full rotation.
     ```
   * **Mandatory QA Gate**: Perform a frame-by-frame scrub. If *any* facial warping or tattoo fading occurs during rotation, discard and re-roll.

### 2. Scene Assembly & Dual Ingestion Prompting
Upload **both** `@master_video` and `@turnaround_sheet` simultaneously into the video engine.
* **Dual Ingestion**: Video drives spatial volume; static sheet anchors textural sharpness.
* **Anti-Rotation Motion Clause**: Explicitly instruct the engine that reference subject rotation must not leak into scene action:
  ```text
  The character maintains natural directional movement through the scene. Do NOT spin, rotate in place, or replicate turntable motion.
  ```
* **Spatial Left/Right Hard-Locking**: For asymmetrical characters, explicitly pin coordinates in every prompt:
  ```text
  Retain the cybernetic plating strictly on the RIGHT side of the face; keep the left cheekbone completely clear of markings. Zero mirrored asymmetry.
  ```

### 3. Wardrobe Decoupling & Persistent Anatomy
Transition characters through different clothing (evening gowns, tactical suits, winter parkas) without facial drift:
* Ingest `@master_video` + `@turnaround_sheet`.
* Explicitly lock skull geometry, eyes, and markings to the references while completely overriding clothing materials, drape, and cut in natural language.

### 4. Multi-Character Interaction Pipeline
Choreograph two distinct characters without feature cross-pollination:
* Upload `@charA_video` and `@charB_video`.
* Hardcode spatial coordinates (Screen-Left vs Screen-Right).
* Enforce spatial partitioning: neither character crosses into the other's quadrant.

---

## 🛠️ Tooling Matrix & Production Economics

To scale multi-shot productions without exhausting credit budgets, generation spend is divided into two tiers:

| Tier | Scope | Recommended Tooling | Rationale |
|---|---|---|---|
| **Tier 1: Master Anchor Tier** | Foundational split-frames & master 360° turntable video (`@master_video`). | GPT Image 2.5 Sunburst + Cance 2.5 (Premium) | Maximum detail retention. Upfront spend prevents cascading errors across all downstream shots. |
| **Tier 2: Production Workhorse Tier** | Narrative scene shots, dialogue cuts, tracking movements. | Kling 4 (Standard) conditioned on `@master_video` + `@turnaround_sheet` | Scalable credit cost; relies on the premium turntable for 3D spatial stability. |
| **Action Tier** | Wide dynamic action shots where facial micro-detail is secondary. | Minimax Hailuo 3 (Fluid) | Exceptional kinetic human motion. |

---

## 🗂️ Repository Structure

This repository strictly implements the **Hollow Shell Architecture** (root `SKILL.md` ≤ 200 tokens) to prevent AI context window bloat:

```text
kirby-volumetric-character-consistency/
├── SKILL.md                                  # Lightweight dispatcher shell (≤ 200 tokens)
├── README.md                                 # Public documentation & installation guide
├── LICENSE                                   # MIT License
└── references/
    ├── 00_dispatcher.md                      # Master router & Canonical Asset Tag Register
    ├── 01_volumetric_asset_pipeline.md       # 4-Phase Asset Scaffolding SOP
    ├── 02_dual_reference_prompting.md        # Scene Assembly, Tagging & Spatial Locks
    ├── 03_advanced_production_workflows.md   # Wardrobe Swaps & Multi-Character Staging
    ├── 04_tooling_and_economics.md           # Model Capabilities & Resource Optimization
    ├── 05_failure_modes_and_mitigations.md   # The Dirty Turntable QA Gate & Mirroring Fixes
    └── 06_source_video_summary.md           # AI Samson Masterclass Transcription & Citations
```

---

## 📜 Primary Source & Attribution

Adapted from the benchmark methodology presented by **AI Samson**:
* **Source Video**: [*The NEW Way To Get Perfect AI Character Consistency*](https://www.youtube.com/watch?v=v-r-SWMiRo4)
* **Creator**: AI Samson
* Detailed timestamp index and evidence breakdown available in [`references/06_source_video_summary.md`](references/06_source_video_summary.md).

---

## 📄 License

MIT License. Copyright (c) 2026 Mark Kirby. Distributed as part of the [Kirby Skills Library](https://github.com/markkirby125/kirby-skills).
