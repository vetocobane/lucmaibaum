# lucmaibaum.com

Redesign of Luc Maibaum's Director of Photography portfolio. Static site built with Astro.

## Requirements

Node 22.12+ and the **Microsoft Visual C++ Redistributable (x64)** — Astro's CSS engine ships a
native binding that fails to load without it (`ERR_DLOPEN_FAILED`, Windows error 126).
If it is not installed, prefix commands with `NAPI_RS_FORCE_WASI=true` to use the slower WASM
fallback (`@bruits/satteri-wasm32-wasi` is already a devDependency).

## Commands

```
npm install
npm run dev      # local dev server on :4321
npm run build    # static output to dist/
npm run preview
```

## Structure

- `src/projects.json` — all 14 projects: title, category, credits, video provider/id, still paths.
  Scraped from the old Wix site. Add a project by appending an entry and dropping its stills in
  `public/stills/`; pages and routes generate from this file.
- `src/impressum.json` — Impressum text, one paragraph per array entry.
- `src/pages/` — `index`, `work/index`, `work/[slug]`, `about`, `contact`, `impressum`.
- `src/components/VideoEmbed.astro` — click-to-load facade. The Vimeo/YouTube iframe is only
  injected on click, so no player chrome or platform branding shows on page load.
- `public/stills/` — 109 stills, 1600×900.

## Outstanding content

- The About bio in `src/pages/about.astro` is placeholder copy and needs Luc's own text.
- The client list on the About page is inferred from project credits; confirm with Luc.
- Stills came from the Wix CDN at 1600×900. Replace with originals when available.
