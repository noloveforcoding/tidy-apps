# Tidy Apps — Website

Static site for [tidy-apps.com](https://tidy-apps.com), built with [Astro](https://astro.build).

## Running locally

```bash
npm install
npm run dev
```

Then open [http://localhost:4321](http://localhost:4321).

To build for production:

```bash
npm run build      # outputs to dist/
npm run preview    # preview the built site locally
```

## Deploying

**Netlify** — connect the repo, set build command to `npm run build`, publish directory to `dist/`.  
**Vercel** — `vercel` (auto-detects Astro, zero config needed).

Both platforms detect Astro automatically from `astro.config.mjs`.

## Adding images

Drop these files into `public/images/` before deploying:

| File | Description |
|---|---|
| `hadit-icon.png` | HadIt? app icon, at least 240×240px |
| `app-store-badge.svg` | Official Apple App Store badge (black version) — download from Apple's marketing resources page |

## Adding a new app

1. **App icon** — add `public/images/<appname>-icon.png`
2. **App page** — create `src/pages/apps/<appname>.astro` (copy `hadit.astro` as a template)
3. **Privacy policy** — create `src/pages/privacy/<appname>.astro`
4. **Support page** — create `src/pages/support/<appname>.astro`
5. **Home page card** — open `src/pages/index.astro` and add another `<AppCard>` inside `.apps-grid`
6. **Nav "Apps" link** — if you now have multiple apps, create `src/pages/apps/index.astro` as a directory page and update `src/components/Nav.astro` to point there instead of directly to a single app

## Project structure

```
src/
  layouts/
    Base.astro          HTML shell, meta tags, CSS
  components/
    Nav.astro           Sticky nav with blur-on-scroll
    Footer.astro        Site footer
    AppCard.astro       Reusable app card (icon + name + description + badge)
  pages/
    index.astro         Home
    about.astro         About
    contact.astro       Contact
    apps/
      hadit.astro       HadIt? app page
    privacy/
      hadit.astro       HadIt? privacy policy
    support/
      hadit.astro       HadIt? support and FAQ
  styles/
    global.css          CSS custom properties, reset, base typography
public/
  images/               Drop hadit-icon.png and app-store-badge.svg here
```
