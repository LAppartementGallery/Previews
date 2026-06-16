# Fact-Sheet — UI Kit

Print-ready A4 fact-sheet for a single artist within a L'Appartement
exhibition. One self-contained HTML file per fact-sheet, exported to
PDF via the browser's *Print → Save as PDF* dialog.

## File

- **`index.html`** — the full reference fact-sheet. Sample data: artist
  *Aria Lemaître* in the exhibition *INHABITED* (28.05 — 17.07.2026),
  two works, accent colour earth-brown `#875026`.

Drop your own images onto the page (the slots are persistent) or
replace the `<image-slot>` markers with `<img>` tags before generating
the final PDF.

## Page sequence (canonique)

| # | Page | Notes |
|---|---|---|
| 1 | Cover | Full-bleed detail; exhibition title centred top; dates below; artist name bottom-left; logo bottom-left |
| 2 | Biography | Family-name display caps LEFT; first-name lighter above; portrait wraps with bio text (9–12 px runaround) |
| 3 | Quote | Full accent-colour bleed; oversize open/close quote marks at corners; signature in caps below |
| 4 | Work A — plate | Work centred, proportional scale; fiche commerciale centred below |
| 5 | Work A — close-up | Full-bleed detail, no text |
| 6 | Work B — plate | (repeat) |
| 7 | Work B — close-up | (repeat) |
| 8 | Detailed fiche | Provenance / Exhibitions / Literature / Notes for every work, paginated as needed |
| 9 | Final — L'Appartement | Logo top-centre, building illustration below, manifesto |

Insert an additional **Quote page** between work cycles for breathing
room when a fact-sheet covers four or more works.

## Variables you inject

Override these on `:root` of your fact-sheet to retune per exhibition:

```css
:root {
  --accent-color:      #875026;
  --accent-text-color: #EFE5D7;
  --bio-title-color:   #2F4A2A;
}
```

## Print

Open the file in Chrome / Edge / Safari, *Cmd+P → Save as PDF*, paper
size A4, margins **None**, background graphics ON. The CSS uses
`@page { size: A4; margin: 0 }` and `page-break-after: always` between
pages, so the result is one PDF page per HTML page.

## Constraints

- No icons, no emoji, no decorative SVG.
- No gradients, no shadows, no border-radius.
- No page numbers, no running header/footer.
- No gallery address, contact, social media, or QR codes — anywhere.
- Body text is justified with last line left; titles and captions are
  left-flush.
- Images on white have their photographic background cropped out;
  frames stay only if part of the work.
- Sizing is proportional across the document: a 200 × 150 cm painting
  visually dominates a 30 × 40 cm painting on its own page.
