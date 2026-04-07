# Long-Form Historical Documentary YouTube Channel — Full Production Blueprint

## Executive Summary

This blueprint covers the complete production system for creating long-form historical documentaries (15–25 minutes) using Nano Banana Pro 2.5 for image generation, AI video tools (Runway/Veo) for animation, and automated assembly workflows. History documentaries command $10–15+ RPM in high-CPM advertising markets[cite:211][cite:208], and long-form content drives 50%+ of total YouTube watch time while enabling mid-roll ad monetization[cite:252][cite:255]. The system maintains human approval gates for quality control before publishing, integrating with your existing n8n/Claude architecture.

---

## Part 1 — Optimal Video Length & Structure

### YouTube Long-Form Performance Data (2025–2026)

| Metric | Finding |
|--------|---------|
| Ideal Length | 15–25 minutes for sustained engagement[cite:206][cite:212] |
| Minimum for Mid-Roll Ads | 8–10 minutes (YouTube policy)[cite:232] |
| Audience Retention Target | 30–45% for 15–30 min videos; 50%+ exceptional[cite:215] |
| Watch Time vs Completion | Long-form wins on watch time; Shorts win on completion rate[cite:252][cite:255] |
| RPM Premium | Long-form history: $10–15+ vs Shorts $2–5[cite:211][cite:208] |
| Binge Threshold | 40–60 min docs capture weekend binge sessions (50% of total views at this length)[cite:255] |

**Your recommended starting length: 18–22 minutes per episode** — long enough for 2–3 mid-roll ad breaks ($15–30 per video in CPM), short enough to maintain 35–50% retention curve[cite:232][cite:233][cite:252].

### Three-Act Story Structure for Historical Documentaries

This is the proven pacing framework used by top documentary channels on YouTube[cite:236][cite:245][cite:259]:

**Act I: Setup & Hook (0–5 minutes)**
- Cold open with a shocking visual or stat ("The Trojan War killed 100,000+ in a decade")
- Introduce main characters/factions (Greeks vs Trojans, key figures)
- Establish stakes and conflict in 2–3 sentences
- End with a promise: "But what really happened is far stranger…"

**Act II: Conflict & Rising Action (5–15 minutes)**
- Major battles, political intrigue, key turning points
- Insert retention hooks every 2–3 minutes: questions, teases, mini-reveals[cite:223]
- Show the "why" behind each decision (Agamemnon's hubris, Hektor's honor)
- Build tension with pacing: short cuts during battles, longer shots during strategy scenes
- Mid-roll ad break around 8–10 minutes (natural chapter break)

**Act III: Resolution & Legacy (15–end)**
- Final climax (fall of Troy, death of key figure)
- Aftermath and real-world impact
- "Here's why this matters today" — connect to modern parallels or archaeology
- End with a hook to next episode or related content

**Total pacing rule**: Cut every 5–10 seconds on average; no single shot longer than 15–20 seconds unless it's a major dramatic moment[cite:228][cite:231].

---

## Part 2 — Production Workflow: Nano Banana Pro + AI Video Animation

### Step 1: Script & Narrative Development

**Input**: Historical topic (e.g., "The Trojan War")
**Tool**: Claude 3.5 / GPT-4o via n8n

Prompt framework:
```
Create a 3-act narrative script for a 20-minute historical documentary:
- Act I: Hook (100 words), Setup (150 words)
- Act II: Rising Action with 4 retention hooks every 2–3 minutes (600 words)
- Act III: Climax & Legacy (200 words)
- Include [N] specific scenes with visual descriptions
- Add sarcastic/dry humor in narrator commentary
- Mark where mid-roll ads should break (at natural chapter ends)
```

**Output**:
- Full narration script with timing markers
- Scene-by-scene breakdown (e.g., "Trojan Walls Rising," "Hektor's Duel")
- Retention hook placement map
- Ad break recommendations

**Deliverable**: Save as `script_[topic].md` with timings and scene IDs.

### Step 2: Image Generation with Nano Banana Pro 2.5

**What is Nano Banana Pro?**
Google's Gemini 3 Pro image-to-image model: 4K-ready output, photorealistic historical scenes, strong character consistency when using reference images[cite:221][cite:230][cite:227].

