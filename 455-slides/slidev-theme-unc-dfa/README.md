# slidev-theme-unc-dfa

A Carolina-blue / navy academic lecture theme for [Slidev](https://sli.dev), adapted from the "Deterministic Finite Automata" lecture deck.

## Use locally

1. Copy this `slidev-theme-unc-dfa/` folder into your Slidev project (or `npm link` it).
2. In your slides' frontmatter, point `theme` at the folder:

```yaml
---
theme: ./slidev-theme-unc-dfa
logo: ./unc-logo.png
---
```

3. Run `slidev example/slides.md` from inside this folder to preview the full "Deterministic Finite Automata" lecture deck (all 32 slides, ported 1:1 from the original), or copy `example/slides.md` and `example/unc-logo.png` as a starting point for your own deck.

## Layouts

- **cover** — navy title slide. Frontmatter: `kicker` (small label above title).
- **section** — navy divider slide with a large index number. Frontmatter: `index` (e.g. `"01"`).
- **default** — paper-background content slide. Frontmatter: `kicker`.
- **two-cols** — paper background, title + two side-by-side columns. Uses named slots `title`, `left`, `right` (via `::title::`, `::left::`, `::right::` markers). Frontmatter: `kicker`.
- **statement** — full navy slide for a single bold claim (theorem teasers, big takeaways). Frontmatter: `kicker`.
- **end** — closing slide, same treatment as cover but left-aligned with a logo.

## Palette & type

CSS variables are defined in `styles/index.css`:

- `--unc-navy #13294B`, `--unc-blue #4B9CD3` (+ `-light`/`-pale`/`-tint` steps)
- `--unc-paper #FAFAF7`, `--unc-ink #1A1F27`, `--unc-ink-soft #51607A`
- Body: system sans (`-apple-system, 'Helvetica Neue', Arial`). Code/math: `'Roboto Mono', ui-monospace, monospace`.

Publish under your own package name to reuse across decks: rename `package.json`'s `name`, `npm publish`, then set `theme: unc-dfa` (or your chosen name) in any Slidev deck.
