# Volumetric Character Consistency

Deterministic standard operating procedure for maintaining strict facial, anatomical, and wardrobe continuity across 20 to 100+ AI-generated video shots. Replaces error-prone 2D static character sheets with a volumetric 360° turntable video conditioning workflow paired with an informational turnaround sheet.

---

### 🪄 The Magic Prompt

Copy and paste this into any AI coding app (Cursor, Windsurf, Claude Code, Grok, Kimi, Reasonix, Antigravity):

```markdown
@agent Install the Volumetric Character Consistency skill from: https://github.com/markkirby125/kirby-volumetric-character-consistency
1. Read `SKILL.md` and `references/` from the repository.
2. Place into your environment's skills/rules directory preserving the dispatcher structure.
3. Confirm when installation is complete.
```

---

## 🏛️ Architectural Overview

1. **Phase 1: Base Character Synthesis** via GPT Image 2.5 Sunburst (Higgsfield).
2. **Phase 2: Split-Frame 16:9 Canvas** (Full Body Left / Facial Close-Up Right) to maximize pixel density per facial coordinate.
3. **Phase 3: Informational Turnaround Sheet** (Front, Profile, Back) documenting non-frontal micro-markings.
4. **Phase 4: Volumetric 360° Turntable Video** rendered with locked-off camera in Cance 2.5 or Kling 4.
5. **Dual Ingestion Conditioning**: Feeding `@master_video` + `@turnaround_sheet` with conditional spatial orientation locks into production scene prompts.
6. **Wardrobe Decoupling & Multi-Character Isolation**: Techniques for reskinning garments and choreographing multiple distinct characters without facial drift or cross-feature bleed.

See [`references/00_dispatcher.md`](references/00_dispatcher.md) for complete workflows.
