# Understory — Scene Creation SOP

Standard process for building a new word scene, start to finish.
Apply this for every word. Do not skip steps.

---

## Step 1: Word Research

Before touching any code or images, look up:

- **Etymology** — what do the component parts literally mean?
- **Origin** — who coined it, when, in what context (poem, philosophy, daily speech)?
- **The radical claim** — what is the most specific, surprising, or counterintuitive thing this word says that English doesn't? This is the thing the felt line must contain.
- **Emotional register** — is it warm or cold? Active or still? Melancholic or joyful? This drives the visual palette and audio.

Document this before writing the image prompt or felt line.

---

## Step 2: Image Prompt

Generate a prompt for ChatGPT / Gemini / Midjourney. Standard template:

```
[Scene description — what you see, from what angle]
[Lighting — time of day, quality of light, color temperature]
[Mood — one adjective that is NOT the word itself]
[Orientation: portrait, tall frame]
[Style: real photo feel, cinematic, no watermarks]
```

**Rules for a good Understory image:**
- Portrait orientation (~0.75 AR) whenever possible — UV crop math favors it
- No perfectly centered symmetric compositions — too AI, too generic
- The image should imply presence (a path, an edge, an angle) not just scenery
- Lighting must be specific — not "nice day." Dusk, overcast bright, low fog, backlit.
- If the image leads somewhere (a path, a horizon), it earns the word better than a static view

**Example prompts by word type:**
- Forest/interior words: low angle, looking up or forward into depth, canopy or mist
- Open/sky words: ground level, wide sky (50–60% of frame), implied movement
- Water words: surface or edge, not aerial
- Abstract/emotional words: find the one physical moment that embodies it

Review the generated image before building. Ask: does this image earn the word, or is it just pretty?

---

## Step 3: Felt Line

Write 3–4 options. Tina picks. Do not implement without her choice.

**Format:** The felt line should produce the feeling, not define the word.
One of these structures usually works:

- **Sensory → emotional:** *"The way sunlight breaks through leaves — as if the forest is trying to reach you."* (Komorebi)
- **Action → revelation:** *"To walk deep enough into the forest that the world behind you goes quiet — and realize the silence feels like coming home."* (Waldeinsamkeit)
- **Poetic rewrite of the actual definition:** *"To live in the open air in any weather, at any hour — not as a discipline, but as the natural state."* (Friluftsliv)

**Rules:**
- Must contain the radical claim from Step 1 — the thing that makes this word untranslatable
- One clean image OR one precise emotional beat — not both
- Never just a rephrasing of the dictionary definition
- Never generic enough to describe a different word
- Tina decides. Sub-agents may flag but never change the felt line unilaterally.

---

## Step 4: Build the Scene

1. Copy image to `/assets/[word].png` (or `.jpg`)
2. Create `/scenes/[word].html` — adapt from the nearest tonal sibling:
   - Forest/enclosed → use `waldeinsamkeit.html` as base
   - Open/sky → use `friluftsliv.html` as base
   - Light/upward → use `komorebi.html` as base
