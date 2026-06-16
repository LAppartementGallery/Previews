# L'Appartement — Design System

Design system for **L'Appartement Gallery** (Genève) — a contemporary fine-art
gallery whose primary editorial output is the **artist fact-sheet**: an
A4 print-ready PDF that introduces a single artist within an exhibition,
their biography, a quote, the works on view (with commercial details,
provenance, exhibitions, literature), and a closing page that reasserts
the gallery's identity.

This system encodes the rules so that any agent — human or otherwise —
can produce a fact-sheet that feels unmistakably *L'Appartement*: editorial,
fine-art, clean, dense when content demands it, otherwise spacious. No
gratuitous decoration. No marketing tropes.

---

## Sources

| Source | Provided | Notes |
|---|---|---|
| Wordmark, complete (with "ART GALLERY" byline) | `uploads/lappartement-complete-black.svg` | Vector, single black ink. |
| Wordmark, monogram (no byline) | `uploads/lappartement-monogram-black.svg` | The default lockup used on most surfaces. |
| Exhibition title artwork — INHABITED | `uploads/inhabited-logo.svg` | Sample exhibition wordmark. *Note: SVG references `class="st0"` with no style declaration — the text needs a font fallback to render. We treat exhibition titles as live text using Inter Display, not as a fixed SVG.* |
| Building illustration | `uploads/immeuble-lappartement.png` | Line-art of the gallery's Geneva building. Closing-page-only asset. |
| Brief / fact-sheet specification | provided inline | Encoded in this README and the fact-sheet UI kit. |

No codebase, Figma, or live product was attached — this system is built
from the typographic brief plus the four supplied vector/raster assets.

---

## Index

```
README.md                       — this file
SKILL.md                        — agent-skill entry point
colors_and_type.css             — project-wide CSS entry (re-exports tokens)
system/
  brand/tokens.css              — colours, A4 grid, type scale, semantic styles
  fonts/fonts.css               — @font-face / family aliases
assets/
  lappartement-complete-black.svg
  lappartement-monogram-black.svg
  inhabited-logo.svg
  immeuble-lappartement.png
ui_kits/
  fact-sheet/
    README.md                   — fact-sheet recipe + variables
    index.html                  — live sample (artist Aria Lemaître, INHABITED)
    page-*.html                 — individual page references
    components/*.jsx            — reusable page primitives
preview/
  *.html                        — Design System tab cards
```

---

## Content fundamentals

L'Appartement copy is **editorial fine-art prose**, not marketing copy.

- **Tone.** Sober, descriptive, occasionally personal when quoting the artist.
  Critic-magazine register: tells the reader *what is there* and *what to
  notice*, never *what to feel*.
- **Voice.** Third-person for the gallery, first-person *only* inside
  attributed artist quotes. Never "we", "you", "discover", "explore".
- **Language.** Bilingual house style — French and English coexist; both
  are written without contractions, with serial commas, em-dashes for
  parenthetical breaks. No exclamation marks. Question marks are rare.
- **Casing.** **All-caps tracked** is reserved for: exhibition titles,
  artist family names on the bio page, section markers (`PROVENANCE`,
  `EXHIBITIONS`, `LITERATURE`), and quote signatures. Body copy uses
  sentence case. Title case is avoided.
- **Numbers and units.**
  - Dates: `28.05 — 17.07.2026` (DD.MM — DD.MM.YYYY, em-dash with spaces).
  - Dimensions: `98 x 80 cm` then `38 5/8 x 31 1/2 in.` on the next line.
  - Prices: thousand separators are apostrophes (Swiss convention) and
    currency follows: `Price (excl. VAT): 95'000 USD`. The label is bold.
  - When sold, the entire price line is replaced by **`Sold`** (bold), nothing more.
- **No emoji, no icons, no decorative glyphs.** The only typographic
  marks that appear by intent are: the apostrophe in *L'Appartement*,
  the em-dash, the slash in fractional inches, and the oversize curly
  quotation marks on the quote page.
- **Vibe.** Restrained, considered, slightly French. The page should feel
  like a museum wall label, not a webshop.

Examples that are correct:

> *Lemaître's INHABITED is the second chapter of a body of work begun
> in 2022 and now extended to nine large canvases…*

> *Price (excl. VAT): 95'000 USD*

Examples that are wrong (do not generate these):

> ~~Discover the works of an emerging visionary!~~
> ~~Lemaitre's Stunning New Show 🎨~~
> ~~Featured artwork — 95,000 USD — Buy now~~

---

## Visual foundations

### Palette
- **Black on paper.** Default body text is `--lapp-black` (`#0A0A0A`,
  warm near-black, never pure `#000`) on `--lapp-paper` (`#FFFFFF`).
- **Accent.** One **per exhibition** (`--accent-color`), pulled from
  the dominant tones of the works — earth brown for *INHABITED*
  (`#875026`); other shows might use forest green, indigo, ochre,
  etc. It only appears as the full-bleed background on the quote page(s)
  and — sparingly — as the bio-title colour.
- **Accent text colour** (`--accent-text-color`) is **never pure white
  and never saturated**: a tinted cream that nods toward the accent's
  complement. Brown accent → warm cream `#EFE5D7`; forest green →
  greenish off-white `#F0F2EC`.
- **Bio title colour** (`--bio-title-color`) may differ from black —
  a deepened relative of the accent (forest green `#2F4A2A` against
  the brown accent) — used for the artist's first + family name on
  page 2. It does NOT appear anywhere else.
