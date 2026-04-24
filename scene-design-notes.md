# Understory — Scene Design Notes

Lessons from building the Komorebi scene. Apply these before starting any new scene.

---

## What to do

### Photo base
- **Use real photos as the scene foundation.** Procedural geometry, Gemini-generated textures, and SDF shapes all look synthetic against the emotional tone the product requires.
- **Shoot from below, looking up.** For forest words especially, the upward perspective places the viewer inside the environment, not observing it from outside.
- **Choose portrait-orientation photos (approx 0.75 AR).** UV cover-crop math shows the most interesting upper portion on landscape screens. Set `CENTER_Y` in the shader to frame the right slice — for Komorebi, 0.73 showed the leaf canopy and sky gaps.
- **Keep the photo static.** No UV displacement, no camera wobble. UV displacement moves the whole image like a shaking camera, not like wind in leaves. If the scene needs movement, add it in a separate layer on top.
- **Serve via HTTP, never `open file://`.** Three.js `TextureLoader` is blocked by browser security when opened directly. Always run `python3 -m http.server 8000` from the project root.

### Light layers
- **Place light origins at the actual sky gaps visible in the photo.** Don't invent light sources that contradict the photo's lighting. Check the glow/ray/beam positions against what the eye naturally reads as "where the light comes from."
- **Use Gaussian cross-section for light shafts: `exp(-x² × 2.2)`**, not `smoothstep`. Gaussian has no visible edge — it fades continuously to zero. `smoothstep` with a hard inner value creates a painted-on strip with a visible boundary.
- **Keep shafts essentially static.** Very slow opacity breathing (period 60–90 seconds) simulates the faint shift of light through settling leaves. Anything faster reads as animation, which breaks the realism.
- **Use `AdditiveBlending` for all light layers.** Black = transparent in additive mode. This is how all glow, ray, and caustic layers work without needing alpha-cutout masks.
- **Couple light layers to the same gust noise as any movement.** If the same noise value drives leaf sway AND light variation, the two feel physically connected — when the wind opens a gap, the light changes.

### Layer stack (render order)
```
0 — photo base (bgMat, clip-space PlaneGeometry)
1 — soft glow / sky halo (AdditiveBlending)
2 — light shafts / rays (AdditiveBlending)
3 — dust motes / particles (3D perspective, AdditiveBlending)
```

### Text
- **Use strong stacked text-shadow for legibility over complex backgrounds.** A single shadow is not enough. Stack pixel shadow + spread shadow + blur: `0 1px 3px rgba(0,0,0,1), 0 0 20px rgba(0,0,0,0.95), 0 2px 8px rgba(0,0,0,0.95)`.
- **Don't use amber/gold text on amber/gold backgrounds.** The Komorebi scene has warm green-gold tones; amber caption text disappears. Use near-white (`rgba(255,250,238,0.92)`) for the romanization and felt line. The large script character can stay amber because its size carries it.
- **Script (large):** amber `#e8c97a` — big enough to read against any background
- **Roman + felt (small):** near-white `rgba(255,250,238,0.9)` with stacked dark shadow

### Scene entry timing
- **Double `requestAnimationFrame` before adding the `.lifted` class to the veil.** A single rAF sometimes batches the class addition with the initial render, making the CSS transition fire on the same frame and appear to do nothing. Double-rAF forces a committed initial state first.
- **Veil lift: 1.4s transition** is right — cinematic but not sluggish.
- **Caption in: 900ms after veil starts lifting** — gives the scene time to breathe before text appears.

---

## What not to do

### Movement
- **Don't displace the photo UV globally.** Even subtle global displacement makes the whole image shake like a handheld camera. Users immediately notice: "the whole screen is moving."
- **Don't use orbiting or floating light dapples.** Moving bright spots look like a screensaver. Users described them as "always flowing, very unrealistic."
- **Don't float external PNG leaf sprites over the photo.** Two different visual realities (photo background + rendered sprite) clash visibly, especially when the sprites have AI-generated aesthetics that don't match the photo's lighting.
- **Don't try to animate specific individual leaves in a photo.** UV-space flutter hotspots look like rubber-sheeting. The photo is a fixed moment; the light is what moves.

