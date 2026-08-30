# 🦠 Germ Busters

A tiny counting game for young kids. Germs wriggle around inside the tummy,
the child taps them, and every pop calls out the next number — 1, 2, 3…
Level 1 has 1 germ, level 2 has 2 germs, all the way to 20. When a level is
cleared, a giant number pops up showing which level it was.

It is one self-contained `index.html` file: no build step, no dependencies,
no network calls. It works offline and on phones, tablets and desktops.

## Playing

- **Tap a germ** to pop it. The number that appears is how many you have
  popped so far, and it is spoken out loud.
- **Clear the level** and a big number shows the level you just finished.
- **🔊** mutes the pops and the spoken numbers. **🔄** starts again.

On a phone held upright the gut turns a quarter turn so it fills the screen
and the germs stay big enough for small fingers.

### Grown-up options

Add these to the address to skip ahead:

- `?level=8` — start at level 8, e.g. `index.html?level=5`

The sound setting is remembered in the browser.

## Running it locally

Just open `index.html` in a browser. Or serve the folder:

```bash
python3 -m http.server 8765
```

then visit <http://localhost:8765>.

## Hosting it on GitHub Pages

1. Create a new repository on GitHub (for example `germ-busters`). Do not add
   a README — this folder already has one.
2. Push this folder to it:

   ```bash
   git remote add origin https://github.com/<your-username>/germ-busters.git
   git branch -M main
   git push -u origin main
   ```

3. On GitHub go to **Settings → Pages**, set **Source** to
   *Deploy from a branch*, pick branch **main** and folder **/ (root)**, and
   save.
4. After a minute the game is live at
   `https://<your-username>.github.io/germ-busters/`.

Because everything lives in `index.html`, any static host works just as well.

## How it is built

- One HTML file: markup, styles and about 600 lines of plain JavaScript.
- The play area is drawn on a `<canvas>`. The gut reports the box it paints
  into and that box is scaled to fill the screen, so the germs are as large
  as the display allows — and it turns a quarter turn on a tall screen.
- The gut is described as a set of **tubes**: a centre line plus a radius,
  which may taper from point to point. One fat short tube makes the stomach
  at the top, one long winding tube makes the intestine.
- Germs wander freely and are pushed back inside the nearest tube each
  frame, so they always stay in the gut. The tighter the tube around a germ,
  the more its heading is steered along that tube's direction — so germs
  swim the length of the intestine instead of rattling against the walls.
- Sound is generated with the Web Audio API; numbers are spoken with the
  browser's built-in speech synthesis. No audio files, no assets, no fonts to
  download.

## Licence

MIT — do what you like with it.
