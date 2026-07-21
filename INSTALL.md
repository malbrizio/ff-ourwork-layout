# Our Work — Install Layout A + Mobile M

Code is ready in the theme files. Images still need to be attached in Shopify (Admin API token was unauthorized from this environment).

## Files changed

| File | Role |
|---|---|
| `sections/our-work-gallery.liquid` | Layout A (desktop) + Layout M (mobile ≤900px) |
| `snippets/our-work-tile.liquid` | Shared tile + lightbox data |

Local path:
- `/Users/matt/shopify-themes/live-current/sections/our-work-gallery.liquid`
- `/Users/matt/shopify-themes/live-current/snippets/our-work-tile.liquid`

Reference mockup: https://malbrizio.github.io/ff-ourwork-layout/

---

## What you need to do

### 1) Upload the 15 heroes to Shopify Files

Source (production weight already exported):

- Tiles: `/Users/matt/ff-ourwork-layout/tiles/01.jpg` … `15.jpg` (or `.webp`)
- Prefer **full/** masters for upload — Shopify resizes via CDN  
  `/Users/matt/ff-ourwork-layout/full/01.jpg` … `15.jpg`

**Shopify Admin → Content → Files → Upload**

Suggested filenames:
`FF_OurWork_Hero_01.jpg` … `FF_OurWork_Hero_15.jpg`

### 2) Push theme code (unpublished first — recommended)

From the theme directory:

```bash
cd /Users/matt/shopify-themes/live-current

# Push ONLY these two files to an unpublished theme (pick ID from theme list)
shopify theme push \
  --store foreverfierce.myshopify.com \
  --theme <UNPUBLISHED_THEME_ID> \
  --only sections/our-work-gallery.liquid \
  --only snippets/our-work-tile.liquid
```

Preview that theme’s Our Work page before touching live.

**Live theme is `Concept 6.0 MERGED`.** Do not push to live until preview looks right.

To push live when ready:

```bash
shopify theme push \
  --store foreverfierce.myshopify.com \
  --theme 144855269443 \
  --only sections/our-work-gallery.liquid \
  --only snippets/our-work-tile.liquid
```

### 3) Wire blocks on the Our Work page

1. Open **Online Store → Themes → Customize** (on the preview theme first)
2. Go to **Pages → Our Work** (template `page.our-work`)
3. In **Our Work Gallery** section:
   - Set copy (defaults are already the new copy):

| Setting | Value |
|---|---|
| Eyebrow | Custom gym apparel |
| Title | Our Work |
| Subheading | Design examples up close — ink, type, and embroidery quality you can judge before you commit. |
| Closing | Every drop is built around your gym. Free design. Members preorder. You don’t buy inventory. |
| CTA | Schedule a call → GHL form URL |

4. **Remove** old square mockup blocks (or keep them under Archive — they only show if present).
5. **Add 15 “Hero shot” blocks** in this exact map:

| Block order | Role (dropdown) | Shot # | Caption | Alt |
|---|---|---|---|---|
| 1 | Open — large feature | **15** | Location identity · St. Louis | Underdog Barbell Club St. Louis skyline print in pink and black |
| 2 | Open — stack | **10** | Minimal left chest | Underdog Strength Club minimal left-chest print on mineral wash tee |
| 3 | Open — stack | **08** | Brand mark · back print | Forever Fierce circular FRVR brand mark back print on black tee |
| 4 | Portrait triptych | **01** | Raglan · crest | Underdog trees raglan crest on white/black raglan |
| 5 | Portrait triptych | **03** | Collegiate mark | Underdog Strength collegiate mark on navy tee |
| 6 | Portrait triptych | **11** | Brush type | Underdog Stay Strong brush type on grey tee |
| 7 | Detail strip / mobile rail | **04** | Script wordmark | Underdog Strength Co. script wordmark on heather raglan |
| 8 | Detail strip / mobile rail | **05** | Full back print | Underdog Barbell Club red badge full back print on white tee |
| 9 | Detail strip / mobile rail | **07** | Embroidery · hoodie | Underdog Barbell Club embroidery on black hoodie |
| 10 | Color pair | **09** | Color + circular mark | Forever Fierce circular mark on blue muscle tank |
| 11 | Color pair | **13** | Halftone texture | USC Underdog Strength Club purple halftone print on lavender tee |
| 12 | Bento — large feature | **06** | Illustrated type · Indiana | Do The Hard Thing illustrated type on mineral wash tee |
| 13 | Bento — stack | **02** | Lift Local series | Lift Local Underdog Barbell orange and cream print on charcoal tee |
| 14 | Bento — stack | **12** | Back print · bubble type | Underdog Barbell Club bubble type back print on black tee |
| 15 | Close craft | **14** | Craft close-up · embroidery | UDBC Underdog Barbell Club embroidery close-up on sand garment |

Optional: **Stats strip** block (one) above the gallery.

### 4) SEO meta (Page settings, not theme)

**Online Store → Pages → Our Work** (or Search engine listing):

| Field | Value |
|---|---|
| Title | Our Work \| Custom Gym Apparel Portfolio – Forever Fierce |
| Description | Design examples up close — ink, type, and embroidery quality from Forever Fierce. Custom gym apparel for 5,000+ gyms and 30,000+ orders. |
| OG image | Prefer shot 15 or 09 (not email header) |

### 5) QA checklist

- [ ] Desktop: open band is large + 2 stack (not a flat grid)
- [ ] Desktop: 3+3+2+bento+close bands look correct
- [ ] Mobile ≤900px: desk layout hidden; mobile scroll shows
- [ ] Mobile: horizontal “Print detail” rail swipes
- [ ] Mobile: captions visible without hover
- [ ] Lightbox works; prev/next doesn’t double-count desk+mobi clones
- [ ] Images sharp (not the old soft mockup previews)
- [ ] CTA opens GHL form
- [ ] Page speed: first tiles load, rest lazy

### 6) Optional archive

If you want the old square mockups below the heroes, leave them as **Archive mockup** blocks. They appear under “More from the archive”. Otherwise delete them.

---

## Architecture (quick)

- **Desktop (>900px):** Layout A — editorial bento bands by `role`
- **Mobile (≤900px):** Layout M — full-bleed → inset → 2-up → horizontal detail rail → color bleed → alternating stack → close
- Same 15 images; dual DOM with lightbox dedupe by `data-shot-id`

## If theme push is blocked

1. Shopify Admin → Themes → … → Edit code  
2. Paste `our-work-gallery.liquid` into `sections/`  
3. Create `snippets/our-work-tile.liquid` and paste snippet  
4. Save → Customize page → map images per table above
