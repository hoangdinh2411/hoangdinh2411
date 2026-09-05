# William Đinh — Portfolio

A one-page portfolio site styled as a technical drawing sheet: a faint
blueprint grid, a corner title block like an architectural drawing, and an
animated circuit-style schematic of the stack instead of a hero photo.
Built to feel like a workshop, not a résumé.

No framework, no build step — one `index.html` with inline CSS/JS and
Google Fonts loaded over a CDN link.

---

## What's in it

- **Hero** — name, role (typed in on load), a short intro, and contact links.
- **Schematic diagram** — an SVG circuit board showing Frontend → Backend →
  Data → Infra, with traces that draw themselves in once on page load, and
  nodes that glow amber on hover.
- **Currently building** — a spotlight on the active project (Sista Steget),
  with a pulsing "live" indicator.
- **Field notes** — past roles told as short case notes (what was built and
  why it mattered) rather than bullet-point job listings.
- **Toolkit** — a grid of the core technologies, each highlighting on hover.
- **Origin** — education, kept brief.
- **Footer** — contact links again, for anyone who scrolls straight to the
  bottom.

Design details:
- Colors, spacing, and animation timings all live in the `<style>` block —
  CSS variables under `:root` at the top control the palette.
- All motion respects `prefers-reduced-motion`: if a visitor's system has
  that on, the typing effect, schematic draw-in, and parallax are skipped
  and everything just appears in place.
- The mouse-parallax on the background grid is subtle by design — it's
  controlled by the `mousemove` listener near the bottom of the file.

## Preview locally

Open `index.html` directly in a browser, or serve it so relative behavior
matches production:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Deploy on GitHub Pages (free)

1. Create a new repository on GitHub, e.g. `william-portfolio`.
2. From this folder, push it:
   ```bash
   git init
   git add .
   git commit -m "Initial portfolio"
   git branch -M main
   git remote add origin https://github.com/<your-username>/william-portfolio.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Set **Branch** to `main`, folder to `/ (root)`, then **Save**.
6. After a minute, it's live at:
   `https://<your-username>.github.io/william-portfolio/`

## Before you push — two placeholders to swap

1. **GitHub link** — the "GitHub" link in the hero currently points to
   `https://github.com/` with no username. Search `index.html` for
   `href="https://github.com/"` and put your profile URL in.
2. **LinkedIn** — your source resume's LinkedIn link went to a
   notifications page (`linkedin.com/notifications/?filter=all`), not a
   public profile, so it was left out of this build entirely. Add a
   `<a href="https://linkedin.com/in/<you>">LinkedIn</a>` next to the other
   contact links once you have the right URL.

## Customize further

- **Palette** — edit the hex values under `:root` in `<style>` (`--bg`,
  `--amber`, `--cyan`, etc.) to shift the whole site's mood.
- **Copy** — the tagline, project description, and field notes are all
  plain text in `index.html`; edit them directly, no build step needed.
- **New project or role** — copy an existing `.note` block (in "Field
  notes") or the `.feature` block (in "Currently building") and edit the
  content.
- **Schematic diagram** — the SVG under `<div class="diagram-wrap">` uses
  absolute coordinates for the boxes and connecting lines; nudge the `x`/`y`
  values if you add or remove a layer.
