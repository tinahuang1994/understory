# PRD: Understory

## Why "Understory"

Understory is the ecological layer beneath the forest canopy — where things grow in the shadow of what is visible above. It is present, alive, and mostly unseen. That is also what this project is about: the layer of feeling beneath what our language can reach. The word "under" + "story" names exactly the gap the product lives in — the stories we carry about nature that we do not have words for.

Both meanings point at the same thing: something real, significant, and just below the surface.

## Vision

Our language for nature is thin. Not because nature is simple — because the words we have do not reach far enough. Most people feel more about a forest at dusk, a sudden rain, the moon on water, than they know how to say. The gap between what nature does to us and what we are able to describe is the real problem. It is why we talk about nature in numbers, or in clichés, or not at all.

Other languages have gotten closer. Scattered across Japanese, Arabic, Sanskrit, Ojibwe, Māori, Quechua, Zulu, Norwegian, Irish, and others are small, specific words for specific relationships between people and the natural world — words English has no room for. These words are proof. Proof that someone, somewhere, stood where we are standing and found a way to name it. They do not solve the gap. But they make it visible.

Understory is built around those words. A user encounters one. They click it. They enter a short cinematic moment — visual and sonic — that tries to take them to the place the word is pointing at. The word names it; the scene lets them feel it. The argument is not "here is a cool word." The argument is: *our instrument for describing nature is too small, and the world has been trying to hand us better instruments the whole time.*

## Emotional Direction (Creative North Star)

The product must make a user feel three things, in this order:

1. **That there is a gap.** Between what nature does to them and what they can say about it. A quiet recognition: *I have felt this, and I have never had a word for it.*
2. **That they are not alone in that gap.** Other cultures have stood here. The words are evidence.
3. **That the gap can be crossed — but not with language.** The scene is where the crossing happens. Sound and image do what the word cannot.

**Tone:** Romantic in the 19th-century sense — seized by something real and large. Not sentimental. Not wellness. Closer to a nature documentary's silent minute than to a meditation app. Closer to a gallery installation than to a website.

**What this is not:**
- Not an educational tool
- Not a language-learning app
- Not a meditation or wellness product
- Not a nature magazine
- Not a data visualization
- Not a travel product

The product is an art piece that lives on the web. It happens to contain twelve real words from nine real languages. Its purpose is not to teach those words. Its purpose is to use them as doors.

## Problem

- Most people feel more about nature than they can articulate, and that gap makes nature feel abstract or private — not shared.
- English (and the dominant register of most world languages in their modern form) has pushed out specific ecological vocabulary in favor of general or technical terms. The loss is cumulative and unnoticed.
- Existing projects that touch this space sit in one of two modes: academic databases of "untranslatable words" (linguistic curiosity, no felt experience), or immersive nature installations (sensory, but without specificity or language). Nobody has put the two together online.

## Target Users

1. **People who feel strongly about nature but distrust the usual vocabulary for it.** Readers, walkers, artists, people who have been moved by a forest or a sea and not known what to do with that. The core audience.
2. **People curious about language and other cultures.** The linguistic-diversity angle is a real draw for a smaller, adjacent audience.
3. **Tina herself — as a showcase of the product as art, not as a tool.** The product should read to a designer, an artist, or a writer as a serious piece of work. Technical audiences are welcome but are not the target.

## Three Must-Haves

1. **Word as portal.** A word, encountered in its original script, is the entire UI. No menus, no preambles, no taxonomy. Clicking is the only interaction that matters.
2. **Sensory crossing.** Each word opens into a full-screen scene that is visual and sonic. The scene is not decoration; it is the product. The word was the door.
3. **Feels like art.** A designer or a gallerist should take it seriously. It is aesthetically and emotionally disciplined — not busy, not ornamented, not informational.

## Content Strategy: Words

### Principles
- All words must be **real and verifiable** — no invented words, no misattributions. Fact-check each one with a native speaker or a reputable source before including.
- Coverage must be **genuinely global** — not just European languages. Include African, Indigenous, Asian, Middle Eastern, South Asian, Pacific language families.
- Words should describe **specific relationships with the natural world** — weather, light, water, earth, forest, season, presence — not generic emotions. The specificity is the point.
- Twelve words at launch. Depth over breadth. A gallery, not a dictionary.

### Candidate sources for word curation
- **Lomas Positive Lexicography** (drtimlomas.com) — 600+ untranslatable words, cross-referenceable for nature words.
- **Robin Wall Kimmerer's work** on Potawatomi and Ojibwe grammar as an ecological worldview.
- **Tim Ingold's** anthropological work on environment, perception, and language.
- **Academic papers in ecolinguistics** (the field studying language–environment relationships).
- Direct consultation with linguists or native-speaker communities where possible.

### Confirmed word list (12 of 12, as of April 2026)

