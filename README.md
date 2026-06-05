# Heel Turn — Story Data

Story content for the [Heel Turn](https://github.com/bkerly) Android app.

The app fetches `manifest.json` on launch, compares versions against its local cache, and downloads any new or updated story files. Built-in stories in the app serve as the offline fallback.

---

## Adding a new story

1. Create `stories/your_story_name.json` following the schema below
2. Add an entry to `manifest.json` with a new `id`, `title`, `file` path, and `version: 1`

The app will pick it up on next launch.

---

## Updating an existing story

1. Edit the story JSON file
2. Bump its `version` number in `manifest.json`

The app re-downloads any story whose manifest version is higher than its cached version.

---

## Story JSON schema

```json
{
  "id": "unique-kebab-case-id",
  "title": "Display Title",
  "subtitle": "One-line tagline",
  "description": "2-3 sentence description shown on the story select screen.",
  "accentColor": "FF4ADE80",
  "characters": [
    {
      "name": "Character Name",
      "description": "One or two sentences describing the character.",
      "stats": {
        "SkillName": 3,
        "AnotherSkill": -1
      },
      "imageName": "Filename.png"
    }
  ],
  "challenges": [
    {
      "prompt": "The full challenge text shown to the player. HOW DO YOU SOLVE IT?",
      "goal": "Short description of what a valid answer looks like.",
      "relevantSkill": "SkillName",
      "difficulty": 8
    }
  ]
}
```

**`accentColor`** — 8-digit ARGB hex string, no `#` or `0x` prefix. e.g. `"FF4ADE80"`.  
**`imageName`** — filename of a PNG in the app's `assets/` folder. Leave `""` for a letter placeholder.  
**`relevantSkill`** — must exactly match one of the keys in `stats` for each character.  
**`difficulty`** — the score threshold (idea + skill bonus + luck roll ≥ difficulty = success). Typical range 3–15.

---

## Stories

| File | Title | Challenges | Characters |
|------|-------|-----------|------------|
| `stories/animal_spy_squad.json` | Animal Spy Squad | 6 | 6 |
| `stories/bird_day_afternoon.json` | Bird Day Afternoon | 14 | 7 |
| `stories/cloud_puppy.json` | Cloud Puppy & Friends | 14 | 4 |
| `stories/huntrx.json` | Huntr/x | 14 | 5 |
| `stories/under_the_sea.json` | Under the Sea | 10 | 4 |
| `stories/champagne_supernova.json` | Champagne Supernova | 17 | 5 |
