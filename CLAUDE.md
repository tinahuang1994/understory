# Understory — Claude Code Rules

## What this is
An immersive web experience where users click on nature words from world languages and enter a cinematic visual + audio moment. Words are the UI. Feeling is the output.

**Project name: Understory** (was Earthtongue → Clearing → Understory, April 2026)

Art product first, climate product second. The argument: our language for nature is too small, and the world has been trying to hand us better instruments the whole time.

## Design principles
- Feels like art — not a dashboard, not a database, not a policy tool
- Every word must earn its place: real language, verified meaning, visceral imagery
- Depth over breadth — 12 strong words beats 20 weak ones
- No definitions on entry — users feel the word before they read about it

## Word integrity rule
- Every word must be verified in a credible linguistic source before inclusion
- Document the source for each word in the word database file
- Never include a word that cannot be verified — no matter how poetic it sounds
- Flag any word with uncertain attribution as ⚠️ in the word list

## Technical constraints
- Web-based, Vercel deployment (consistent with Tina's other projects)
- No Unreal Engine — too complex and expensive to host for a solo web project
- Three.js for generative visual scenes; pre-rendered video loops for sound-anchored imagery
- Keep bundle size manageable — lazy load each word's assets on click

## Stack
- Next.js + TypeScript
- Three.js (generative scenes)
- Web Audio API (sound)
- GSAP or Framer Motion (transitions)
- Vercel

## Content files
- `words/` — one file per word with: language, script, romanization, meaning, scene type, asset references, source citation
- `PRD.md` — product requirements and vision
- `design-brief.md` — full visual and emotional design language (updated April 2026)
- `scene-design-notes.md` — ⚠️ READ THIS before building any scene. Do's and don'ts learned from Komorebi. Covers photo setup, light shafts, text legibility, movement mistakes, timing.
- `word-field.html` — approved Word Field prototype (source of truth for entry + word field)
- `ui-spec.md` — visual design spec (to be created from word-field.html)

## Do not
- Use placeholder words — every word in the product must be verified
- Add UI chrome or navigation menus that distract from the word experience
- Make it look like a climate report or policy document
- Use the same visual treatment for every word — each word deserves its own scene logic
