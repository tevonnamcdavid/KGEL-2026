# KGEL Christmas Catalog 2026

A static HTML5 flipbook using locally bundled Tailwind CSS 2.2.19 and StPageFlip 2.0.7. No runtime CDN, framework, package installation, or build dependency is required. The 168 page images were exported from the existing local catalog on October 27, 2026; the original catalog and references remain separate.

## Preview and validate

From this folder, run `npm run build` to validate the output, then `npm start`. Open http://127.0.0.1:8792. Use an HTTP server rather than opening index.html directly, because the app fetches its page configuration.

## Deploy

- **Vercel:** Import this folder as the project root. The included vercel.json selects `dist` as the output. No install step is required.
- **GitHub Pages:** Publish the contents of `dist` at your Pages root (or copy them into your repository's `docs` directory and select that source). All asset URLs are relative, including on repository subpaths. Include `.nojekyll`.
- Any static host can serve the contents of `dist`. No server routes or secrets are needed.

## Configure pages

Edit `dist/pages.json`. Numbers must be sequential, starting at 1. Each entry supports:

```json
{
  "number": 1,
  "image": "assets/page-001.jpg",
  "thumbnail": "assets/thumb-001.jpg",
  "title": "Power tools",
  "keywords": "drill saw SKU-123",
  "button": {"label": "View product", "url": "https://your-store.example/product"}
}
```

`thumbnail`, `keywords`, and `button` are optional. No store links have been invented; add real product destinations to enable overlays. Use HTTPS URLs for external assets and links. Provide images at the catalog's 8.5:11 ratio. Page images load only around the active spread. Thumbnails load lazily when the tray opens. The search indexes page titles and extracted product text, including SKUs. A shared URL can include `#page=42`.

Desktop displays a spread; mobile displays one page. Click, drag corners, swipe, use arrows, or use the page slider. Zoom opens a scrollable high-resolution detail view; Escape closes it. Fullscreen uses the browser Fullscreen API when supported. Reduced-motion preferences shorten page transitions.

`render.cjs` is a development-only exporter for the original neighboring catalog. It uses Playwright and Edge from this workspace and is not required for deployment. Re-export images if the source catalog changes. `qa.cjs` is the local browser verification script.

The libraries retain their MIT licenses in `dist/vendor`. Catalog artwork and product content remain the owner's materials.

## Spread layout

Uses the supplied Flipsnack reference: the front cover is centered alone, followed by interior spreads 2–3, 4–5, and so on, with the final cover centered alone. Desktop includes side arrows and a subtle center-fold shadow. Mobile retains one page at a time.
