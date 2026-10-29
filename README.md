# Pip's Paint Pots

Colour mixing with guinea pigs, for a seven-year-old (and simple enough for a
four-year-old). Plain HTML, JavaScript and CSS — no build step, no
dependencies, no backend.

**Live:** https://andrewlord311-sudo.github.io/PipsPaintPots/

## How it works

Each round a guinea pig wants something painted (a hutch, bow, ball, cushion
or tunnel, or its own coat), and a card shows the colour. She taps paint pots
to drop blobs into a bowl, which shows the mix as it goes, then **Paint it!**
paints the thing so she can hold it against the card. Any mix that looks the
same counts (two blue and two yellow is the same green as one and one).

**Hints guide without giving the answer.** A miss says which way the colour is
off ("it needs to be bluer", "yours is a bit too dark"), or names a paint the
colour doesn't use at all, but never the recipe. After three tries "Show me
the recipe" fills the bowl.

Seven stages, in teaching order:

1. **Mixing two colours**: the three primaries, and two of them make green, orange or purple.
2. **More of one colour**: lime, sea green, mango, tomato.
3. **Lighter and darker**: white makes a tint, black makes a shade.
4. **Guinea pig coats**: red, yellow and blue together make brown.
5. **Warm and cool**: tap the sunny or the snowy side.
6. **Opposite colours** on a colour wheel, then shown mixed as paint (a muddy brown).
7. **Mixing light**: red, green and blue torches on a dark wall. Red and green
   make yellow and all three make white, next to what the same colours make as
   paint.

1-3 stars a round (2 or 1 for warm/cool and the wheel). A stage clears with at
most one "show me", and the stage row is the way back to any stage. Progress is
in `localStorage` (`ttg_colours`).

**The paint really mixes like paint**, not like RGB, which turns blue + yellow
into grey. Each paint is a reflectance curve across the rainbow, and paints
mix by Kubelka-Munk (each paint's absorption averaged by amount and tinting
strength), seen through the CIE colour-matching functions as sRGB. The curves
were fitted so the mixes look like children's poster paint. Light mixes with
CSS `mix-blend-mode: screen`, which is how light really adds. One honest limit:
these five paints can't make a true cream (it comes out lemon or peach), so
Evie, who is cream, isn't one of the coats.

## Stars and the Guinea Pig Garden

The stars go to the same **Guinea Pig Garden** as Pip's Maths
(`andrewlord311-sudo/TimesTables`, which owns the garden). Every
`andrewlord311-sudo.github.io` site shares one origin, and so one
`localStorage`, so `addStars` here adds to the same `ttg_rewards` key the
maths games use. The star total and the garden tile link to the garden there.
It only works on the live sites: opened from a local server, the stars stay in
that server's own storage.

It began as the Colour Mixing game inside Pip's Maths, and moved here on
29.10.26 because it isn't maths. The `ttg_colours` key is the same, so progress
made there carries over.

## The files

- `index.html` — the home, game and finish screens.
- `paint.js` — the game: the paint model, stages, hints, stars.
- `pigs.js` — the guinea pig drawing and the farm pigs' looks, copied from
  Pip's Maths so the apps match. Change them there and copy them here.
- `style.css` — the base styles copied from Pip's Maths, then the game's own.

## Progress

Kept in the browser only, so it does not follow her between devices and is
lost if that browser's data is cleared.
