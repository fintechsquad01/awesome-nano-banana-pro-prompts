# Video Animation Prompt Templates — Runway Gen-3 / Google Veo 3.1

> Convert Nano Banana Pro stills into 3–8 second cinematic clips.
> Always provide the source image as a reference input.
> Save as: `scene_[name]_[number]_take[N].mp4`

---

## Tool Selection Guide

| Scene Type | Recommended Tool | Why |
|------------|-----------------|-----|
| Character close-ups | Veo 3.1 | Best consistency with ref images |
| Establishing/landscape | Veo 3.1 | High-fidelity environments |
| Battle / action | Runway Gen-3 | Better motion control |
| Wide panning shots | Runway Gen-3 | Superior camera path control |
| Detail / artifact shots | Either | Both handle subtle motion well |

---

## Camera Motion Templates

### Slow Dolly-In (Character Reveal)

```
Camera: Slow dolly-in toward [CHARACTER] in [SETTING].
Motion: Character breathes subtly, slight head turn toward camera.
Environment: [Background details]. [Lighting description].
Duration: 4 seconds. Smooth, cinematic motion. No jerky movement.
```

**Example**:
```
Camera: Slow dolly-in toward Achilles in full bronze armor at Greek camp.
Motion: Warrior breathes subtly, slowly grips spear tighter, slight head turn.
Environment: Morning mist, tents in background, dawn light breaking.
Duration: 4 seconds. Smooth, cinematic motion. No jerky movement.
```

### Slow Pan (Establishing Shot)

```
Camera: Slow horizontal pan across [LANDSCAPE/CITY].
Motion: Ambient environmental motion — flags waving, smoke rising, water flowing.
Environment: [Full scene description]. [Time of day, weather].
Duration: 5 seconds. Steady, smooth lateral movement.
```

### Tilt Up (Reveal / Scale)

```
Camera: Slow tilt up from [GROUND DETAIL] to reveal [LARGE STRUCTURE/SKY].
Motion: Minimal — dust particles, torch flicker, cloud drift.
Environment: [Setting details].
Duration: 4 seconds. Gradual reveal, building sense of scale.
```

### Static with Subtle Motion (Dialogue Scene)

```
Camera: Locked static shot of [CHARACTER/SCENE].
Motion: Subtle breathing, fabric sway, torch flicker, smoke drift.
Environment: [Interior/exterior details]. [Lighting].
Duration: 4 seconds. Near-still with lifelike micro-movements.
```

### Orbit / Arc (Dramatic Moment)

```
Camera: Slow arc around [CHARACTER/OBJECT], moving from [LEFT/RIGHT] side.
Motion: Subject remains still or turns slowly. Cape/hair catches wind.
Environment: [Setting]. Dramatic backlighting or rim light.
Duration: 4 seconds. Smooth orbital path, cinematic weight.
```

### Aerial / Crane Down (Battle Overview)

```
Camera: Slow crane down from high overhead to eye-level view of [BATTLEFIELD].
Motion: Troops moving in formation, dust clouds, distant siege equipment.
Environment: [Battlefield description]. [Weather, time of day].
Duration: 5 seconds. Smooth descent, epic sense of scale.
```

### Zoom to Detail (Artifact / Weapon)

```
Camera: Slow push-in from medium shot to extreme close-up on [OBJECT].
Motion: Minimal — light reflections, slight rotation of object.
Environment: [Context — table, hand holding it, museum case].
Duration: 3 seconds. Smooth zoom, shallow depth of field at end.
```

---

## Motion Intensity Guide

| Scene Type | Motion Level | Notes |
|------------|-------------|-------|
| Dialogue / political | Very subtle | Breathing, blinks, fabric sway only |
| Establishing shot | Low | Clouds, flags, distant figures |
| March / travel | Medium | Walking motion, horse movement |
| Battle close-up | Medium-high | Weapon swings, impacts — keep controlled |
| Battle wide shot | Medium | Formation movement, dust — avoid chaos |
| Climactic moment | Low-medium | Slow-mo feel, deliberate motion |

**Key rule**: Focus prompts on **camera motion**, not character action. Less character movement = less drift and distortion.

---

## Consistency Checklist

Before generating each clip:

- [ ] Source image attached as reference input
- [ ] Character clothing/armor matches character sheet
- [ ] Lighting direction consistent with scene (e.g., all golden-hour shots face same way)
- [ ] Camera motion type chosen from templates above
- [ ] Duration set (3–5 seconds standard)
- [ ] Generated 2–3 takes; best one selected
- [ ] No dissolves or transitions baked into clip (handle in editing)

---

## Cost Reference

| Tool | Cost per Clip | Clips per Episode | Episode Total |
|------|--------------|-------------------|---------------|
| Veo 3.1 | ~$0.05–0.10 | 50–60 | $2.50–6.00 |
| Runway Gen-3 | ~$0.10–0.20 | 40–60 | $4.00–12.00 |
| **Combined** | | **80–120** | **$10–20** |
