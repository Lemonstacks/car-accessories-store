# DriveStack — Site Specification

## Brand Identity

- **Name**: DriveStack
- **Tagline**: Upgrade Every Drive.
- **Niche**: Premium automotive accessories (car interior, exterior, electronics, detailing)
- **Tone**: Minimalist luxury, angular, editorial, automotive performance

## Color Palette

| Token | Hex | Usage |
|-------|-----|-------|
| Black | `#0a0a0a` | Primary backgrounds |
| Carbon | `#141414` | Secondary dark surfaces |
| Surface | `#1a1a1a` | Cards, inputs on dark bg |
| White | `#FFFFFF` | Primary text on dark |
| White Dim | `rgba(255,255,255,0.72)` | Body text on dark |
| White Muted | `rgba(255,255,255,0.38)` | Subtle text, labels |
| Electric Blue | `#007BFF` | CTAs, accents, icons |
| Blue Bright | `#3395ff` | Hover states |
| Blue Dim | `rgba(0,123,255,0.15)` | Decorative/background accents |

## Typography

- **Headings**: Barlow (800 weight, uppercase, tight letter-spacing)
- **Body**: Inter (400/600 weight)
- **Style**: Uppercase headings, 0.2em letter-spacing on eyebrows/labels, editorial feel

## Design Language

- Angular clip-path CTAs (not rounded buttons)
- 1px border separators (not box-shadows)
- Blue bottom-line reveals on hover
- Left-anchored content (not centered)
- Dark backgrounds dominate (scheme-2 is primary)
- Asymmetric layouts over symmetric grids
- No Bootstrap patterns (no centered cards, no rounded corners, no drop shadows)

## Theme Architecture

- **Base**: Shopify Horizon v3.5.1 (renamed "Whisper" in admin)
- **Architecture**: Online Store 2.0 (JSON templates, sections, blocks)
- **Custom CSS**: `assets/drivestack-custom.css`
- **No build tools**: Pure Liquid + CSS + vanilla JS
- **No jQuery**

## Color Schemes (settings_data.json)

| Scheme | Background | Text | Usage |
|--------|-----------|------|-------|
| scheme-1 | `#FFFFFF` | `#111111` | Product pages, light sections |
| scheme-2 | `#111111` | `#FFFFFF` | Header, footer, dark sections, hero |
| scheme-3 | `#007BFF` | `#FFFFFF` | Accent/CTA sections |
| scheme-4 | `#1a1a1a` | `#FFFFFF` | Alternate dark (newsletter, trust) |

## Homepage Sections (in order)

1. **DriveStack Hero** (`sections/drivestack-hero.liquid`)
   - Left-anchored editorial layout
   - Eyebrow text + uppercase heading + subheading + angular CTA
   - Dark diagonal gradient overlay
   - Settings: image, eyebrow, heading, subheading, button_label, button_link, height

2. **DriveStack Categories** (`sections/drivestack-categories.liquid`)
   - 4-column dark cards, 3:4 aspect ratio
   - Bottom-anchored title + "Explore →" arrow
   - Blue line reveal on hover, image zoom
   - Categories: Interior, Exterior, Electronics, Detailing

3. **Best Sellers** (native `product-list` section)
   - Uses Shopify's built-in product grid
   - 4 columns, portrait image ratio
   - Needs a collection assigned

4. **DriveStack Trust** (`sections/drivestack-trust.liquid`)
   - Split panel: label left (280px), icon grid right
   - 4 trust items with SVG icons
   - Items: Premium Quality, Secure Checkout, Fast Shipping, Easy Returns

5. **DriveStack Reviews** (`sections/drivestack-reviews.liquid`)
   - Dark background, 3-column grid
   - Blue left-border accent on cards
   - Large decorative quote mark
   - Compatible with @app blocks (Judge.me, Loox)

6. **DriveStack Newsletter** (`sections/drivestack-newsletter.liquid`)
   - Two-column split: copy left, form right
   - Joined input+button (no gap, no rounded corners)
   - Uses Shopify customer form

## Product Page

- **Template**: `templates/product.json`
- **Layout**: Media left (grid), sticky details right
- **Blocks**: Title (H3 preset), Price, Divider, Variant Picker, Buy Buttons, Description
- **Extras section** (`sections/drivestack-product-extras.liquid`):
  - Trust badges (Secure Checkout, Fast Shipping, 30-Day Returns, Premium Quality)
  - Specifications table (configurable via blocks)
  - Product JSON-LD schema (`snippets/drivestack-product-schema.liquid`)
