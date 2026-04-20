# Understory — Design Brief

## The Feeling We Are Designing For

This is not a website. It is a room you enter.

The user should feel what happens when you stand at the edge of something vast — a forest at dusk, an open steppe, water that extends past the horizon — and realize that you do not have words for what you are experiencing. That the inadequacy is not a failure of language. It is proof that the world is larger than you.

This feeling has no clean name. It is not "humbled" (too small). It is not "awe" (too casual). It is closer to: *realizing that the earth has been offering you something your whole life that you never had the words to receive.*

That is what Understory makes visible. The words are not the content. They are evidence that other people, in other languages, got there before us — that the gap between what nature does to us and what we can say about it is a real thing, and a crossable thing.

**Emotional register:** Romantic in the 19th-century sense — not sentimental, but seized by something real and vast. Rilke, not Hallmark. Hiroshi Sugimoto's seascapes, not a nature calendar. The Rothko Chapel, not a gallery gift shop.

**The vastness the user stands at the edge of is nature — not an abstract void.** That is an important distinction. The solitude is not loneliness for its own sake; it is the solitude of one small person standing in front of something alive and huge. The romanticism is about nature, not about melancholy.

---

## What Nature Sounds Like Here

Nature enters this product primarily through sound and scene — not through visual decoration of the shell. The shell stays dark and restrained; the scenes and the sound are where nature is permitted to arrive with its full weight.

- **Entry and word field:** a very quiet, very distant ambient bed. One element only — distant air, a low drone, or very occasional water. The kind of sound you do not notice starting. The field should feel like *a room with a window open onto something vast.*
- **Scene:** the scene's own specific sound, full-fidelity. Rain on earth for Ghayth. Wind through leaves for Komorebi. Mist-silence for Ceobhrán.
- **Never:** music with melody or beat, new-age textures, spa ambience, sound-effect collages.
- **A single sound toggle** lives in the bottom-right corner. Dim, small, always there. On or off — no slider.

---

## Visual Language

### Color
- **Background:** Near-black. Not pure black — something that breathes. `#080808` to `#0d0d0d`. The kind of dark that exists just before your eyes adjust.
- **Text:** Off-white to warm cream. `#f5f0e8`. Never pure white — pure white is clinical.
- **Glow / hover states:** A very faint warm amber pulse. Not orange. Not gold. The color of a candle seen through fog.
- **Scene colors:** Each word owns its own palette. These are defined per scene, not globally. The word field and landing page stay close to monochrome — color belongs to the scenes.
- **No bright colors anywhere outside of scenes.** No blues, no greens, no reds in the shell UI.
- **No horizon line, no gradient band in the shell.** The darkness is a single continuous space. Any visible boundary reads as a diagram and breaks the feeling of being *inside* something.

### Typography
- **One typeface family.** A humanist serif — something with weight and history. Suggestions: EB Garamond, Cormorant Garamond, or Playfair Display. The words must feel like they have been here for centuries.
- **Non-Latin scripts must render correctly and beautifully.** 木漏れ日, غيث, ऋतु, 숲멍 each need a paired serif face (Noto Serif JP / Noto Naskh Arabic / Noto Serif Devanagari / Noto Serif KR) that feels kin to the Latin serif — not a mismatched system fallback.
- **The words themselves:** Large. 36–52px. Loose letter-spacing. The word is the object — it should feel like a physical thing.
- **Line 1 — original script.** Larger. Cream.
- **Line 2 — romanization.** Smaller, lighter, italic. Like a translation whispered. *For Latin-script words, this line is omitted — do not repeat the word.*
- **Line 3 — language.** Smallest, most dim. Small-caps or spaced monospace works. Feels like a museum plaque.
- **Supporting text (one-line felt descriptions, only in scenes):** Small. 14–16px. Light weight. Long line-spacing. Present but quiet.
- **No bold anywhere in the shell UI.** Weight comes from size and contrast, not boldness.

