# Module 03: Advanced Production Workflows

This module details high-complexity production scenarios: reskinning a consistent character across diverse wardrobe styles, choreographing multi-character scenes without feature bleeding, and maintaining continuity across 20–100+ shot sequences using iterative chaining.

---

## Workflow 3: Wardrobe Swapping with Persistent Identity

Cinematic storytelling requires characters to transition through different outfits (e.g., tactical suits, casual streetwear, formal evening wear, heavy winter gear) without mutating facial geometry or identifying bodily markings.

```text
[Conditioning: @master_video (Volume) + @turnaround_sheet (Facial Textures)]
                                │
                                ▼
                 [Decouple Geometry from Garments]
  • Lock facial topology, skull structure, hair, and tattoos to references
  • Overwrite clothing descriptions, fabrics, drape, and cut in prompt
                                │
                                ▼
                    [Target Scenario Injection]
  ├── Scenario A: Gala Silk Evening Gown
  ├── Scenario B: Distressed Streetwear Hoodie
  └── Scenario C: Heavy Thermal Arctic Parka
                                │
                                ▼
                     [Render in Video Engine]
  • Preserves exact facial identity and physical markings
  • Fully re-skins clothing, folds, fabric weight, and drape
```

### Execution Protocol:
1. **Maintain Dual Ingestion**: Never drop the static image reference during wardrobe swaps. Ingest **both** `@master_video` (for 3D volume and skull geometry) and `@turnaround_sheet` (for facial, ear, and hair micro-textures).
2. **Signal Decoupling**: Diffusion models naturally bind garment silhouettes to reference volumes. To overcome this, explicitly instruct the model to separate anatomical identity from wardrobe assets:
   * Explicitly bind facial features to the references.
   * Explicitly command the complete replacement of garments.
3. **Multi-Arc Wardrobe Rule**: For major scene arcs where a character spends 10+ shots in a new costume, render a dedicated `@turnaround_sheet_costumeB` to prevent lingering bleed from the original outfit.
4. **Prompt Template**:
   ```text
   Cinematic medium shot of the character from @master_video and @turnaround_sheet attending an upscale diplomatic reception. 
   
   Identity Anchor: Retain the identical facial bone structure, skin complexion, eye color, and right-cheekbone bird tattoo from @master_video and @turnaround_sheet. 
   
   Wardrobe Decoupling & Override: Replace original clothing completely. Disregard tactical jacket from references. The character now wears an elegant midnight-blue silk evening gown with halter neckline, tailored fit, and natural fabric drape. 
   
   Environment & Atmosphere: Ambient warm chandelier lighting, soft bokeh background with out-of-focus guests, cinematic film grain, locked facial identity.
   ```

---

## Workflow 4: Multi-Character Interaction Pipeline

Placing two distinct AI characters in the same shot frequently causes "character bleed"—where facial features, hairstyles, and clothing patterns blend into an incoherent hybrid.

```text
[Character A: @charA_video]           [Character B: @charB_video]
             │                                   │
             └─────────────────┬─────────────────┘
                               │
                               ▼
               [Dual Video Conditioning Input]
                               │
                               ▼
        [Spatial Partitioning & Choreography Prompt]
  • Hardcode Character A strictly to screen-left coordinates
  • Hardcode Character B strictly to screen-right coordinates
  • Define synchronized or interactive action (walking, dialog)
                               │
                               ▼
                   [Master Export & Audit]
  • Verify zero cross-pollination of costume textures or faces
```

### Execution Protocol:
1. **Dual Video Conditioning**: Upload `@charA_video` (Character 1 turntable) and `@charB_video` (Character 2 turntable).
2. **Spatial Partitioning Rule**: Always anchor characters to opposite halves of the frame using unambiguous positional language (Screen-Left vs Screen-Right).
3. **Explicit Actor-Action Binding**: Tie each wardrobe and behavioral attribute directly to the specific tag reference.
4. **Single-Video Interface Fallback**: If the platform only accepts one video conditioning file, upload `@charA_video` and inject Character B via a static 2D turnaround sheet (`@charB_sheet`), positioning Character A in dynamic foreground action and Character B in static profile.
5. **Prompt Template**:
   ```text
   Cinematic wide tracking shot featuring two characters walking forward in unison.
   
   Screen Left: Character strictly from @charA_video, wearing charcoal tactical armor, matching her height, facial structure, and hair from @charA_video. 
   
   Screen Right: Character strictly from @charB_video, wearing crimson wool trench coat, matching his facial features, skin tone, and beard from @charB_video. 
   
   Interaction & Movement: Both characters walk forward side by side matching pace, speaking quietly. Neither character crosses into the other's quadrant. Zero visual feature bleeding between characters. Photorealistic atmospheric lighting, 35mm lens.
   ```

---

## Workflow 5: Iterative Scene Chaining

When generating long narrative arcs (20–100+ shots), subtle compositional and lighting drifts can compound across consecutive scenes.

### The Chaining Rule:
If a scene begins to diverge from established narrative continuity:
1. Select the **last successfully approved production shot** (`@last_scene_frame`).
2. Feed three conditioning assets simultaneously:
   * `@master_video` (Foundational 360° Turntable for anatomical volume)
   * `@turnaround_sheet` (High-resolution Turnaround Sheet for feature sharpness)
   * `@last_scene_frame` (Approved still frame from Scene N-1)
3. Direct the engine:
   ```text
   Synthesize motion and core facial volume from @master_video and @turnaround_sheet, matching immediate scene lighting, color grade, and environmental context from @last_scene_frame.
   ```
