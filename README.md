# Forever Fierce — Our Work Layout Concepts

Interactive layout mockups for a new **Our Work** section featuring 15 hero product close-up shots.

## View live

After GitHub Pages is on, open:

**https://malbrizio.github.io/ff-ourwork-layout/**

Or open `index.html` locally.

## What’s inside

Four layout options (switch in the top bar):

| Option | Name | Role |
|---|---|---|
| **A** | Editorial Bento | **Recommended desktop** — native ratios, paced bands |
| **B** | Masonry | Fast density, weaker narrative |
| **C** | Runway | Luxury strips; better with fewer shots |
| **M** | Mobile product scroll | **Recommended phone** — full-bleed / inset / 2-up / horizontal detail rail |

Direct mobile view: https://malbrizio.github.io/ff-ourwork-layout/?view=m

Use **Toggle band labels** on Layout A to see the structure. On **M**, scroll inside the phone frame (desktop) or full-screen (real phone).

## Feedback asks

1. Prefer A, B, or C for the live site?
2. Keep all 15, or cut to a tighter hero set (8–10)?
3. Should existing square mockups live below as an “archive” grid?
4. Any shot order / pairing changes?

## Notes

- **Production-weight images** (not the old 400px previews):
  - `tiles/` — ~native–1600px long edge, WebP + JPEG, ~150–250 KB target (avg ~207 KB WebP)
  - `full/` — lightbox masters ~native–2200px, WebP + JPEG, ~250–450 KB target
  - Mockup serves WebP; JPEG kept as CDN/fallback masters
- Design system: FF bone / ink / lime, Montserrat only.
- Rationale is at the bottom of the page.