3. Adapt **visual layers** for the word's specific atmosphere:
   - Layer 0: Photo base — always film grain, always vignette
   - Layer 1: Primary atmosphere (glow, haze, or light source)
   - Layer 2: Movement layer (mist, cloud drift, shimmer)
   - Layer 3: Particles (warm golden vs cold grey vs neutral — match the word's temperature)
4. Set `CENTER_Y` by eye — what vertical slice of the image best shows the concept?
5. Adapt **audio** — key questions:
   - What frequency register? (Low/enclosed = forest. High/open = ridge/sky. Mid/moving = water.)
   - Does the word have silence in it? (Waldeinsamkeit does → silence gaps. Friluftsliv doesn't → wind is constant.)
   - What rare event marks the passage of time? (Creak, impact, distant call, drip?)
6. Set caption:
   - `.word` — the word itself, 56px, amber `#e8c97a` — always
   - `.lang` — language attribution, 16px italic uppercase — always
   - `.felt` — the chosen felt line — always
   - Non-Latin scripts: add `.script` in original characters (large amber) above `.word`
7. Wire into `index.html` sceneMap

**Always-on rules (never skip):**
- Film grain in the photo shader (breaks AI smoothness)
- `AdditiveBlending` on all light/particle layers
- Double `requestAnimationFrame` before veil lift
- Serve via `python3 -m http.server 8000` — never `file://`

---

## Step 5: Creative Director Review

Runs after the scene is built — before it is approved. This is mandatory, not optional.

Spin up a sub-agent with:
- The scene file path
- The word, etymology, and emotional register
- The three approved scenes as reference points (Komorebi, Waldeinsamkeit, Friluftsliv)
- Specific asks: image crop, visual layers, audio register, felt line accuracy

Run in background while presenting the scene to Tina for a first look.
When the review returns, present findings as options — not as implemented changes.
Tina decides what to act on.

**The felt line is always Tina's decision — sub-agents may flag, never change.**

---

## Step 6: Approve and Document

Once fixes are done:
- Update `/scene-design-notes.md` Approved Scenes table
- Add the word's image to `/assets/` with a clean filename
- Confirm the sceneMap entry in `index.html` is live

---

## Audio Distinctiveness Rule

Every scene must be sonically distinct from (a) the word field ambient and (b) every other built scene. Before finalising audio, run this check:

**Word field baseline:** wind drone + low distant air. Any scene that sounds like "more wind" is not distinct enough.

**Current sound fingerprints (do not duplicate):**
| Scene | Defining sonic character |
|---|---|
| Word field | Twin sines 41/55 Hz + 420 Hz LP noise |
| Komorebi | 2400 Hz leaf rustle + bird chirps — high, warm, organic |
| Waldeinsamkeit | Dual sub-bass beat 44/44.7 Hz + wind surges + minor chord + creaks + rare deep impact |
| Friluftsliv | 2200 Hz grass rustle + 880 Hz sky tone sine |
| Toska | 220 Hz triangle string + 330 Hz fifth + 600 Hz BP room hiss + crow (rare) |
| Ghayth | 58 Hz drone + 350 Hz LP wind + 1200 Hz BP rain hiss + rolling thunder 80-130 Hz (rare) |
| Soop-meong | 72 Hz + 250 Hz LP pine wind + 3500 Hz BP pine sibilance (leads) + branch settle (rare) |
| Ceobhrán | 65 Hz + 220 Hz LP wind + 1600-4000 Hz continuous mist hiss + rare stone drops HP 1800-2400 Hz |
| Wiikwegamaa | 68 Hz drone + 2800 Hz HP water surface hiss + loon call sweep 400-640 Hz (rare, echo) |
| Pachamama | 62 Hz drone + 140 Hz LP mountain rumble + 950 Hz BP stone resonance + mountain echo (rare) |

**Rule:** Each new scene needs at least one frequency range or event type that no other scene uses. Identify it before building. If you can't name what makes this scene's sound unique, the design isn't done yet.

## Audio Quick Reference

| Register | Cutoff / Freq | When to use |
|---|---|---|
| Sub-bass drone (55–80 Hz) | Felt, not heard | Every scene — the earth |
| Forest wind (180–220 Hz LP) | Dark, enclosed | Forest / interior words |
| Open wind (500–700 Hz LP) | Bright, expansive | Sky / open words |
| Grass/leaves (2000–2500 Hz BP) | Papery, quick | Ground-level scenes |
| Sky tone (800–1000 Hz sine) | Altitude, height | Open / elevated scenes |
| Rare event (every 14–60s) | Breaks stillness | Every scene needs one |
| Silence gap (wind drops to 2%) | The word itself | When the word IS silence |

---

## Felt Line Archive

| Word | Language | Felt line |
|---|---|---|
| Komorebi | Japanese | The way sunlight breaks through leaves — as if the forest is trying to reach you. |
| Waldeinsamkeit | German | To walk deep enough into the forest that the world behind you goes quiet — and realize the silence feels like coming home. |
| Friluftsliv | Norwegian | To live in the open air in any weather, at any hour — not as a discipline, but as the natural state. |
| Toska | Russian | A longing with nothing to long for. The ache that has no address. |
| Ghayth | Arabic | In the Arabian desert, rain is not weather. It is rescue. غيث is the word for when it finally comes. |
| Soop-meong | Korean | Sitting in the forest until your mind goes quiet enough to disappear into it. |
| Ceobhrán | Irish | Not rain, not fog. The air between them — when the world turns silver and you stop minding getting wet. |
| Wiikwegamaa | Ojibwe | The bay does not simply hold water. In Anishinaabe, the water is your kin — and standing at its edge is not sightseeing. It is visiting. |
| Pachamama | Quechua | In Quechua, the word for earth and the word for time are the same. Pachamama is not where things happen. She is when they happen too. |

## Scenes built (9/9)
1. Komorebi ✅ approved
2. Waldeinsamkeit ✅ approved
3. Friluftsliv ✅ approved
4. Toska ✅ approved
5. Ghayth 🔄 awaiting review
6. Soop-meong 🔄 awaiting review
7. Ceobhrán 🔄 awaiting review
8. Wiikwegamaa 🔄 awaiting review
9. Pachamama 🔄 awaiting review

## Cut words (removed from product)
- Ṛtu (Sanskrit) — cut: too visually similar to Friluftsliv (same open-horizon composition)
- Whatungarongaro (Māori) — cut: redundant with Ceobhrán + Wiikwegamaa mist cluster
- Ubuntu (Zulu) — cut: image could not be fixed (persistent horizontal flip), word removed April 24 2026

## Image generation notes
- AI images fail on close-up tactile textures (cracked earth, dust, rain drops, snow)
- Wide/atmospheric shots are more convincing from AI generators
- ChatGPT image gen > Gemini for photographic realism
- Always portrait orientation (0.75 AR tall)
- Always specify: real photo feel, cinematic, no watermarks
- If two attempts fail on the same word — find a real photo (Unsplash/Pexels)
