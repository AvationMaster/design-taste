---
name: design-taste
description: Design and critique web interfaces in Ryan Chapin's taste — reductive, physical, seam-first work for portfolios, photography, and image-led sites. Use when a page should feel art-directed rather than template-built, or when reviewing a UI for unnecessary text, weak hand-offs, generic polish, or a missing static path.
---

# Design taste

Most portfolios look assembled. The ones worth remembering feel like one object someone made.

The work is the interface. Layout, type, motion and copy exist to give it a stage, then get out of the way. Almost every decision below is subtraction.

This is distilled from two pieces only:

- **Gluten** — a scroll-driven portfolio for 3D work. One continuous colour field, near-full-screen images, a footer character built with real craft.
- **Assembled** — a photograph portfolio you operate. Thirty thousand particles rest as an orb, assemble into a print, hold, then break from the rim inward.

## The laws

### 1. One idea, carried all the way
A piece has a single physical idea. Photographs assemble from dust. A page descends from sky to ground. Every transition, cursor response and caption must be explainable by that idea. If an effect needs a paragraph to justify it, it is decoration.

### 2. Design the seam first
Amateurs polish states. The memory is in the hand-off. Decide how A becomes B before you polish A or B: what covers what, when the old layer is allowed to disappear, and what the frame in between looks like. No cuts, no hard edges, no two truths crossfading.

### 3. One truth at a time
Never show two representations of the same thing. When the print is in, the grain is gone. When the grain is the picture, the print is hidden. When the scroll cue has done its job, it is removed. If two layers are visible, one of them is lying.

### 4. Say it once
No eyebrow labels. No "scroll to explore". No explanation of the interface. A title, one line, metadata. If a label describes what the visitor can already see, delete it. The smallest copy change usually makes the biggest difference.

### 5. Motion needs a cause
Everything moves like it has mass: springs, drag, wind, light. No bounce for its own sake, no easing zoo, no animation because a section entered the viewport. If the metaphor does not explain the motion, it does not move.

### 6. The last 5% is the design
The 1px seam. The strip of background under a full-height image. The frame where opacity snaps. The particle that bleeds past the print's rim. The piece is finished when the edges no longer announce themselves.

### 7. Performance is part of the look
A stutter is a visible flaw. One loop, one draw call where possible, transform and opacity only, destroy what left the screen, compress until the page feels instant. Beautiful work that lags is not beautiful.

### 8. The static version is still a composition
Reduced motion is not "turn the animations off". It is another art direction: the first frame, the right crop, the copy visible, the colour still doing its job. No WebGL? Show the photograph. No JS? The first image is already there.

### 9. One joke, built seriously
At most one human detail, executed with real craft. A fully modelled character fishing in the footer. A "made with ❤" line at the end of a hook. Not jokes in every caption, not emoji in the headings. One, and it lands because everything around it is straight.

### 10. Invent nothing
Real photographs, real metadata, real presence. If you do not know a client, a date, an email or a result, leave the space empty. Placeholders get flagged in the hand-off, never dressed up as content. A beautiful lie is still a lie.

## How to build it

1. **Name the subject and the verb.** "Photographs assemble." "The page descends." If you cannot name a verb, there is no piece yet.
2. **Choose one physical metaphor and its resting state.** Write it in one sentence at the top of the file. Every effect must follow from it.
3. **Define the states — four at most.** Write the state machine: `dust → form → photo → out`. List what is visible in each and which transitions are legal. If two states can be true at once, the design is wrong.
4. **Build the hand-off before the polish.** Put both layers on screen. Make the incoming layer able to cover the outgoing one. Only then hide the outgoing one. Inspect the exact frame where they swap.
5. **Compose the frame.** Full-bleed for immersion, a fixed stage for an object. Decide where the text lives before you write it.
6. **Set type and colour.** One display face, one apparatus face, one accent. Ink and dim ink. The work supplies the saturation.
7. **Write the copy last, then cut it in half.** Keep only what the work cannot say.
8. **Remove the interface.** Every border, button, label and hint has to justify itself. If the work can carry it, let it.
9. **Tune the last 5%** at real size with real assets: rim, seam, last frame, stray strip.
10. **Build the static path.** Reduced motion, no WebGL, slow network. It should still look composed.