**Character Sheet Generation** (Critical for Consistency)
For each major character, generate 2–3 reference images before animating:

```
Prompt Template (Nano Banana Pro):
"Full-body portrait of [Character Name], [Historical Period].
[Character description + period-accurate armor/clothing].
Realistic, cinematic lighting, 4K quality.
Style: Historical accuracy + dramatic lighting."
```

Examples:
- "Full-body portrait of Achilles, Bronze Age Greek.
  Muscular warrior, bronze armor, red plume helmet, spear.
  Realistic cinematic lighting, 4K."
- "Hektor of Troy, detailed bronze armor, crested helmet,
  confident stance, gate of Troy in background, 4K cinematic."

**Save reference images** as `char_[name]_v1.png`, `char_[name]_v2.png` for later use in video generation.

**Scene Image Generation**
For each scene in your script, generate 3–4 key images:

```
Scene: "Trojan Walls Rising"
- Image 1: "Wide shot of Troy's walls under construction,
  workers, scaffolding, bronze age setting, warm sunset light, 4K"
- Image 2: "Close-up of stone blocks being placed,
  detailed masonry, hands of workers, dust, 4K"
- Image 3: "Overhead view of entire Troy fortification,
  surrounding plain, Greek camps in distance, 4K"
```

**Generation Settings**:
- Resolution: 1920×1440 (16:9 for widescreen docs, or 1080×1920 for vertical if planning YouTube Shorts clips)
- Quality: "Maximum" (slower but worth it for archival-quality docs)
- Style: "Photorealistic" or "Cinematic" (avoid fantasy/cartoon styles)
- Output: Save as `scene_[name]_[number].png`

**Total images per 20-minute episode**:
- 5–8 character sheets (2–3 images each) = 10–24 images
- 20–25 scenes × 3–4 images per scene = 60–100 images
- **Total: ~80–120 images per episode** (manageable in 2–4 hours of batch generation)

**Nano Banana Pro Cost**: ~$0.01–0.05 per image with Google's API pricing[cite:221]. Budget: **$1–5 per episode for all images**.

### Step 3: Image-to-Video Animation (Runway / Veo)

Convert stills into short cinematic clips with subtle motion and camera work.

**Tool Comparison**:

| Tool | Best For | Output Length | Character Consistency | Cost |
|------|----------|----------------|----------------------|------|
| Runway Gen-3 | Image-to-video with motion control | Up to 4 seconds | Moderate (needs ref images)[cite:237][cite:207] | ~$0.10–0.20/clip |
| Google Veo 3.1 | High-fidelity video from images | 4–5 seconds | Very high with reference images[cite:240][cite:243] | ~$0.05–0.10/clip |
| Pika Labs | Fast, creative motion | 3–4 seconds | Good | ~$0.05–0.15/clip |

**Recommended workflow**: Use Veo 3.1 for character closeups and establishing shots; Runway Gen-3 for battle scenes and wide landscapes.

**Image-to-Video Prompts**:

```
Prompt (Veo / Runway):
"Camera: slow dolly-in on [character name in bronze armor].
Motion: character slowly turns, looks over shoulder.
Details: [specific environment]. Warm cinematic lighting.
Duration: 4 seconds. Subtle, realistic motion."

Example:
"Camera: slow dolly-in on Achilles in full bronze armor.
Motion: warrior slowly turns, grips spear, looks toward distant Troy.
Details: Greek camp at dawn, tents, morning mist. Golden hour lighting.
Duration: 4 seconds. Cinematic, no jerky motion."
```

**Best Practices for Consistency**:
1. Always provide a **reference image** from your character sheet to the video model
2. Keep prompts focused on **camera motion, not character action** (less drift)
3. Generate **2–3 takes** per scene; pick the best one
4. Limit motion to subtle changes: turns, tilts, breathing, weapon adjustments
5. Avoid dissolves or special effects at the clip level; do all transitions in editing[cite:243]

**Output**:
- Each scene generates 2–4 short clips (3–8 seconds each)
- Save as `scene_[name]_[number]_take[n].mp4`
- **Total per 20-min episode**: ~80–120 short video clips

