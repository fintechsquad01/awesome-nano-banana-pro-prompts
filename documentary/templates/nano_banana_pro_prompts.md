# Nano Banana Pro 2.5 — Prompt Templates for Historical Documentaries

> Use these templates with the Nano Banana Pro API or Google AI Studio.
> Always generate at 4K / Maximum quality. Style: Photorealistic or Cinematic.

---

## Character Sheet Prompts

Generate 2–3 reference images per character **before** animating any scenes.
Save as: `char_[name]_v1.png`, `char_[name]_v2.png`

### Full-Body Portrait

```
Full-body portrait of [CHARACTER NAME], [HISTORICAL PERIOD].
[Physical description: build, height impression, skin tone, hair].
[Clothing/armor: period-accurate details, materials, colors].
[Pose: standing, battle-ready, seated, etc.].
Realistic, cinematic lighting, 4K quality.
Style: Historical accuracy + dramatic lighting.
```

**Example — Achilles**:
```
Full-body portrait of Achilles, Bronze Age Greek warrior.
Tall, muscular build, tanned skin, long dark hair tied back.
Bronze Dendra-type armor with boar-tusk helmet, red horsehair plume, round shield with gorgon emblem, ash spear.
Confident battle-ready stance, weight on front foot.
Realistic, cinematic lighting, 4K quality.
Style: Historical accuracy + dramatic lighting.
```

### Bust / Close-Up Portrait

```
Cinematic close-up portrait of [CHARACTER NAME], [HISTORICAL PERIOD].
[Facial features: age, expression, scars, beard, etc.].
[Head covering/helmet details].
Shallow depth of field, warm golden-hour side lighting, 4K.
Style: Documentary portrait, historically accurate.
```

### Character Turnaround (for animation consistency)

```
Character reference sheet of [CHARACTER NAME], [HISTORICAL PERIOD].
Front view, 3/4 view, and side profile on neutral background.
[Full clothing/armor description].
Clean lighting, no dramatic shadows, 4K.
Style: Character design reference, realistic proportions.
```

---

## Scene Prompts

Generate 3–4 images per scene. Save as: `scene_[name]_[number].png`

### Wide Establishing Shot

```
Wide cinematic shot of [LOCATION/SETTING], [HISTORICAL PERIOD].
[Landscape details: terrain, structures, weather, time of day].
[Activity: armies marching, ships arriving, city bustling, etc.].
Atmospheric perspective, epic scale, 4K.
Style: Historical epic, cinematic composition.
```

**Example — Troy Establishing Shot**:
```
Wide cinematic shot of the fortified city of Troy, Late Bronze Age.
Massive stone walls with square towers on a hill overlooking the Scamander plain.
Greek encampment of tents and beached black ships visible in the distance.
Golden hour, dust haze, warm Mediterranean light, 4K.
Style: Historical epic, cinematic composition.
```

### Battle Scene

```
Dynamic battle scene, [HISTORICAL PERIOD].
[Combatants: who vs whom, weapons, formations].
[Action: charge, melee, siege, cavalry, etc.].
[Environment: field, city walls, river crossing, etc.].
Motion blur on weapons, dust and debris, dramatic lighting, 4K.
Style: Cinematic war photography, gritty realism.
```

### Interior / Political Scene

```
Interior scene of [LOCATION], [HISTORICAL PERIOD].
[Room details: throne room, tent, temple, market, etc.].
[Characters present: who, what they're doing, expressions].
[Lighting: torchlight, oil lamps, window light, etc.].
Rich textures, warm tones, 4K.
Style: Historical drama, intimate cinematography.
```

### Close-Up Detail Shot

```
Extreme close-up of [OBJECT/DETAIL], [HISTORICAL PERIOD].
[Description: weapon, artifact, inscription, food, hands, etc.].
Shallow depth of field, macro-style detail, 4K.
Style: Documentary detail shot, museum-quality clarity.
```

### Map / Overhead View

```
Overhead bird's-eye view of [REGION/BATTLEFIELD], [HISTORICAL PERIOD].
[Geographic features: rivers, mountains, coastlines, roads].
[Military positions: camps, formations, fleet positions].
Painterly cartographic style with realistic terrain, 4K.
Style: Historical military map brought to life, cinematic aerial.
```

---

## Overlay & Graphics Prompts

### Aged Parchment Background (for text overlays)

```
Blank aged parchment texture, warm cream tone, subtle stains and worn edges.
No text, no writing. Clean center area for overlay use.
Soft warm lighting, 4K.
Style: Ancient document texture, authentic.
```

### Title Card Background

```
Dark cinematic background with subtle [PERIOD-APPROPRIATE] motif.
[Examples: Greek key pattern, Egyptian hieroglyphs, Roman laurels].
Dramatic rim lighting, deep shadows, space for centered text, 4K.
Style: Documentary title card, premium broadcast quality.
```

---

## Generation Settings Reference

| Parameter | Value |
|-----------|-------|
| Resolution | 1920x1080 (16:9) or 1080x1920 (9:16 for Shorts) |
| Quality | Maximum |
| Style | Photorealistic / Cinematic |
| Output format | PNG |
| Naming | `char_[name]_v[N].png` or `scene_[name]_[N].png` |

**Budget**: ~$0.01–0.05 per image. Total per episode: $1–5 for 80–120 images.