### Motion
- **Everything moves slowly.** Nothing snaps. Nothing bounces. Transitions are dissolves, not slides.
- **Words breathe.** In the word field, words drift very slowly — not randomly, organically. Like objects floating in still water. Drift distance is small: 4–8px over 6–10 seconds. This is the difference between alive and a screensaver.
- **Breathing can be differentiated per word, in service of the word's meaning** — e.g. Whatungarongaro's breath fades more deeply than the others; Ghayth's rhythm is steadier and more drop-like; Rtu's is the slowest. Keep this subtle — a user who notices it consciously is the exception.
- **Hover response:** When a word is hovered, it clarifies — comes into slightly sharper focus, increases glow very faintly, other words dim slightly. The user feels the word notice them.
- **Scene transitions:** When a word is clicked, the word field does not slide away. It dissolves — like something going dark. The scene fades up from black. It should feel like entering, not navigating.
- **Exit:** The scene fades to black. The word field breathes back into existence — softer than the first reveal. No title on re-entry.

### Layout
- **Full bleed always.** No containers, no max-widths, no cards.
- **No navigation.** No persistent header. No footer. No menus. The only exit from a scene is a barely-visible back affordance and Escape.
- **The word field is not a grid.** Words are placed organically across the full screen — like they drifted there. No alignment to columns or rows. Sizes should vary more than feels comfortable: one or two words notably larger, one or two notably smaller. Rotations are slight (±2–3°), and a few words sit at zero — so it does not feel like everything has been tilted on purpose.
- **Clusters and isolations.** Some words sit close to another; some are alone at an edge. The reward is for slow looking.
- **Generous negative space.** The dark is not empty — it is the subject. Words float *within* the darkness; they do not fill it.

---

## The Three Screens

### Screen 1 + 2 — One Continuous Reveal

Landing and word field are a single screen. The reveal is the product's opening note and should be paced carefully.

1. **Black** (≈1.5s). The page loads to darkness. Nothing else. The user's eyes begin to adjust.
2. **Title fades in** (≈2s fade). *Clearing* — centered, large, humanist serif, cream.
3. **Argument line fades in** (≈1.5s later, ≈2s fade).
   > *Our language for nature is thin. Other languages have gotten closer.*
   Left aligned under the title, same serif, smaller, dimmer. This is the product's one sentence; it sets the whole thesis in two clauses.
4. **Stillness** (≈2–3s). The user reads the line. Nothing happens.
5. **Dissolve into field.** Title and line slowly fade. Simultaneously, twelve words begin to breathe into visibility across the space — not all at once; staggered over 4–6 seconds, like stars becoming visible as the sky darkens. Komorebi is the last to light, and it stays gently lit as an invitation.

**No "enter →" prompt.** The words are the invitation. A prompt would make it a website; its absence makes it a space.

**On re-entry from a scene:** skip steps 1–4. Words breathe back in directly, more quickly (≈2s), with one word already softly lit — the word the user just exited.

### Screen 2 (held state) — Word Field

The full screen. Near-black. Twelve words scattered organically across the space. Some cluster loosely, some are isolated. One word is always softly lit — first Komorebi, then whichever word the user last hovered. The layout rewards slow looking.

Each word renders as:
- **Line 1:** Original script (large, 36–52px, cream)
- **Line 2:** Romanization (smaller, 18–22px, italic, dimmer) — *omitted for Latin-script words*
- **Line 3:** Language (smallest, 12–14px, very dim)

Words breathe slowly. On hover: the hovered word clarifies, others dim very slightly. On click: the word field dissolves. The scene rises.

### Screen 3 — Scene (template, Komorebi as first)

Full bleed. The Three.js or video scene fills the entire viewport. The word appears overlaid in the lower third — script, romanization, and a single felt line (not a definition). For example:

> 木漏れ日  *Komorebi*
> The way sunlight breaks through leaves — as if the forest is trying to reach you.

No other UI except a barely-visible exit. The scene's ambient sound plays on entry, respecting the global sound toggle. The experience lasts as long as the user stays. There is no timer.

---

## What This Is Not

- Not a climate dashboard
- Not a language-learning app
- Not a travel or culture magazine
- Not a meditation or wellness app
- Not a starfield, a particle playground, or a music product
- Not dark-mode-as-aesthetic — dark because the dark is the subject

---

## How to Use This Brief in Claude Design

Paste the relevant section as your prompt. Be specific about screen, colors, and feeling. Claude Design responds better to emotional and sensory language than to technical specs — lean into that.

Start with **Screen 1 + 2 (the continuous reveal into the word field)** — it is the heart of the product. Design that first. The scene screens follow from it.