### Light effects
- **Don't use `smoothstep(hw, hw * 0.25, perp)` for beam cross-sections.** The flat inner region looks painted on. Replace with `exp(-normPerp² × 2.2)`.
- **Don't use fast-moving caustic dapple spots.** At speed, they read as floating UI elements rather than physical light.

### Text / UI
- **Don't use `cursor: default` on interactive word elements.** Users won't discover hover/click without the pointer cursor signal.
- **Don't use hover transition durations longer than 0.3s on word interactions.** 1.6s (the original) feels broken — users move their cursor and nothing happens for almost two seconds.
- **Don't use the same font style for the intro argument line and the CTA.** The argument is italic prose; the CTA is an invitation. If both are italic at similar sizes, they blur into one block of text.

### Infrastructure
- **Don't open HTML files with `open filename.html`.** This uses `file://` protocol and breaks Three.js texture loading. Always use the local server.
- **Don't put scene HTML files in the project root.** They belong in `/scenes/`. Assets (photos) go in `/assets/`.

---

## Photo sourcing model (for future scenes)

The Komorebi workflow — Tina shoots a photo → Claude renders the scene on top of it — is proven and should be the default for all photo-based scenes. For future scenes:

1. Shoot with the word's meaning in mind (time of day, angle, environment)
2. Portrait orientation preferred (0.75 AR)
3. Drop in `/assets/` with a clean name (e.g. `waldeinsamkeit.jpg`)
4. Set `CENTER_Y` in bgMat shader by eye — what slice of the photo best shows the concept?

Words that may not need a photo base (pure generative Three.js):
- **Rtu** — particle mandala cycling four seasonal states; a real photo may not be needed
- **Ubuntu** — root network graph; abstract by design
- **Pachamama** — breathing terrain displacement; photo possible but challenging

---

## Felt line process

Each scene has one felt line — the single sentence (or two) that produces the feeling of the word rather than defining it. Rules:
- Research the actual etymology and literary origin before writing
- Write 3–4 options; Tina picks
- Sub-agents may critique but never change the felt line unilaterally — that decision stays with Tina
- The felt line should include whatever is most specific and surprising about the word (e.g. "any weather" for Friluftsliv, not just "the outdoors")
- One clean image or one precise emotional beat — see Komorebi's line as the model

## Word color system
Each word's color matches its emotional register — not a fixed amber for all scenes.
- Warm words (Komorebi, Friluftsliv, Waldeinsamkeit): `#e8c97a` amber
- Cold/grey words (Toska): `rgba(220, 215, 205, 0.94)` cold off-white
- Apply this judgment to each new scene individually

## Scenes

| Scene | File | Photo | Status |
|-------|------|-------|--------|
| Komorebi | `/scenes/komorebi.html` | `/assets/komorebi.jpg` | ✅ Approved |
| Waldeinsamkeit | `/scenes/waldeinsamkeit.html` | `/assets/waldeinsamkeit.png` | ✅ Approved |
| Friluftsliv | `/scenes/friluftsliv.html` | `/assets/friluftsliv.png` | ✅ Approved |
| Toska | `/scenes/toska.html` | `/assets/toska.png` | ✅ Approved |
| Ghayth | `/scenes/ghayth.html` | `/assets/ghayth.png` | 🔄 Awaiting review |
| Soop-meong | `/scenes/soop-meong.html` | `/assets/soop-meong.png` | 🔄 Awaiting review |
| Ceobhrán | `/scenes/ceobhran.html` | `/assets/ceobhran.png` | 🔄 Awaiting review |
| Ubuntu | `/scenes/ubuntu.html` | `/assets/ubuntu.png` | 🔄 Awaiting review — image horizontally flipped (known) |
| Wiikwegamaa | `/scenes/wiikwegamaa.html` | `/assets/wiikwegamaa.png` | 🔄 Awaiting review |
| Pachamama | `/scenes/pachamama.html` | `/assets/pachamama.png` | 🔄 Awaiting review |
