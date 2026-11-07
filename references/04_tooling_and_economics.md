# Module 04: Tooling Matrix & Production Economics

Scaling a 20 to 100+ shot production pipeline requires balancing computational fidelity with generation credit consumption. Allocating premium compute to foundational reference assets while deploying cost-effective engines for bulk narrative shots prevents budget exhaustion.

---

## 1. Engine Capabilities & Selection Matrix

> **⚠️ Tooling Re-Validation Note**: AI video platforms evolve rapidly. Model names cited here (e.g., Cance 2.5, Kling 4, Minimax Hailuo 3) reflect the state of testing in late 2026. Prior to production, verify current platform capabilities: ensure the chosen engine accepts native video-to-video / temporal conditioning (`@video`) inputs and adheres to camera-locking prompts.

| Category | Representative Engines | Key Capabilities | Operational Constraints | Production Role |
|---|---|---|---|---|
| **Base Image Generation** | **GPT Image 2.5 Sunburst** (via Higgsfield) | Superior anatomical proportions, crisp micro-details, clean prompt adherence. | Standard credit tier; requires structured split-frame prompting. | **Primary Choice**: Mandatory for Phase 1 base characters & Phase 2 split frames. |
| **Fast Image Generation** | **Nano Banana 2.1** | Rapid generation speed, high visual punch and contrast. | Prone to aspect ratio warping and limb/facial distortion. | **Secondary Only**: Not recommended for foundational references. |
| **High-Fidelity Video Engine** | **Cance 2.5** / Premium Tier | Industry-leading detail retention; sharpest tattoo and facial fidelity; minimal blurring. | Premium credit cost per second; slower queue processing. | **Master Asset Tier**: Reserve for `@master_video` turntables and extreme close-up hero shots. |
| **Workhorse Video Engine** | **Kling 4** / Standard Tier | High reference adherence, stable motion dynamics, scalable credit cost. | Slight softening of sub-millimeter textures during rapid motion. | **Production Workhorse**: Recommended for 80% of daily scene renders and dialogue cuts. |
| **Dynamic Video Engine** | **Minimax Hailuo 3** / Fluid Tier | Fluid human kinetic movement, strong environmental lighting integration. | Weaker adherence to unilateral asymmetry; higher risk of mirroring. | **Action Tier**: Best for wide dynamic shots where facial micro-detail is secondary. |

---

## 2. Production Economics & Resource Allocation Strategy

To produce high-volume commercial or cinematic videos without runaway costs, structure generation spend into two distinct tiers:

### Tier 1: The Master Anchor Asset Tier (High-Compute Budget)
* **Assets**: Base character split frame + 360° volumetric turntable video (`@master_video`).
* **Tooling**: High-fidelity image engine + premium video engine.
* **Philosophy**: Do not cut costs on foundational assets. Re-roll the turntable video until it is 100% physically coherent. Investing upfront compute here prevents cascading failures across all downstream production shots.

### Tier 2: The Multi-Shot Narrative Tier (Optimized Workhorse Budget)
* **Assets**: Scene generations, dialogue shots, medium tracking shots.
* **Tooling**: Workhorse video engine (conditioned on `@master_video` + `@turnaround_sheet`).
* **Philosophy**: Leverage standard-tier credit efficiency while relying on the premium master turntable to provide the required 3D spatial grounding.

---

## 3. Computational Benchmark Analysis

Stress testing across complex visual anomalies (koi fish tattoos, unilateral cybernetics, ear piercings) yields clear efficiency curves:

* **Traditional 2D Sheet**: Generates frequent facial morphing and missing rear details, often requiring numerous re-rolls per scene to obtain acceptable continuity.
* **Hybrid Volumetric Conditioning (`@master_video` + `@turnaround_sheet`)**: Dramatically reduces re-roll frequency by providing continuous 3D volume. While producing the master turntable requires an initial upfront investment, it significantly lowers total credit expenditure across any multi-shot arc (20–100+ shots).