- **Muted greys** (`--lapp-ink-muted` `#5B5B5B`, `--lapp-ink-faint`
  `#9A9A9A`) are reserved for codes, secondary labels, and the
  Artlogic identifier. Body text never uses them.

### Typography
- **Display** — Inter Display (Inter v4 at high optical size, SIL-OFL,
  substituting Forma DJR Display). Used for exhibition titles, artist
  family-name capitals, section heads. Always tracked open
  (`letter-spacing: 0.14em`+) in capitals, never in lowercase.
- **Body** — Inter (substituting Helvetica). Optical sizing on, tight
  tracking (`0.005em`). Justified with last-line-left for body
  paragraphs; left-flush for captions, labels, lists.
- The hierarchy is built from **size, weight, letter-spacing, and
  whitespace** — never from boxes, borders, coloured highlights, or
  background fills (the quote page is the single exception).

### Layout & grid
- **A4 portrait, 210 × 297 mm.** Margins `20mm` editorial default,
  `14mm` when a page is dense.
- Single-column body by default. The bio page runs a **text wrap
  (`shape-outside`)** around the portrait with a `9–12 px` inner
  margin — likewise the artist's name wraps around the portrait on
  the same page.
- No running headers, no page numbers, no footers. The gallery logo
  appears **only** on page 1 (cover) and the closing page.
- Body paragraphs are justified, last line left. Drapeau gauche
  (ragged-right) is allowed for titles, labels, captions, lists.

### Imagery
- Works on white. Backgrounds (greys, fond perdu, photographic
  surrounds) **must be cropped out**. Frames stay if they are part
  of the piece.
- **Proportional scaling within a fact-sheet.** A 200 × 150 cm canvas
  must visually dominate a 30 × 40 cm canvas. We compute a target
  width from `real_size_cm` against the largest work in the document.
  Pages do not auto-fill — small works sit small on the page.
- Cover detail is full-bleed but never crops in a way that destroys
  the motif's legibility. Close-ups (page B of each cycle) are full-bleed
  texture studies, no text overlay.

### Backgrounds, surfaces, effects
- **No gradients.** No glassmorphism. No marketing drop-shadows. No
  rounded-corner cards. No coloured left-border accents.
- The quote page is the single full-bleed colour surface. Everything
  else lives on paper white.
- **No transparency**, no blur. Print constraints, but also taste.

### Borders, rules, shadows
- Hairline rules (`0.4–0.5 pt`) are permitted to separate fiche items
  *only when density requires it* — most fact-sheets do without.
- No outer shadows. No inner shadows. No glow. No filters of any kind.
- Corner radius is **0 everywhere**. Frames around works render as-is
  with whatever radius the artwork itself has.

### Animation / motion
- **N/A.** Fact-sheets are print artifacts. The HTML deliverable is
  a print-target with `@page` rules; nothing animates. If this system
  is ever ported to a screen surface, transitions remain quiet: 200ms
  ease for hover state changes, no springs, no parallax.

### States (when used on screen)
- Links/buttons (rare): hover darkens to 75 % opacity, active drops to
  60 %. No colour shifts, no shadows.

### Whitespace & rhythm
- Whitespace is the structural device. A 3-line bio paragraph and a
  half-page of breathing room beneath it is correct. Most pages are
  closer to *empty* than to *filled*.

---

## Iconography

**L'Appartement uses no icon system whatsoever.** No icon font, no
sprite, no Lucide / Heroicons / Material set, no SVG glyphs in body
copy, no unicode arrows, no emoji. The closing-page **building line-art**
(`assets/immeuble-lappartement.png`) is the single piece of pictorial
brand iconography that exists — it appears once, on the final page,
beneath the logo. The wordmark itself is the other recurring vector
mark; everything else on a fact-sheet is type, photograph, or paper.

If a future surface (a website, a digital invitation) genuinely needs
a UI affordance (a play button, a download arrow), use Inter at its
current size, no icon — or set the affordance in body text. This is
non-negotiable.

---

## Per-exhibition variables to inject

```css
:root {
  --accent-color:      #875026;   /* fil rouge identitaire */
  --accent-text-color: #EFE5D7;   /* texte sur fond accent */
  --bio-title-color:   #2F4A2A;   /* nom de l'artiste page 2 */
}
```

Plus the data shape consumed by `ui_kits/fact-sheet`:

- **Exhibition** — `title`, `dates`, `cover_artwork_detail`,
  optional `curatorial_intro`.
- **Artist** — `first_name`, `family_name`, `portrait`, `bio` (paragraphs),
  `quotes` (array of `{text, position_in_sequence}`).
- **Works** — array of `{image, close_up_image, title, year, medium,
  dimensions_cm, dimensions_in, code, price_usd | sold, provenance[],
  exhibitions[], literature[], notes, real_size_cm}`.

See `ui_kits/fact-sheet/README.md` for the page-by-page recipe.

---

## Open caveats

- **Fonts.** `Inter` is loaded from Google Fonts as the stand-in for
  Forma DJR Display + Helvetica per the brief. If you have access to
  the licensed faces, drop the `.woff2` files into
  `system/fonts/files/` and rewrite the `@font-face` block in
  `system/fonts/fonts.css`. Layout was tuned against Inter's metrics,
  so swapping in a different face may need a small re-balance of
  display sizes.
- **Building illustration** is provided as a PNG. A vector original
  would be preferable for print scaling — flag if you can supply one.
- **The INHABITED logo SVG** has no embedded font; we treat exhibition
  titles as live text. If the typeface in the source SVG was a custom
  drawing, swap our display family for that file on a per-show basis.
