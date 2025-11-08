# static-site

This folder contains a lightweight, static copy of the HVEP landing page originally built in Next.js. It is provided as a self-contained HTML/CSS/JS preview you can open locally for design, content, and QA work.

## Contents

- `index.html` — main page markup (hero, categories, featured products, stories, donation, footer)
- `styles.css` — global stylesheet (theme variables, layout, responsive rules)
- `scripts.js` — small JS for carousel, header behavior, and rendering featured products
- `product-images/` — local product images used by `scripts.js`
- `images/` — assorted decorative images and icons

## Quick preview

1. Serve the folder (recommended) so relative image paths and JS load correctly:

```sh
# from the repository root
python3 -m http.server --directory static-site 8000
# open http://localhost:8000 in your browser
```

2. Or open `static-site/index.html` directly in the browser (some browsers block local fetches for scripts/images).

## How the product images are wired

- Product data is defined in `scripts.js` (the `featuredProducts` array). Each product object has an `image` property. The script renders product cards into the `#product-grid` element at runtime.
- Local product images live in `product-images/`. Filenames must match the `image` path used in `scripts.js`. If a product image is missing the browser will show a broken image; you can either fix the filename or add a fallback in `scripts.js`.

## Changing prices or products

- Prices are stored as integer rupee amounts in `scripts.js` and formatted for display using the `Intl.NumberFormat('en-IN', { style: 'currency', currency: 'INR' })` helper.
- To change a price or product label, edit the corresponding entry in `scripts.js` and refresh the page.

## Theme and styles

- The site uses handcrafted CSS in `styles.css` with CSS variables at the top for colors and gradients. Recent edits changed the theme to an eco-friendly green palette — update `:root` variables to tweak the theme.
- The hero overlay is controlled by `.slide-overlay` and was switched to a neutral dark gradient so hero images retain natural color.

## Accessibility & performance notes

- Buttons in the static demo are keyboard-accessible and have focus outlines. Images use `alt` text, and critical UI controls include ARIA labels where appropriate.
- Images in this static preview are not optimized — consider compressing or converting to `webp` for production.

## Limitations

- This is a static demonstration. Interactive features like login, cart persistence, and donation processing are intentionally stubbed.
- Some images are hotlinked or included as local placeholder files. For an offline-ready build, copy remote images into `product-images/` and update paths in `scripts.js`.

## Development hints

- If you want to rename an image file (recommended: use simple, lowercase names without spaces), update the corresponding `image` value in `scripts.js`.
- To add a new featured product: add an object to the `featuredProducts` array with `id`, `image`, `name`, `tagline`, and `price`.