## Composition

- **The work gets the majority of the viewport.** Text is a narrow rail or a caption band, never a card grid wrapped around a hero.
- **Choose one relationship.** Full-bleed means the image is the world (Gluten, sticky, 100svh, copy on the picture). A fixed stage means the piece is an object (Assembled: `min(74svh, 660px)`, a title line beneath it).
- **Asymmetric splits, not 50/50.** Assembled: `0.82fr / 1.18fr`, text left, piece right, `max-width: 34rem` on the rail.
- **Preserve aspect ratios in collections.** Crop only when the frame itself is the point. A grid that crops every photograph to the same shape is a contact sheet, not a portfolio.
- **One alignment edge.** Title and metadata can justify to opposite edges only when they belong to the same object, like a plate caption.
- **Space separates before lines do.** If a line is needed: `1px solid rgba(ink, 0.13)`, not a grey border.
- **Use `100svh`, not `100vh`.** A full-height frame must be exactly full height; a stray strip reads as a mistake.
- **Fluid spacing and type with `clamp()`.** No hard-coded desktop sizes, no breakpoint at every 100px.
- **The first screen is one composition, not a stack.** If the hero is name + paragraph + buttons + scroll cue + socials, it is a template.
- **Stack on mobile; do not shrink the desktop composition.** Assembled: stage 54svh, two-column grid, hint hidden. Gluten: sticky panels become static, copy stays on the image.

## Type

- **Two families maximum.** One carries the subject, one carries the apparatus. Assembled: Instrument Serif + JetBrains Mono. Gluten: Archivo for display, Inter for body.
- **Display type is tight.** Line-height `0.86–0.9`, tracking `−0.02em` to `−0.055em`, large `clamp()`. Two lines with the second indented is a strong default (`padding-left: clamp(1.2rem, 6vw, 5rem)`).
- **Weight contrast instead of colour.** 900 next to 300. Roman next to a true italic for the human word. Do not fake an italic with a slant.
- **The apparatus is small, uppercase, tracked wide, dim.** Mono at `0.6rem`, `0.16em` tracking, 46% opacity. It labels; it does not speak.
- **Body copy is quiet.** 300 weight, `1.6` line-height, `34–40ch`, `0.94–1.1rem`, `rgba(ink, 0.82)` at most.
- **Use numerals as texture.** `01 / 26`, `MMXXIV / MMXXVI`, plate numbers. Leading zero. Tabular when they align.
- **No all-caps sentences.** Mono caps only for labels, metadata and footer legal lines.
- **No text shadows on UI.** Over a photograph, use a scrim instead.
- **Keep text selectable and real.** Do not outline headings or set them as images.

## Colour and light

- **One field, one ink, one dim ink, one accent.** Not a palette. Assembled: `#08080a`, `#f2efe8`, 46% ink, `#e8a05a`. Gluten: `#eaf1f8`, `#0b1520`, `#e79a4d`.
- **Avoid pure black and pure white.** Near-black and warm white. Over photographs, white is allowed but lives on a scrim.
- **The work supplies the colour.** Sample the image and tint the glow; do not impose a brand palette on photographs.
- **Gradients have a source.** Sky, sun, a radial glow behind an object. No decorative mesh gradients or floating colour blobs.
- **Section colours are one continuous field.** Gluten: each section declares `data-bg`; the engine blends across the last 0.9 screens, so a section owns its colour while it is on screen and only shifts as the next one arrives. The hero gradient ends on exactly the backdrop colour, so there is no seam at any scroll position.
- **Glow is the image, enlarged and blurred.** `blur(42px) saturate(1.1) brightness(0.6)`, not a neon halo.
- **Grain is a material, not a filter.** One fixed overlay binds the layers together: 3–4% in Gluten, stronger in Assembled. Tune it to the piece; keep it consistent.
- **Contrast is not optional.** Dim text is for metadata only. Body copy must be readable on the actual background, not the one in the design file.

## Copy