**Cost**: ~$0.10–0.20 per clip × 100 clips = **$10–20 per episode for video generation**.

### Step 4: Storyboarding & Timeline Assembly

**Tool**: DaVinci Resolve (free), Adobe Premiere, or Runway's built-in editor.

**Process**:
1. Create a timeline matching your script's act structure (Act I, Act II, Act III)
2. Import all video clips, organize by scene folder
3. Build a rough cut:
   - 3–4 clips per scene
   - Cut every 5–10 seconds
   - Leave space for text overlays, maps, diagrams

**Clip Duration Rules**:
- Dialogue-heavy scenes: 5–8 seconds per clip (easier for viewers to absorb narration)
- Battle/action scenes: 3–5 seconds per clip (faster cuts = more energy)
- Establishing shots: 10–15 seconds (can hold longer)
- Close-ups: 3–5 seconds (keep moving)

**Timeline structure example** (for 20-minute Trojan War episode):
```
0:00–3:00 (Act I) — Hook + Setup
  - Opening logo/title card (5 sec)
  - Shocking stat with dramatic image (10 sec)
  - Character intro montage: Greek leaders (30 sec)
  - Character intro: Trojans (30 sec)
  - Conflict setup (60 sec)
  - Promise/tease to Act II (10 sec)

3:00–15:00 (Act II) — Rising Action + First Mid-Roll Ad
  - Scene 1: Trojan War begins (2:00)
  - [AD BREAK 1 - 8:00 into video]
  - Scene 2: First battles (3:00)
  - Scene 3: Greek strategy (2:00)
  - [AD BREAK 2 - auto-inserted at 14:00]
  - Scene 4: Hektor rises to power (2:00)

15:00–20:00 (Act III) — Climax & Resolution
  - Scene 5: Final confrontation (2:00)
  - Scene 6: Fall of Troy (2:00)
  - Scene 7: Aftermath & legacy (1:00)
  - Outro + subscribe CTA (0:30)

[AD BREAK 3 at 18:00]
```

**Overlay & Enhancement Layers**:
1. **Maps**: Pan/zoom over maps showing troop movements, city locations
2. **Text overlays**: Dates, character names, key stats (pop in/out on beat)
3. **Diagrams**: Tactical formations, family trees, timelines (simple animated reveals)
4. **Chapter markers**: "Act I: The Setup" — fade in/fade out at section breaks
5. **Lower-third graphics**: "Hektor — Prince of Troy" when introducing characters

---

## Part 3 — Brand Identity & Visual Style

### Color Palette

| Element | Hex | Use |
|---------|-----|-----|
| Gold/Warm | #D4AF37 | Armor, royal figures, key reveals |
| Deep Bronze | #3C3C30 | Backgrounds, armor shadows |
| Burnt Orange | #8B4513 | Fire, clay, earth |
| Steel Blue | #2C3E50 | Water, night scenes, armor |
| Cream/Parchment | #F5E6D3 | Text overlays, title cards |
| Crimson | #A7394F | Blood, danger, emphasized moments |

### Typography

- **Titles & Headers**: Serif font (e.g., Garamond, Crimson Text) — authoritative, historical feel
- **Body Text & Captions**: Clean sans-serif (e.g., Inter, Roboto) — readable at any size
- **Shocking Stats**: Bold, large, all-caps, gold or crimson color
- **Character Names**: Serif, smaller, cream/parchment background

### Opening Sequence (3–5 seconds, non-negotiable)

- Logo animation: Your channel name appears with a subtle film strip or scroll reveal
- Background: Cinematic historical scene (burning Troy, or landscape matching episode)
- Text overlay: Episode title + hook quote
- Sound: Dramatic sting (French horn, war drum)

**Example**:
- [Channel logo fades in over burning Troy gates]
- [Text appears]: "THE TROJAN WAR: What Really Happened"
- [Smaller text]: "The evidence rewrites everything…"
- [Sting plays]
- [Fade to black, narrator begins]

### Closing Sequence (2–3 seconds)

- Channel logo + subscribe button graphic
- "Next episode: [Teaser]"
- Sound: Satisfying resolution (resolved chord, fade to silence)
- **Always the same format** — brand consistency compounds over time[cite:259]

