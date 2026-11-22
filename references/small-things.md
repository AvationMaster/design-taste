# The small things

None of these are features. Each one is the difference between "nice" and "his".

## Words

- Delete the eyebrow above the heading. The heading is the eyebrow.
- No "scroll to explore", mouse icon, or labelled arrow.
- One-sentence lede. If it has two clauses, cut the second.
- Do not label the count. `01 / 26` is enough.
- Use the subject's noun: plates, frames, roll. Not "Gallery", "Projects", "Content".
- Hints only for non-obvious input. Lowercase. One line. Hide on touch.
- No "Welcome". The name is the headline.
- Footer: one human line and one legal line.
- No social icon row. One link is a relationship; five is a directory.
- No "back to top". The piece is the way back.
- Never invent a client, date, result, email or testimonial. Leave the gap.
- Do not explain the joke.
- No exclamation marks.
- A portfolio says "I", not "we".
- Project copy says what it is and how it was made, not why it is amazing.
- Cut every sentence that describes the interface.
- Then cut one more.

## Type

- Display line-height `0.86–0.9`.
- Negative tracking on display (`−0.02` to `−0.055em`); positive tracking on mono (`0.16em`).
- Indent the second line of a two-line name.
- Use a true italic, never an oblique.
- Body copy `34–40ch`, weight 300, line-height 1.6.
- Mono labels: `0.6rem`, uppercase, `0.16em`, 46% opacity.
- Index numbers with a leading zero.
- Two families maximum.
- No letter-spaced body copy.
- Do not centre long text.
- Do not outline type or set headings as images.
- Make the name big enough that it is the image.
- Keep the display type off the fold edge on small screens.

## Colour and edges

- No `#000` and no `#fff`. Near-black and warm white.
- One accent, used once per screen.
- The next section's background is the exact hex the previous one ends on.
- The hero gradient's last stop is the backdrop colour.
- Mask an incoming image's top edge to the page colour, so it dissolves instead of slides.
- Use `100svh`, not `100vh`.
- No stray strip under a full-height frame. If it parallaxes, inset it (`-6% 0`, height `112%`).
- A hairline is `1px solid rgba(ink, 0.13)`, never `#333`.
- Radius only where the object would have one. Photographs are square-cornered.
- Shadows are huge and soft with negative spread: `0 40px 90px -60px #000`.
- A glow is a blurred, enlarged copy of the image — not a neon halo.
- One grain layer, fixed, everywhere.
- Do not put a border on a photograph.

## Motion

- Never show two versions of the same thing.
- Never cut a layer. Fade the last frame (`0.55s`) or wipe it (`0.7s`).
- The incoming layer covers the outgoing one before the outgoing one disappears.
- Break from the rim, not from a random order.
- Queue input. Never interrupt a transition.
- Measure cursor tilt from the entry point, not the canvas centre.
- Ramp avoidance in; do not switch it on at full strength.
- One rAF loop. Track it, cancel before re-arming.
- One house curve. Two at most.
- Stagger by geometry, not by index.
- No entrance animation on every section.
- Keep parallax under ~10%; past that it is seasickness.
- Reduced motion is a composed static state, not `animation: none`.
- The idle state breathes. An orb that sits still is a spinner.
- Let the print hold. 9.5 seconds is not too long for a photograph.
- If it feels slow, it is probably 50ms too fast.
- Inspect the last frame by sampling opacity or recording the screen.
- Disable cursor repulsion when the layer is hidden and about to break.

## Interaction

- The work is the control. Click anywhere on it.
- Right click goes back; left click goes forward.
- Arrows are 2.4rem circles, not a nav bar.
- Focus is visible: 1px outline, 4px offset. Never `outline: none`.
- Tap targets at least 44px.
- `cursor: pointer` only on operable things.
- No custom cursor unless the cursor is the metaphor.
- Hover is slow and small: 0.9s, 1.055 scale, one property group.
- Destroy iframes on mouseleave. Delay previews by 200ms.
- No hover-only affordance on mobile.
- The interaction should teach itself in five seconds.

## Assets and performance

- 1600px WebP at q88, `srcset`, real `width`/`height`.
- Preload the first image; lazy-load the rest.
- A 64px blurred copy behind every image, not a grey box.
- Fade in only once decoded.
- Check the network panel, not just the design.
- Cap DPR at 2.
- Skip simulation and draw when off-screen.
- No unused JS, no second loop, no hidden canvas doing full work.
- Test on the phone, not the desktop simulator.
- A 3MB hero image is a design failure.

## Finish

- Check 390, 768 and 1440.
- No console messages.
- No layout shift when fonts load.
- No horizontal scroll.
- No clipped descenders on display type.
- Check the colour seam at every scroll position.
- Check the rim at 100% zoom.
- Check with reduced motion on.
- Check on a slow network.
- Check with a keyboard only.
- Remove debug hooks and `window.__` globals.
- Leave a note for every placeholder.