- **Voice:** plain, dry, first person, specific. "Twenty-six frames, assembled out of dust." "Say hi." "If the light's on, I'm around."
- **The name is the headline.** No "Welcome to my portfolio." No "I'm a designer based in…" before the work.
- **One-sentence lede.** One line if it fits, two if it must. Assembled's entire explanation of the piece is seven words.
- **Hints only for non-obvious input**, one line, lowercase, dim: "left click forwards · right click back · scroll for all of them". Hide it on touch.
- **Use the subject's nouns.** Roll, plates, frames, photographs. Not "Gallery", "Projects" or "Content". The right noun does more than a heading style.
- **Project copy says what it is, what it is made of, how it was lit or built.** Two or three sentences. The first project gets the most words; it is the proof.
- **Ban the portfolio dialect:** passionate, immersive, cutting-edge, stunning, seamless, elevate, journey, solution, "brings to life", "crafted with care".
- **No interface narration.** "Scroll to explore", "Click to view", "Drag to interact", "Hover to preview" are all confessions that the design did not explain itself. Keep one only if the interaction is truly invisible.
- **The footer is one human line and one legal line.** Not a sitemap, not a social icon wall, not a newsletter.
- **Numbers:** spell them out in poetic copy ("Twenty-six frames"), use numerals for data (`01 / 26`, camera settings).
- **Never invent a fact.** No fake clients, dates, testimonials, metrics or emails. If it is unknown, omit it or mark it as a placeholder in the hand-off.
- **Cut every sentence that describes the interface.** Then cut one more.

## Motion and state

- **Start from a state machine.** Four states, one truth. Assembled: `dust` (orb) → `form` (assembling) → `photo` (print holds) → `out` (breaking) → `dust`.
- **The incoming layer must cover the outgoing one before the outgoing one disappears.** Assembled: the grain forms the print; the print fades to opacity 1 while the grain is still there; 1.05 s later the canvas is hidden. On the way back, the grain is restored beneath the opaque print before the print wipes. No frame shows a gap.
- **Never cut a layer.** If something disappears, fade the last frame (`0.55s`) or wipe it (`0.7s`). A one-frame cut is visible even when you think it is not.
- **Break from geometry, not a random order.** Assembled: rim first, middle last, a 0.6 s front, ±0.12 s of jitter. The outside is already leaving while the middle is still a picture. That is what makes it read as a material failing instead of an animation playing.
- **Queue input; never interrupt a transition.** A click mid-dissolve sets the next index. The current break finishes, the orb gathers, then the next photograph forms. No restarting mid-air, no snapping.
- **Entry must not move the scene.** Measure cursor tilt from the point where the pointer entered, ease at ~2.8/s; ramp avoidance at ~6/s. The pointer is a hand, not a camera. A scene that jumps when the cursor arrives feels broken even if the follow-up motion is nice.
- **One house curve.** `cubic-bezier(0.22, 0.71, 0.18, 1)`. Micro-interactions can use `cubic-bezier(0.22, 0.61, 0.36, 1)`. Pick two, use them everywhere.
- **Inertia, not hijacking.** Scroll-driven values trail the scrollbar at ~0.18; native scroll stays native. Never take the scrollbar away from the visitor.
- **The idle state is designed.** The orb breathes (4% radius), spins slowly, avoids the cursor. A resting state with no life is a dead page.
- **Reduced motion gets a complete static composition.** Assembled disables the auto-break and the assembly delay. Gluten paints every section's colour, shows all copy and removes the scroll engine. Not `animation: none` on a page that depends on it.
- **Let hand-offs breathe.** If it feels slow, it is probably 50 ms too fast.

Assembled's timings are a calibration, not a law:

| moment | value |
| --- | --- |
| micro hover / button | 0.2–0.3 s |
| layer fade | 0.55 s |
| print wipe | 0.7 s |
| print fade-in | 0.95 s |
| grain → print | 1.04 s |
| print hold | 9.5 s |
| break front | 0.6 s + up to 0.12 s jitter |
| orb gather | 1.32 s |

## Interaction