### Transitions

- **Standard cut**: Hard cut on narrator beat or action moment
- **Chapter break**: Fade to black (0.5 sec) + title card (1 sec) + fade in
- **Map pan**: Smooth 2–3 second pan/zoom from wide to specific location
- **Scroll reveal**: Image "unrolls" like ancient papyrus (old-world aesthetic)
- **Torch flicker**: Brief light flicker before/after major moments (subtle, not overused)

Avoid: Star wipes, spinning text, dissolves (feel cheap). Aim for film-documentary aesthetic[cite:228][cite:231].

---

## Part 4 — Monetization & Mid-Roll Ad Placement

### YouTube Monetization Requirements (2026)

- Minimum length: 8 minutes for mid-roll ads[cite:232]
- Mid-roll ad placement: One every 4–8 minutes for 20-minute videos[cite:232][cite:233]
- Optimal for retention: Place at **natural chapter breaks**, not mid-scene
- Revenue: Typically $15–25 per 1,000 views for historical/educational content in CPM markets[cite:208][cite:211]

### Sample 20-Minute Episode Ad Placement

```
0:00–0:03 — Logo/Intro
0:03–1:00 — Shocking stat hook
1:00–8:00 — Act I & II setup (5 min of content)
[MID-ROLL AD #1 — ~3–5 ads, 20–30 sec total]

8:00–14:00 — Act II middle (6 min of content)
[MID-ROLL AD #2]

14:00–18:00 — Act II climax (4 min of content)
[MID-ROLL AD #3]

18:00–20:00 — Act III resolution + outro
[POST-ROLL AD]
```

**Expected revenue** (rough estimate):
- 100K views × $0.015–0.025 CPM = $1,500–2,500 per video
- Plus brand deals in history niche: $500–3,000 depending on channel size[cite:208]
- **Long-form history is highly profitable once you hit 100K+ regular viewers**[cite:208]

---

## Part 5 — Integration with n8n / Claude Code Stack

### Module 1: Idea & Script Generation

**Trigger**: Daily schedule or manual approval

**Workflow**:
1. n8n node: Fetch trending history topics (Google Trends, Reddit r/History, Historical subreddits)
2. Claude node: Score topics for virality + research depth
3. Claude node: Generate full 3-act script (1,500–2,000 words) with scene breakdown
4. Output: Script document → Google Sheet "Documentary Ideas Queue"

**Human gate**: Approve script before moving to image generation

### Module 2: Image & Video Generation

**Trigger**: Manual "Generate" click on approved script

**Workflow**:
1. Parse script into scenes (AI extracts scene list)
2. For each scene:
   - Call Nano Banana Pro API (via Replicate or direct) → generate 3–4 images
   - Download images, save to project folder
3. For each image:
   - Call Runway / Veo API → generate 4-second video clip
   - Download clip, save with scene ID
4. Output: All images + video clips in `assets/[episode_name]/`
5. Google Sheet: Log all asset IDs and generation costs

**Human gate**: Review all images/clips before assembly

### Module 3: Timeline Assembly & Video Composition

**Trigger**: Manual "Assemble" click after assets approved

**Workflow**:
1. Read scene list + clip IDs from database
2. Call FFmpeg (local or cloud) with a pre-built XML project file:
   - Arrange clips in timeline
   - Add transitions (hard cuts)
   - Overlay chapter titles, maps, text graphics
   - Burn-in closed captions (via Whisper transcription of narration)
3. Generate rough cut MP4 (2–3 quality passes)
4. Upload to YouTube as **unlisted draft**
5. Output: Video URL → Google Sheet for human review

**Human gate**: Watch unlisted video, approve/request revisions before publishing

### Module 4: Publishing & Analytics

**Trigger**: Manual "Publish" click after final review

**Workflow**:
1. Move video from unlisted → public
2. Auto-generate title, description, tags (Claude via script metadata)
3. Schedule upload time (optimal: 2–3 PM US ET, 8–9 PM UK)[cite:204]
4. Create YouTube card for next episode (auto-generated, manual approval)
5. Post to Twitter/Reddit with teaser thumbnail

