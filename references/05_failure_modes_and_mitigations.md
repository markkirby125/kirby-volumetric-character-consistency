# Module 05: Failure Modes & Mitigations

This module catalogs the four primary failure modes encountered in generative video pipelines and prescribes exact, actionable countermeasures.

---

## 1. The Dirty Turntable QA Gate

* **Symptom**: In production scenes, the character's facial features warp, eye size shifts, or tattoos disintegrate whenever the head turns.
* **Root Cause**: The foundational 360° turntable reference (`@master_video`) had micro-flaws (e.g., an eye subtly shifting shape or a tattoo fading as the head passed the 180° profile). Because the video model treats `@master_video` as its ground-truth spatial geometry, any defect in the reference multiplies across every production shot.
* **Authoritative QA Protocol (Frame-by-Frame Scrub)**:
  1. Never approve a turntable video that is merely "almost good enough."
  2. Perform a mandatory frame-by-frame scrub of `@master_video` at 0.5x speed or step-by-step prior to writing scene prompts.
  3. **Inspection Checklist**:
     * [ ] Jawline, nose bridge, and cheekbone contours remain 100% rigid throughout the full 360° rotation.
     * [ ] All facial tattoos, scars, and ear markings maintain consistent dimensions and textural sharpness across all rotational angles.
     * [ ] Zero lateral or sagittal flipping of unilateral features occurs during the turn.
     * [ ] The synthetic camera remains strictly stationary (no zooming, dollying, or wobbly horizon).
  4. **Strict Verdict**: If ANY distortion is detected, discard immediately and re-roll the turntable pass.

---

## 2. Kinetic Camera Drift in Turntable Generation

* **Symptom**: During scene generation, the character appears distorted, perspective is warped, or the camera exhibits unintended orbital rotation.
* **Root Cause**: The camera prompt during the turntable generation pass was insufficiently locked, allowing the camera to zoom, dolly, or pan during rotation. The video model baked camera motion into the character's volumetric coordinates.
* **Mitigation Protocol**:
  * Enforce strict kinetic negative and positive constraints in the turntable prompt:
    ```text
    Locked-off static camera, stationary tripod, zero camera movement, no zoom, no dolly, no panning, no camera rotation. The character rotates on a mechanical turntable in place. Neutral studio background.
    ```

---

## 3. The Unilateral Mirroring Glitch

* **Symptom**: An eyepatch, mechanical arm, or facial scar flips from the left side of the character to the right side between cuts.
* **Root Cause**: Generative diffusion models are largely invariant to horizontal reflections. Without explicit guidance, the model treats left and right as interchangeable visual concepts.
* **Mitigation Protocol**:
  1. **Anatomical Coordinate Lock**: Explicitly state the exact anatomical side in the prompt:
     `"Retain the mechanical prosthetic strictly on the LEFT arm; the RIGHT arm is natural organic skin."`
  2. **Negative Prompting**: Add explicit inverted coordinates to the negative prompt:
     `"prosthetic on right arm, mirrored cybernetics, flipped tattoo, bilateral marking"`
  3. **Visual Reference Anchor**: Pair `@master_video` with `@turnaround_sheet`, ensuring both profile views clearly show which side is clean and which side contains the marking.

---

## 4. Cumulative Scene Divergence (Style Drift)

* **Symptom**: By shot 15 or 20 of a sequence, the character gradually looks less like the original master design (e.g., skin tone shifts, nose shape changes slightly).
* **Root Cause**: Subtle compounding deviations occurring across successive generations when relying solely on text prompts for scene variations.
* **Mitigation Protocol**:
  1. Deploy **Triple Conditioning**: Ingest `@master_video`, `@turnaround_sheet`, and a static frame from the *most recently approved scene* (`@last_scene_frame`).
  2. Instruct the model:
     ```text
     Maintain exact facial anatomy and markings from @master_video and @turnaround_sheet, matching the direct lighting setup and subtle wardrobe wear from @last_scene_frame.
     ```