- **The work is the control.** Click anywhere on the piece to advance, right-click to go back. Arrows and keys mirror it. The canvas is the button.
- **No toolbar.** Two 2.4rem circles and a count are enough. A nav bar above three sections is furniture.
- **Hints are one line, dim, and disappear on touch.** The interaction should teach itself in the first five seconds.
- **Hover is slow and small.** 1.055 scale over 0.9 s, a little saturation and brightness. Buttons invert (ink fill, background text). Nothing lifts, glows, rotates and shadows at once.
- **Focus is visible.** `outline: 1px solid rgba(ink, 0.6); outline-offset: 4px`. Never `outline: none`.
- **Tap targets are at least 44px.** Even the small arrows.
- **Cursor is `pointer` only on operable things.** No custom cursor unless the cursor is the metaphor.
- **Mobile has no hover-only affordance.** Stack, reveal the hint's information in another way, keep the piece operable with one thumb.

## Performance

- **One `requestAnimationFrame` loop.** Track `rafId`; cancel before re-arming. A watchdog must never start a second chain. Real bug from Assembled: a 250 ms watchdog called the frame function directly whenever the hero was off-screen, and each call left another permanent rAF chain behind. After a minute in the gallery, dozens of loops ran the full simulation at once. Refresh was the only fix. One loop, always.
- **Skip work off-screen.** Use an `IntersectionObserver`; when the piece is out of view, tick cheaply and update `lastFrame` instead of simulating and drawing.
- **`transform` and `opacity` only per frame.** For pointer-driven layers, write one CSS variable per axis and let CSS apply it. Do not write six transforms from JS.
- **Measure on load, resize and `fonts.ready`, not every frame.** Batch layout reads. Debounce resize.
- **Cap DPR at 2.** Cap particle count to what holds 60 fps on the target machine, then tune by eye.
- **Images: 1600px WebP at q88**, `srcset`, `width`/`height`, the first image preloaded, the rest lazy. Fade in only once decoded. Put a 64px blurred copy behind the frame, not a grey box.
- **Destroy iframes on `mouseleave`.** Delay hover previews by 200 ms so passing cursors do not download a video. Warm an animation only if it will be used.
- **A 3 MB hero image is a design failure**, no matter how good it looks.
- **Reduced motion should reduce work, not just visuals.**

## Accessibility

- Real elements: `button`, `a`, `alt`, `aria-label` on icon-only controls.
- The canvas gets an `aria-label`; the DOM plate carries the real `alt`.
- Keyboard: arrows for navigation, Escape for overlays, Enter/Space for cards.
- Never hide essential content behind hover.
- Contrast for body copy. Dim only for metadata.
- A complete `prefers-reduced-motion` path.
- `100svh` so mobile browser chrome does not crop the composition.
- Check 390, 768 and 1440 before calling it done.

## What I reject

- Icon + heading + paragraph + CTA cards.
- Glassmorphism, gradient blobs, floating orbs with no relationship to the content.
- "We craft digital experiences."
- Mouse icons and "scroll to explore".
- Several fonts, several accents, several shadow recipes.
- The same fade-up-on-scroll for every section.
- A lagging custom cursor.
- Dots standing in for a photograph. The assembled state must be the photograph, not a screen of dots.
- A spinner for a static image.
- Text on a photo without a scrim.
- Pure `#000` and `#fff`.
- Labels on obvious controls.
- A footer sitemap.
- Placeholder copy left in production.
- Uncompressed PNGs.
- A second rAF loop.
- A hard cut on the last frame.
- Explaining the joke.

## The test

1. Can I name the one physical idea? Does every motion follow from it?
2. Is there any frame where two versions of the same thing are visible? Fix it.
3. Does the interface disappear when the work arrives?
4. Can I delete half the words without losing meaning? Then delete them.
5. Does the first screen read as one composition at 390, 768 and 1440?
6. Is there a hard seam, a stray strip, or a 1px line that is not intentional?
7. Does it hold 60 fps during the heaviest transition?
8. Does reduced motion still look composed?
9. Is every fact real? Is every placeholder marked?
10. Is there exactly one joke or delight, and is it built with craft?

When in doubt, remove something.

## References

- `references/case-studies.md` — Gluten and Assembled, decision by decision.
- `references/small-things.md` — the small moves that make the difference.