**Tracking**: Store video ID, publish date, initial view count in database for later performance analysis

---

## Part 6 — Retention & Engagement Tactics

### Hook Placement (Every 2–3 Minutes)

Insert one of these every 180 seconds to keep attention curves high[cite:223]:

| Hook Type | Example | Placement |
|-----------|---------|-----------|
| Shocking Stat | "100,000 soldiers died in one year" | Delivered over dramatic image |
| Question | "But what if everything was a lie?" | Narrated, then dramatic pause |
| Teaser | "Later: you'll see how one arrow changes everything" | Quick text overlay + music sting |
| Visual Contrast | Quick cut to extreme close-up or wide shot | Sudden change in framing |
| Character Surprise | Introduce unexpected player or betrayal | "But Achilles had a secret…" |

### Cut Frequency for Pacing

- **Dialogue scenes**: 5–8 sec per clip (let viewers absorb narration)
- **Action/battle scenes**: 3–5 sec per clip (faster energy)
- **Establishing shots**: 10–15 sec (can hold longer)
- **Close-ups**: 3–5 sec (quick, punchy)
- **Overall average**: 5–8 seconds per cut

Faster cutting = higher energy but higher cognitive load. Slower cutting = easier to follow but risks losing engagement[cite:228][cite:231].

### Sound Design (Half the Battle)

- **Background ambience**: Distant battle drums, crackling fire, water, wind (very subtle, -20dB)
- **Foley effects**: Sword clashes, armor clinks, footsteps (only on key moments, not every step)
- **Narration**: Clear, warm, slightly deeper than natural pitch (adds authority)[cite:223]
- **Music**: Period-appropriate instrumental (strings, horns), rise and fall with tension[cite:223]
- **Silence**: 0.5–1 sec of silence before major reveals (creates anticipation)
- **Stings**: Single sharp sound (French horn, drum hit) on key stat reveals

**Rule**: You should never have more than 3 simultaneous audio layers (narration + music + 1 effect)[cite:223].

### Pattern Interrupts (Around 8–12 Minute Mark)

Retention curves dip predictably around the 8–12 minute mark in long-form video[cite:215][cite:223]. Combat this with:
- Sudden cut to extreme close-up
- Quick text reveal with shocking stat
- Music sting + dramatic pause
- "You won't believe what happens next"
- Abrupt scene change (e.g., from diplomacy to battle)

---

## Part 7 — Content Series Ideas (Quick Reference)

Your channel can rotate between these formats, all 18–22 minutes:

