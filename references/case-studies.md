# Case studies

Two pieces, two problems. Both are examples of the same taste applied to different material — not templates to copy.

## Gluten — the page as one continuous field

**The problem:** three 3D stills and a contact section. No video, no motion reel, nothing that proves the work can move. The page had to make still images feel like a place.

### Colour is a timeline, not a theme

- The page background is one continuously interpolated colour. Each section declares its own in `data-bg`: `#12489b` blue, `#eaf1f8` pale, `#05070c` near-black, `#f7e8d2` warm cream, `#0b1220`, `#04060c`.
- The engine blends between two sections across the last **0.9 screens** of the outgoing one, using a smoothstep. A section owns its colour for its whole time on screen; the world only shifts as the next one comes up underneath it.
- The hero gradient's last stop is exactly `#eaf1f8`, the colour of the backdrop beneath it. There is no seam at any scroll position.
- The first project is masked at the top by `--intro`, and its scrim fades in on the same variable. The dark gradient does not sit under an empty frame waiting for an image.

**Why it works:** the transition happens under the incoming section, not across the outgoing one. By the time the next section is visible, the background is already its colour. The visitor never sees a crossfade between two panels; they see the world change.

### The image is the page

- Sections are **135vh**. The media is sticky at `top: 0`, **100svh**, full width, zero horizontal crop. The copy sits inside the frame, bottom-left, on a two-direction scrim.
- The scrim is strong at the bottom and left and falls away by 56%, so the same white copy works on a blown-out airfield, a black hall and a warm street without a per-image colour decision.
- Leaving is a move, not a cut. `--exit` shrinks the panel to **96%**, dims it to **45%** and dissolves the copy while the next image slides over it. The image carries a slow **1.06 → 1.0** zoom and **±4%** vertical parallax, so the frame is never fully static.
- The copy is capped at **34rem** and **40ch**. The image gets the screen; the words get a column.

**Why it works:** the photograph is not a card on a page. The page is the frame around the photograph. Every piece of chrome is either on the image or out of its way.

### Typography is poster, not UI

- Archivo at **900** for the hero, **800** for headings, against the same face at **300** for the second line of each title. Weight contrast instead of italics — blockier, more poster-like.
- Inter at 300 for body copy. Display line-height **0.86–0.9**, tracking **−0.045 to −0.055em**.
- No eyebrow labels, no "DESCRIPTION", no "SCROLL TO EXPLORE". A single small `01 / 02 / 03` acts as an editorial index, not a caption.
- The hero name is set at up to **16.5vw**, lifts **38vh** and fades as you scroll, while the clouds travel **13–122vh** at different depths.

**Why it works:** the display type is treated as another image. The body copy is treated as a caption. Nothing in between pretends to be navigation.

### The one joke

- The footer character is a real Blender render of the avatar, posed by rotating whole body parts, lit with four area lights, alpha-trimmed and exported at 460×386.
- He is sunk **38px** into the footer so he never reaches the section above. The rod is painted into the render; a zero-length CSS rod carries only the tip, so the fishing line hangs from the real rod's end.
- The line reels from **44vh to 8vh** as `--reel` runs 0 → 1 across the footer entry. The heart thumps. The copy reads "made with ❤ / by @avationmaster".
- `FEATURES.angler = false` removes the whole thing without touching the markup.

**Why it works:** the joke is in the craft, not the caption. It is the only joke on the page, and it is built as seriously as the work.

### Performance and finish

- Three PNGs at 1.2–2.1 MB became **465 KB of WebP** at q88. Each still has a **1.2 KB, 64px** blurred copy behind it, painted before the sharp file decodes.
- Video previews wait **200ms** after hover, play muted/looping, and are destroyed on mouseleave rather than left running.
- The Discord card uses a still frame of the animated banner until hover, because a GIF cannot be paused in CSS.
- Fixed film grain at **4.5%**, a hairline scroll-progress bar, and a complete static path for `prefers-reduced-motion`.

### Numbers

`0.18` scroll trailing · `135vh` sections · `100svh` media · `0.9`-screen colour blend · `38vh` hero lift · `13–122vh` cloud travel · `1.06 → 1` zoom · `96% / 45%` exit · `200ms` hover delay · `5.4s` showcase hold · `4.5%` grain.

### What not to copy

- The project copy was written from the images and flagged for replacement. Do not treat plausible copy as finished copy.
- The angler only works because it is the only joke. Three characters would turn the footer into a mascot parade.
- Do not copy the palette. Copy the rule: the work supplies the colour; the chrome supplies one value.

## Assembled — one truth at a time

**The problem:** twenty-six photographs. Not a scroll page. An experience you operate with a click, where the photograph is the reward and the dust is the material.

### The metaphor

- Dust that remembers an image. At rest it is an orb, like a device waiting to pair. A click makes it assemble. A click while it holds makes it break. It gathers back into the orb.
- Four states: `dust → form → photo → out`. At any moment, exactly one of them is the truth.
- Every motion is dust: spring, drift, drag, rim break, whirl. There is no second vocabulary.

### The hand-off

This is the part worth studying.