- **CSS fixes**: Description headings capped at 1.25rem max, tables styled

## Collection Page

- **Template**: `templates/collection.json`
- **Header**: Dark (scheme-2), collection title + description
- **Grid**: Horizontal filters, medium card size, adapt image ratio

## Header (`sections/header-group.json`)

- Announcement bar (scheme-2, dark)
- Logo left, menu center, search right
- Sticky always
- Transparent on homepage
- Logo height: 44px desktop / 30px mobile

## Footer (`sections/footer-group.json`)

- Dark (scheme-2)
- Menus + contact info
- Copyright, policies, social links (Instagram, YouTube, TikTok)

## 404 Page

- Dark (scheme-2)
- "Page not found" + continue shopping CTA
- Product recommendations below

## Custom Files Created

| File | Purpose |
|------|---------|
| `assets/drivestack-custom.css` | All custom brand styling |
| `sections/drivestack-hero.liquid` | Homepage hero |
| `sections/drivestack-categories.liquid` | Category cards |
| `sections/drivestack-trust.liquid` | Trust/why section |
| `sections/drivestack-reviews.liquid` | Testimonials |
| `sections/drivestack-newsletter.liquid` | Email signup |
| `sections/drivestack-product-extras.liquid` | Product trust + specs |
| `snippets/drivestack-product-trust.liquid` | Trust badge strip |
| `snippets/drivestack-product-schema.liquid` | Product JSON-LD |
| `snippets/drivestack-scroll-top.liquid` | Scroll-to-top button |

## Performance Considerations

- No jQuery (Horizon is modern Web Components)
- ES modules with importmap (@theme/* namespace)
- modulepreload for critical JS
- Single custom CSS file (no external dependencies)
- Images: lazy loading on all except hero (eager + high fetchpriority)
- Avada SEO Suite installed (adds snippets to theme.liquid head)

## SEO Implementation

- Product JSON-LD schema on all product pages
- Proper H1 hierarchy (one per page)
- Alt text attributes rendered via templates
- Meta tags rendered via built-in `meta-tags` snippet
- Avada SEO app for additional optimization

## Shopify Store Details

- **Store URL**: drivestack.myshopify.com
- **Custom Domain**: drivestack.store
- **Theme ID**: 164680204544
- **Theme name in admin**: Whisper
- **GitHub repo**: github.com/Lemonstacks/car-accessories-store
- **Currency**: ZAR (targeting South Africa + US)
- **Fulfillment**: CJDropshipping (China warehouse, 5-11 day delivery)

## Push Commands

**CRITICAL RULE: Always pull before pushing any JSON template or config file. The Shopify admin/Theme Editor may be ahead of local. Pushing without pulling first will overwrite admin changes (images, settings, etc).**

```bash
# ALWAYS pull first before any push
$env:NODE_OPTIONS="--use-system-ca"; shopify theme pull --theme 164680204544 --path . --force --store drivestack.myshopify.com

# Then push to Shopify (live)
$env:NODE_OPTIONS="--use-system-ca"; echo "y" | shopify theme push --theme 164680204544 --path . --allow-live --store drivestack.myshopify.com

# Push specific files only (safer)
$env:NODE_OPTIONS="--use-system-ca"; echo "y" | shopify theme push --theme 164680204544 --path . --allow-live --only assets/drivestack-custom.css --store drivestack.myshopify.com
```

**Safe to push without pulling first:**
- `assets/drivestack-custom.css` (never edited in admin)
- `snippets/*` (custom snippets not touched by admin)
- `sections/drivestack-*.liquid` (custom sections)

**MUST pull before pushing:**
- `templates/index.json` (admin edits images, sections, settings here)
- `templates/product.json`
- `templates/collection.json`
- `config/settings_data.json`
- `sections/header-group.json`
- `sections/footer-group.json`

## Pending / TODO

- [ ] Upload category images (Interior, Exterior, Electronics, Detailing)
- [ ] Link category cards to collections in Theme Editor
- [ ] Add 10-15 more products with custom descriptions
- [ ] Set up main navigation menu
- [ ] Create specific sub-collections for SEO
- [ ] Add shipping/return/privacy policies
- [ ] Configure payment provider
- [ ] Set up abandoned cart emails
- [ ] Submit sitemap to Google Search Console
- [ ] Remove store password when ready to launch
