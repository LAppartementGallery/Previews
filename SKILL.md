---
name: lappartement-design
description: Use this skill to generate well-branded interfaces and assets for L'Appartement Gallery (Geneva), either for production or throwaway prototypes/mocks/etc. Contains essential design guidelines, colors, type, fonts, assets, and UI kit components for prototyping. Specialises in artist fact-sheets (A4 print-ready PDFs) but the visual system extends to any L'Appartement editorial surface.
user-invocable: true
---

Read the `README.md` file within this skill, and explore the other available files.

Key files to know:
- `README.md` — full brand context, content fundamentals, visual foundations, iconography.
- `colors_and_type.css` — root entry point. Importing it gives you every brand token.
- `system/brand/tokens.css` — source of truth for colours, type scale, A4 grid.
- `system/fonts/fonts.css` — Inter + Inter Display via Google Fonts (substitute for Forma DJR / Helvetica).
- `assets/` — wordmarks (complete + monogram, black on transparent) and the building line-art for the closing page.
- `ui_kits/fact-sheet/index.html` — the reference fact-sheet (Aria Lemaître / INHABITED). Copy and retune per exhibition.
- `preview/` — atomic design-system cards (colours, type, components, rules).

If creating visual artifacts (slides, mocks, throwaway prototypes, fact-sheets), copy assets out of this skill and create static HTML files for the user to view. If working on production code, you can copy assets and read the rules here to become an expert in designing with this brand.

Hard rules — non-negotiable:
- No icons, no emoji, no decorative SVG glyphs anywhere.
- No gradients, no glassmorphism, no marketing shadows, no rounded-corner cards.
- No page numbers, no running headers/footers on print artifacts.
- No address, no contact details, no social handles, no QR codes — on any surface, ever.
- Hierarchy is built from typography + space + colour, never from boxes or decorative borders.

If the user invokes this skill without any other guidance, ask them what they want to build or design, ask some questions (which exhibition? which artist? how many works? what is the accent colour pulled from the works?), and act as an expert designer who outputs HTML artifacts *or* production code, depending on the need.