| Word | Language / Script | Meaning | Viz approach | Confidence | Notes |
|------|------------------|---------|--------------|------------|-------|
| **Komorebi** | Japanese 木漏れ日 | Sunlight filtering through leaves | Three.js generative — leaf canopy + god rays | ✅ HIGH | Start here for first build |
| **Waldeinsamkeit** | German | Forest solitude — Romantic melancholy, not eco-wellness | Three.js + FogExp2, cool tones, no warmth | ✅ HIGH | Frame as 19th-c Romantic sublime, not wellness |
| **Friluftsliv** | Norwegian | Open-air life; being fully present outdoors | Three.js sky dome + wind-grass vertex shader | ✅ HIGH | Challenge: restraint over prettiness |
| **Toska** | Russian | Aching longing with no object (Nabokov) | Three.js steppe + darkening sky + stars | 🟡 MEDIUM | Risk: reads as "pretty night" not aching emptiness |
| **Ghayth** | Arabic غيث | Rain that brings relief in an arid landscape | Canvas + WebGL hybrid — cracked earth + rain particles | ✅ HIGH | Most complex emotional arc; build after core words |
| **Rtu** | Sanskrit ऋतु | Season as cosmic cyclic order | Three.js particle mandala cycling 4 states | ✅ HIGH | Risk: screensaver aesthetic; sound design essential |
| **Ubuntu** | Zulu | "I am because we are" — ecological interdependence (scholarly extension) | Three.js root-network graph, 50–100 nodes, light pulses | 🟡 MEDIUM | Keep non-anthropomorphic; attribute eco extension to scholars |
| **Pachamama** | Quechua | Earth Mother; the living, animate earth | Three.js displacement shader — terrain that breathes | ✅ HIGH | Hard to execute. Build last. Fallback: subtle central mound |
| **Wiikwegamaa** | Ojibwe | Relational word for bay/water body | THREE.Water library + dawn light + mist | 🟡 MEDIUM | Attribute to Kimmerer; camera *with* the water, not observing it |
| **Whatungarongaro** | Māori | Gradual fading until imperceptible — "people disappear, land endures" | Three.js + fog — figure walks into mist, dissolves | ✅ HIGH | Source: Te Aka Māori Dictionary (Moorfield, Massey University) |
| **숲멍 Soop-meong** | Korean | Sitting in forest, staring blankly with empty mind | Static atmospheric scene — figure from behind, soft forest | 🟡 MEDIUM-HIGH | Source: NIKL contemporary vocabulary + Forest Welfare Institute |
| **Ceobhrán** | Irish | Light drizzle-mist — the threshold between rain and air | Three.js mist particles + soft grey light | ✅ HIGH | Replaces fabricated Clagarnach; verify in Foclóir Gaeilge-Béarla |

### All 12 words confirmed ✅

### Cut words
- **Mångata** (Swedish, moonlight road on water) — cut for geographic diversity; strong word, possible future addition
- **Liget** (Ilongot) — single-source ethnographic documentation; too academic for general audience
- **Yūgen** (Japanese) — cut for geographic diversity (Japanese already covered by Komorebi)
- **Sumak Kawsay** (Quechua) — geographic duplicate of Pachamama region

## Experience Design Concept

The product is three screens. The first two are a single continuous reveal (see Design Brief, Screen 1/2).

- **Entry.** Darkness. The title surfaces. A single line names the argument: that our language for nature is thin, and that other languages have gotten closer. The title dissolves; twelve words breathe out of the darkness, scattered, at rest.
- **Word field.** The twelve words float in a dark field. One is softly lit at any time. Hovering moves the light. Clicking enters the word.
- **Scene.** Full-bleed visual + sound. The word is the only text on screen, in the lower third — original script, romanization, and one felt line (not a definition). The scene lasts as long as the user stays. Exit is barely visible; Escape works.

The entire product is navigable by attention alone. No menus, no tabs, no categorical organization. The twelve words are not a list — they are a constellation.

## Technical Approach (To Be Decided)

### Key decision: rendering approach
| Option | Quality | Complexity | Hosting cost |
|--------|---------|------------|-------------|
| Pre-rendered video loops + Web Audio API | High (cinematic) | Low | Low |
| Three.js / WebGL generative | High (interactive) | Medium | Low |
| Hybrid (video for some words, generative for others) | Highest | Medium-High | Low |
| Unreal Engine Pixel Streaming | Very high | Very high | High (server required) |

**Working recommendation:** Hybrid approach. Words with strong sound-anchored imagery (rain, water, wind) → pre-rendered video + real audio. Words with light/motion qualities (komorebi, mångata) → Three.js generative. Unreal Engine is not recommended for a web product — server cost and complexity are prohibitive for a solo project.

### Stack (proposed, subject to confirmation)
- Next.js
- Three.js for generative scenes
- Web Audio API for sound, with a minimal global mute control (bottom-right, near-invisible)
- Framer Motion or GSAP for transitions
- Vercel for deployment

## Sound

Sound is not optional. Nature enters this product through sound more than through image.

- **Entry / word field:** a single continuous ambient bed — very distant, very quiet, non-melodic. Not a nature-sound collage. One element only: distant air, or a low earth-drone, or very occasional water. The room should feel like it has weather.
- **Scene:** the scene's own sound, full and specific. Rain on earth for Ghayth. Leaves and wind for Komorebi. Mist-silence for Ceobhrán. This is where sound carries most of the emotional weight.
- **Never:** music with melody or beat. No spa cues. No swells.
- **Control:** one small sound toggle, always in the same corner, always dim. No volume slider. On or off.

## Open Questions

1. **Product name.** Confirmed: **Understory**.
2. **Word count at launch.** 12 is the current commitment. Keep.
3. **Sound sourcing.** Original recordings preferred. Licensed library as fallback. AI-generated ambient is acceptable for the entry bed but not for scenes.
4. **UI language.** English only at launch. Translations of the one-line felt descriptions are a future consideration, not a launch concern.
5. **Re-entry behavior.** When a user exits a scene, how does the word field come back — identical to first load, or softer? (Recommend: softer, no title reveal on re-entry.)