1. **"The Untold Story of [Event]"** — Single-episode deep dives (Troy, Thermopylae, Battle of Marathon)
2. **"[Era] Explained" series** — 5–8 episodes breaking down an entire period (Bronze Age collapse, Ottoman rise)
3. **"What Archaeology Proves"** — Compare historical record vs. modern evidence
4. **"Mistakes Historians Made"** — Debunk popular myths (Troy wasn't literally *that* place, etc.)
5. **"Comparison: [Culture A] vs [Culture B]"** — Military tactics, trade, daily life
6. **"The Real [Character]"** — Biography vs. myth (Cleopatra, Julius Caesar, Hannibal)

Each format works with the nano banana pro + Veo pipeline; just adjust scene emphasis[cite:259].

---

## Part 8 — Phased Execution Roadmap

### Phase 1: Setup & Single Episode (Weeks 1–3)

- [ ] Set up Nano Banana Pro API access (Google Cloud / Replicate)
- [ ] Set up Runway / Veo access
- [ ] Design brand identity (color palette, fonts, intro/outro)
- [ ] Test on **one complete episode** (Trojan War recommended as your reference video)
- [ ] Time the full production: image gen → video gen → assembly
- [ ] Refine timing estimates for future episodes

### Phase 2: Publish First 3 Episodes (Weeks 4–8)

- [ ] Script 3 episode ideas (history topics you're passionate about)
- [ ] Generate all assets for each
- [ ] Manually assemble and edit in DaVinci/Premiere
- [ ] Publish unlisted, get feedback from 5–10 trusted viewers
- [ ] Iterate on pacing, hook placement, sound design
- [ ] Publish publicly with full marketing push

### Phase 3: n8n Automation (Weeks 9–12)

- [ ] Build Module 1 workflows (script generation + idea approval)
- [ ] Build Module 2 workflows (image/video generation + cost tracking)
- [ ] Build Module 3 workflows (FFmpeg assembly + draft upload)
- [ ] Test end-to-end with one new episode
- [ ] Lock in approval gates (human always reviews before publish)

### Phase 4: Scaling & Optimization (Weeks 13+)

- [ ] Publish 1–2 new episodes per week
- [ ] A/B test: episode length (18 min vs. 22 min vs. 25 min)
- [ ] A/B test: ad placement density
- [ ] A/B test: narration tone (serious vs. dry sarcasm)
- [ ] Track retention curves, identify where viewers drop
- [ ] Refine hook placement based on real data
- [ ] Experiment with 40–60 min "binge" episodes on weekends

---

## Part 9 — Cost Breakdown (Per Episode)

| Component | Tool | Cost |
|-----------|------|------|
| Image generation (80–120 images) | Nano Banana Pro | $1–5 |
| Video clips (80–120 × 4-sec clips) | Runway/Veo | $10–20 |
| Narration/TTS (optional, if not recording yourself) | ElevenLabs | $5–10 |
| Music/SFX library | Epidemic Sound or Artlist | ~$0.50 (subscription amortized) |
| Assembly & editing (FFmpeg + manual tweaks) | Local / DaVinci Resolve | Free |
| **Total per episode** | | **$16–35** |

**Revenue potential**: 100K–500K views (realistic for new channel after 6 months) × $0.015–0.025 CPM = **$1,500–12,500 per episode**.
**Payback period**: 1–2 videos.
**Long-term**: History channels with 500K+ subscribers earn $10K–50K+ per month[cite:208][cite:211].

---

## Part 10 — Common Pitfalls & Mitigations

| Pitfall | Mitigation |
|---------|-----------|
| Stale information (archaeology updates, new evidence) | Always timestamp scripts; add "As of [date]" card in intro |
| AI video character drift (Achilles looks different each clip) | Generate and lock character sheets; provide ref images to every video prompt |
| Over-automation before winning formula found | Do Phase 2 manually first; only automate after testing |
| Retention drop at 8–12 min | Pre-plan pattern-interrupt moments; test with viewers |
| Monotonous narration | Use narrator with theatrical background; vary pace and tone |
| Sound design overpowering narration | Keep music/effects -20dB below dialogue; use silence strategically |
| Ad placement mid-action | Map out ad breaks during script writing; lock them before production |
| Insufficient fact-checking | Add peer-review step before publishing; run by a historian[cite:249] |

---

## Part 11 — Success Metrics to Track

After each episode, log:

- **View count** (24hr, 7-day, 30-day)
- **Average view duration** (in minutes and as % of video length)
- **Click-through rate** (CTR) on thumbnails
- **Audience retention curve** (identify drop-off points)
- **Engagement** (likes, comments, shares, subscribes)
- **CPM/RPM earned**
- **Traffic source** (suggested videos, search, direct, etc.)

**Goal targets** (reasonable after 3–6 months):
- 30–50% average retention curve
- 50%+ click-through rate on thumbnails
- 3–5% engagement rate (likes + comments / views)
- 10K–50K average views per new video
- $0.015–0.025 CPM (history niche standard)

---

## References & Tools

**Image Generation**:
- Nano Banana Pro 2.5: `ai.google.dev/gemini-api` or via Replicate API

**Video Animation**:
- Runway Gen-3: `runway.com`
- Google Veo 3.1: Via Google AI Labs or waitlist
- Pika Labs: `pika.art`

**Automation & Assembly**:
- n8n: `n8n.io` (self-hosted or cloud)
- FFmpeg: `ffmpeg.org` (free, open-source video composition)
- DaVinci Resolve: `blackmagicdesign.com` (free tier available)

**Narration & Audio**:
- ElevenLabs: `elevenlabs.io`
- Music: Epidemic Sound, Artlist, or Incompetech (Creative Commons)

**Analytics**:
- YouTube Studio native analytics
- VidIQ or TubeBuddy (optional, for competitive analysis)