- **Form:** particles spring to their print positions. They stay white dust until they are nearly home, then flood with colour. Their sprites square off as they arrive, so they tile the cell.
- At **1.04s** the print — a real `<img>` above the canvas — begins a **0.95s** fade to opacity 1 while the grain is still visible beneath it.
- **1.05s after** the print is fully opaque, the canvas fades to 0 over **0.55s**.
- **Break:** the canvas is restored instantly *beneath* the opaque print, then the print's `clip-path` wipes from the edges to the centre over **0.7s**. No gap, no flash, no frame where two different states are visible.

**Why it works:** the incoming layer must be able to cover the outgoing one before the outgoing one is allowed to leave. Hiding the canvas when the print merely starts fading would dim the scene. Fading the canvas early would expose the rim. Hiding it in one frame would pop. The order is the design.

### The break is geometry, not a delay

- The break front is measured from the print's rim: `hypot(ex, ey) / √2`. Corners and edges let go first; the middle is last.
- Front length **0.6s**, plus up to **0.12s** of per-particle jitter.
- Each particle starts gathering **70–240ms** after it breaks. The whole field is dust by **1.32s**.
- The first particles leave with a bite inward, a lot of sideways spin, and a little depth. The field whirls as it funnels; it does not shrink.

**Why it works:** the middle is still a photograph while the outside is already leaving. The image appears to fail at its edges, not to switch off. The jitter stops it looking like a wipe.

### Input

- Left click forwards, right click back, arrow keys, two arrows. One line of hint: "left click forwards · right click back · scroll for all of them".
- **Navigation queues.** A click during a dissolve or assembly sets `pending`. The current break finishes, the orb gathers, then `show(next)` runs. The transition is never interrupted.
- **Entry must not move the scene.** Cursor tilt is measured from the point where the pointer entered (`ox`/`oy`), not from the canvas centre, and eased at **2.8/s**. Avoidance ramps at **6/s**. Entering the canvas must not turn or shove the orb.
- In the photo state, repulsion is disabled. The grain is hidden and about to break; denting it would show at the break.

**Why it works:** the pointer is a hand, not a camera. Input is a request, not an interruption.

### The print is a photograph

- **30,000 points**, but the assembled state is a DOM image, not a screen of dots. The points exist to become it and to leave it.
- The plate is positioned at the same `ox/oy/iw/ih` as the sampled grid, so the particle print and the image are pixel-aligned.
- Once the print is opaque, the canvas is hidden entirely. Nothing from the grid can show at the rim, because there is no grid.
- The particle count is not the point. The point is that the assembled state reads as a photograph.

### The frame

- Left rail: kicker, `Ryan / Chapin` in a serif with the second line indented and italic, one-sentence lede, arrows and `01 / 26`, one-line hint.
- Right: a fixed stage of `min(74svh, 660px)`, a hairline caption beneath with title on the left and camera settings on the right.
- Gallery: "The whole roll", four columns preserving each photograph's aspect ratio, title and plate number. Hover is a 1.055 scale and a small saturation lift.
- Footer: location and copyright. Nothing else.

**Why it works:** the piece is an object on a stage, not a background. The text is a caption rail. The collection is a roll, not a grid of content.

### The bug that became a rule

- The watchdog called the frame function directly every **250ms** whenever `lastFrame` looked stale. While the hero was scrolled out of view, `frame()` returned before updating `lastFrame`, so the watchdog fired continuously and each call left another permanent `requestAnimationFrame` chain behind.
- After a minute in the gallery, dozens of loops ran the full simulation and draw at once. The page became unusable until refresh.
- The fix: one tracked `rafId`, cancel before re-arming, a cheap off-screen path that updates `lastFrame`, and no second chain from the watchdog.

**Why it matters:** a hidden loop can undo the whole feel. Performance is not a pass at the end; it is part of the composition.

### Numbers

`30,000` points · `74svh` stage · `0.82 / 1.18` split · `1.04s` assembly · `0.95s` print fade · `1.05s` wait · `0.55s` canvas fade · `0.7s` wipe · `9.5s` hold · `0.6s` break front · `0.12s` jitter · `70–240ms` gather offset · `1.32s` to dust · `2.8/s` tilt ease · `6/s` avoidance ramp.

### What not to copy

- **30k points is not a requirement.** The requirement is that the assembled state reads as a photograph. A hundred well-chosen points that resolve into a print would pass; thirty thousand that read as a dot screen would fail.
- Do not copy the timings blindly. Copy the ordering: incoming covers outgoing, then outgoing leaves; restore the old layer under the new one, then take the new one away.
- Do not keep a canvas alive behind an opaque layer if it can be hidden. But never hide it before the layer is opaque.
- Do not copy the rim-break formula without a rim. If your material does not have edges, find its equivalent — a direction, a light source, a seam.

## What both pieces prove

- The signature is a relationship between two states, not a static screen.
- The interface is removed at the moment the content arrives.
- The best details are structural: a seam, a hand-off, a rim, a queue.
- One metaphor, one accent, one curve, one joke.
- If it stutters, it is not finished.
- The copy is part of the composition; cutting it is a design move.
- The static path is designed, not tolerated.

## Applying it without copying

1. Name the verb of your subject. Build the one transition that expresses it.
2. Put both layers on screen. Make the incoming one cover the outgoing one. Only then hide the outgoing one.
3. Remove one layer of interface: a label, a border, a button, a paragraph.
4. Cut the copy in half. Then cut the sentence that explains the cut.
5. Fix one edge at 100% zoom: a seam, a rim, a stray strip, the last frame.
