# Understory

An immersive web experience where users encounter nature words from world languages and enter a cinematic visual and audio moment for each one.

**Words are the UI. Feeling is the output.**

## What it is

Understory is not an educational tool or a language app. It is closer to a gallery installation that lives on the web. Users click a word — from Japanese, Norwegian, Arabic, Māori, Korean, Irish, and others — and enter a full-screen cinematic scene that lets them *feel* what the word means, not read a definition.

The argument: our language for nature is too small. The world has been trying to hand us better instruments the whole time.

## How to run locally

```bash
npm install
npm run dev
```

Opens at http://localhost:3000

Or to preview the current prototype HTML files:

```bash
cd /Users/tinahuang/Desktop/understory
python3 -m http.server 8000
```

Then open:
- http://localhost:8000/ — entry / word field
- http://localhost:8000/scenes/komorebi.html — Komorebi scene

## Deploy

Deployed on Vercel. Push to main triggers a production deploy.

## Stack

- Next.js + TypeScript
- Three.js (generative visual scenes per word)
- Web Audio API (ambient sound + scene-specific sound, no external files)
- GSAP (transitions)
- Vercel

## Project structure

```
/scenes             — One HTML prototype per word (source of truth until Next.js migration)
  komorebi.html     — ✅ Approved
/assets             — Photos and images used in scenes
  komorebi.jpg      — Source photo for Komorebi scene
word-field.html     — ✅ Approved entry / word field prototype
PRD.md              — Product requirements and full vision
design-brief.md     — Visual and emotional design language (source of truth)
CLAUDE.md           — Rules for Claude Code in this project
```

## The 12 words

| Word | Language | Concept |
|------|----------|---------|
| 木漏れ日 Komorebi | Japanese | Sunlight filtering through leaves |
| Waldeinsamkeit | German | Solitude in a forest — Romantic melancholy |
| Friluftsliv | Norwegian | Open-air life; being fully present outdoors |
| Тоска Toska | Russian | Aching longing with no object |
| غيث Ghayth | Arabic | Rain that brings relief in an arid landscape |
| ऋतु Rtu | Sanskrit | Season as cosmic cyclic order |
| Ubuntu | Zulu | I am because we are — ecological interdependence |
| Pachamama | Quechua | Earth Mother; the living, animate earth |
| Wiikwegamaa | Ojibwe | Relational word for bay/water body |
| Whatungarongaro | Māori | Gradual fading — people disappear, land endures |
| 숲멍 Soop-meong | Korean | Sitting in forest, staring with an empty mind |
| Ceobhrán | Irish | Light drizzle-mist; the threshold between rain and air |

## Word integrity rule

Every word is verified in a primary linguistic source. Sources documented in `/words/`. Never add a word that cannot be sourced.
