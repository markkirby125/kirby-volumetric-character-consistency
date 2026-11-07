# Module 01: Volumetric Asset Generation Pipeline

This module outlines the 4-phase protocol for generating the master conditioning assets required prior to scripting or rendering production scene shots.

```text
[Phase 1: Base Character Creation]
  └── Tool: High-fidelity image engine (e.g., GPT Image 2.5 Sunburst via Higgsfield)
  └── Setting: Auto Aspect Ratio; high-detail concept prompt
            │
            ▼
[Phase 2: Split-Frame Start Canvas]
  ├── Layout: 16:9 Canvas
  ├── Left 50%: Full-body standing pose
  └── Right 50%: Extreme close-up full-face portrait
            │
            ▼
[Phase 3: Informational Turnaround Sheet]
  ├── Input: Phase 1 & 2 image references
  └── Output: Front, Profile, and Back view detailing hidden markings (@turnaround_sheet)
            │
            ▼
[Phase 4: 360° Turntable Video Synthesis]
  ├── Tool: Video conditioning engine (e.g., Cance 2.5, Kling 4)
  ├── Camera Invariant: Locked-off, static, no pan, no zoom, zero cuts
  ├── Prompt: Single 360-degree turntable rotation in place
  └── Output: Clean 5–10s video of character rotating 1 full turn (@master_video)
```

---

## Phase 1: Base Character Creation

1. **Tool Selection**: Use a high-fidelity image engine capable of realistic anatomical proportions (e.g., GPT Image 2.5 Sunburst).
   * *Selection Criterion*: The model must render clean, proportional human anatomy without facial warping or synthetic plastic skin.
2. **Configuration**:
   * Aspect Ratio: 1:1 or native 16:9 matching production delivery.
   * Style Anchors: Photorealistic, cinematic 35mm, or stylized 3D—maintain consistent aesthetic vocabulary across all subsequent prompts.
3. **Prompt Architecture & Neutral Baseline**:
   * Define foundational geometry: bone structure, eye shape, facial hair, distinct markings, skin tone.
   * **Neutral Expression Invariant**: The character MUST maintain a relaxed, neutral facial expression with closed mouth and resting eyes. Never generate a smiling, scowling, or expressive base reference—emotional expressions baked into the 3D skull volume will corrupt lip-sync and fight dramatic scene tone downstream.
   * *Anti-Slop Rule*: Avoid non-descriptive buzzwords like "hyperrealistic 8k masterpiece". Specify concrete physical parameters (e.g., "asymmetrical scar over left eyebrow, small geometric bird tattoo under right cheekbone, olive skin tone, defined cheekbones").

---

## Phase 2: Split-Frame Start Canvas (16:9)

The primary reason traditional reference sheets fail is pixel starvation. Placing 6 tiny poses on one canvas leaves fewer than 100x100 pixels for the face.

1. **Execution**:
   * Ingest the Phase 1 base character as an image reference.
   * Prompt for a **split-frame composition** on a 16:9 canvas:
     * **Left Half (50%)**: Full-body standing pose establishing wardrobe silhouette, posture, height, and footwear.
     * **Right Half (50%)**: Extreme frontal close-up portrait from collarbone up, capturing facial contours, iris texture, ear anatomy, and skin blemishes.
2. **Prompt Template**:
   ```text
   Split-screen composition on a 16:9 canvas. 
   Left side: full body standing portrait of the character in @reference1, neutral stance, clean studio backdrop. 
   Right side: extreme close-up portrait of the character's face, razor-sharp detail on facial features, eyes, and skin texture. Identical character, neutral lighting, matching colors.
   ```

---

## Phase 3: Informational Turnaround Sheet (Back & Profile Views)

Video models hallucinate when a character turns because front-facing sheets leave lateral and posterior anatomy undefined.

1. **Execution**:
   * Feed both Phase 1 and Phase 2 outputs as visual references.
   * Request a clean **3-angle informational character turnaround**:
     * **Front View**: Neutral baseline.
     * **Side Profile**: Nose bridge, ear structure, jawline angle.
     * **Back View**: Hairline, neck markings, rear jacket embroidery, and clothing seams.
2. **Output Registration**:
   * Save this asset as `@turnaround_sheet`. Verify that asymmetrical micro-details (e.g., ear piercings, neck tattoos, hair braids) are explicitly positioned and rendered crisply on both side and rear views.

---

## Phase 4: Volumetric 360° Turntable Video Synthesis

This is the central master reference asset that supplies rotational 3D volume to the video engine.

1. **Engine Selection**: Deploy an engine accepting video-to-video or image-to-video conditioning (e.g., Cance 2.5 or Kling 4).
2. **Input Conditioning & Canvas Centering**:
   * **Crucial Isolation Rule**: Never feed the raw uncropped Phase 2 split-frame directly into a video generator without isolation, or the model may attempt to animate two side-by-side subjects.
   * **Canvas Aspect-Ratio Parity**: Crop the left full-body vertical panel and place the subject centered onto a neutral dark-grey 16:9 canvas (if 16:9 is your production target). Feeding an unpadded vertical (9:16) crop into a landscape video generator forces auto-scaling, focal zooming, or horizon distortion.
   * Pair with `@turnaround_sheet` for posterior coordinate grounding.
3. **Aspect-Ratio Parity**:
   * Ensure the turntable video resolution and aspect ratio (e.g., 16:9 landscape 1080p) exactly matches the intended production scene aspect ratio.
4. **Strict Kinetic Invariants (Prompt Copy)**:
   ```text
   Locked-off static camera, zero camera movement, no zoom, no pan, no tilt, zero cuts, clean studio turntable character reference. The single character smoothly and slowly rotates 360 degrees once in place on a neutral dark grey studio backdrop. Constant rotational speed, stable lighting, zero morphing, pristine anatomical consistency throughout full rotation.
   ```
5. **Output Registration & QA Gate**:
   * Save the approved render as `@master_video`.
   * **Mandatory QA Gate**: Immediately subject `@master_video` to the authoritative frame-by-frame scrub protocol detailed in [`05_failure_modes_and_mitigations.md#1-the-dirty-turntable-qa-gate`](05_failure_modes_and_mitigations.md#1-the-dirty-turntable-qa-gate). Never advance to scene production with a flawed turntable.
