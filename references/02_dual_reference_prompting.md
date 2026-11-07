# Module 02: Production Scene Assembly & Dual-Reference Prompting

Once foundational master assets (`@master_video` and `@turnaround_sheet`) pass QA, they are utilized concurrently as multimodal conditioning inputs to generate narrative scene shots.

```text
[Input Conditioning Assets]
  ├── @master_video (Master 360° MP4)
  └── @turnaround_sheet (High-Resolution Turnaround PNG)
            │
            ▼
[Prompt Construction Engine]
  ├── Primary Action & Narrative Environment
  ├── Explicit Tagging: "@master_video and @turnaround_sheet"
  ├── Anti-Rotation Motion Separation Clause
  └── Spatial Orientation Hard-Lock (Conditional)
            │
            ▼
[Video Generation Pass]
            │
            ▼
[Quality Inspection Gate]
  ├── Facial bone structure & tattoo edge inspection
  ├── Orientation Verification: Did unilateral features mirror?
  └── If defect detected: Inject negative prompt lock & re-roll
```

---

## 1. The Dual Ingestion Rule

Video diffusion engines benefit from two complementary data streams:
1. **The 360° Video Reference (`@master_video`)**: Provides temporal geometry, 3D volume, rotational lighting behavior, and anatomical mass.
2. **The Turnaround Sheet Image (`@turnaround_sheet`)**: Provides frozen high-frequency pixel clarity, fine textural lines (skin pores, tattoo borders, sharp edges).

### Operational Protocol:
* Upload **both** files into the generative video interface.
* Reference both assets directly in the prompt text using platform-native tagging syntax:
  ```text
  Character as depicted in @master_video and @turnaround_sheet ...
  ```
* **Single-Asset Interface Fallback**: If the platform restricts inputs to a single conditioning asset:
  * Prioritize `@master_video` for dynamic action or rotational camera moves.
  * Prioritize `@turnaround_sheet` for static dialogue close-ups.

---

## 2. Motion Separation: Preventing Turntable Rotation Leakage

Because the master reference video features a 360° spinning subject, generative video models risk inheriting rotational movement as a motion prior into scene shots.

### Anti-Rotation Clause:
In every production scene prompt, explicitly decouple the reference volume from the scene choreography:
```text
The character maintains natural posture and directional movement through the scene. Do NOT spin, rotate in place, or replicate turntable motion.
```

---

## 3. Spatial Orientation Hard-Locking (Conditional Application)

Diffusion algorithms are fundamentally invariant to horizontal reflections (mirror flips). Because the model cannot distinguish between a character's anatomical right and camera-relative right, unilateral features frequently mirror across shots.

### When to Apply:
* **Apply STRICTLY IF**: The character has unilateral features (e.g., an eyepatch, asymmetric mechanical limb, unilateral tattoo, or single-ear earring).
* **Omit IF**: The character's anatomy, hair, and wardrobe are symmetrical. Over-constraining symmetrical characters adds prompt noise that reduces adherence to other descriptors.

### Hard-Locking Template (For Asymmetrical Subjects):
```text
Anatomical spatial lock: Retain the bird tattoo strictly on the RIGHT cheekbone under the right eye; keep the left cheekbone completely clear of markings. Zero mirrored markings.
```

---

## 4. Master Production Prompt Template

```text
Cinematic [Shot Type: medium tracking shot / close-up] of the character from @master_video and @turnaround_sheet [Action: walking through a neon-lit rain-slicked alley]. 

Physical continuity locks: Retain exact facial bone structure, skin tone, and hair styling from @master_video. Textural details, clothing seams, and accessories match @turnaround_sheet. [Insert Spatial Lock if asymmetrical: Retain marking strictly on RIGHT side].

Motion & Staging: Character moves naturally forward. Do not spin or rotate in place. Camera tracks smoothly on a dolly at chest height.

Camera & Lighting: 35mm anamorphic lens, shallow depth of field, atmospheric lighting reflecting off wet pavement, cinematic color grade, 24fps.
```

---

## 5. Downstream Quality Inspection Gate

Never advance a generated shot into the final edit timeline without running this 3-point check:

1. **Sagittal Symmetry Audit**: If the character possesses unilateral features, did they flip? If flipped, add negative prompt locks (`"mirrored tattoo, flipped marking, inverted asymmetry"`) and re-roll.
2. **Textural Boundary Audit**: Did micro-tattoos or hair braids blur into skin smudges? If blurred, verify `@turnaround_sheet` parsing or re-render using a higher-fidelity model tier.
3. **Bone Structure Continuity**: Did jawline width or nose shape warp during head movements? If warping occurs, ensure the camera move in the scene prompt is not fighting the character's movement vector.
