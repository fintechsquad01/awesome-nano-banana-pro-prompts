# Documentary Assets Directory

Store generated assets here, organized per episode:

```
assets/
├── EP-001_trojan_war/
│   ├── characters/
│   │   ├── char_achilles_v1.png
│   │   ├── char_achilles_v2.png
│   │   ├── char_hektor_v1.png
│   │   └── ...
│   ├── scenes/
│   │   ├── scene_trojan_walls_01.png
│   │   ├── scene_trojan_walls_02.png
│   │   └── ...
│   ├── clips/
│   │   ├── scene_trojan_walls_01_take1.mp4
│   │   ├── scene_trojan_walls_01_take2.mp4
│   │   └── ...
│   ├── overlays/
│   │   ├── map_troy_region.png
│   │   ├── title_card_act1.png
│   │   └── ...
│   └── audio/
│       ├── narration.mp3
│       ├── music_track.mp3
│       └── sfx/
├── EP-002_thermopylae/
│   └── ...
└── ...
```

## Naming Conventions

| Asset Type | Pattern | Example |
|-----------|---------|---------|
| Character sheet | `char_[name]_v[N].png` | `char_achilles_v1.png` |
| Scene image | `scene_[name]_[N].png` | `scene_trojan_walls_02.png` |
| Video clip | `scene_[name]_[N]_take[N].mp4` | `scene_trojan_walls_01_take2.mp4` |
| Map overlay | `map_[region].png` | `map_troy_region.png` |
| Title card | `title_card_[section].png` | `title_card_act1.png` |

## Notes

- **Do not commit large binary assets to git** — use Google Drive or cloud storage
- This directory is `.gitignore`d by default; only this README is tracked
- See `templates/nano_banana_pro_prompts.md` for image generation prompts
- See `templates/video_animation_prompts.md` for Runway/Veo prompts
