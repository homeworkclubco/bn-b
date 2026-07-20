# Belliappa Norman-Butler

Website for **Belliappa Norman-Butler**, a London-based hybrid art advisory practice building distinguished post-war and contemporary art collections worldwide.

**Live URL:** [https://bnb.art](https://bnb.art)

---

## Technology Stack

| Layer | Technology |
|---|---|
| Framework | [Astro 6](https://astro.build/) (static site generation) |
| Language | TypeScript (strict mode) |
| Styling | [UnoCSS](https://unocss.dev/) (custom preset) + PostCSS (Utopia fluid type/space, nesting, custom media) |
| Interactivity | [Alpine.js](https://alpinejs.dev/) |
| Animation | Scroll-reveal via `IntersectionObserver` (`src/scripts/reveal.ts`) |
| CMS | [Pages CMS](https://pagescms.org/) (Git-based, configured via `.pages.yml`) |
| Media | Plyr (YouTube embeds), lightbox3 (image galleries), Sharp (image optimisation) |
| Icons | `@lucide/astro` |
| Fonts | LTC Caslon Pro + Futura (via Adobe Typekit) |
| Consent | vanilla-cookieconsent |
| Package Manager | pnpm |

## Project Structure

```
├── src/
│   ├── assets/                 # Images, SVGs, fonts processed by Astro
│   │   └── uploads/            # CMS-uploaded images
│   ├── components/
│   │   ├── actions/            # Buttons, action links
│   │   ├── blocks/             # Page-section blocks
│   │   ├── display/            # Heading, Prose, OverlapHeading
│   │   ├── forms/              # Input, Textarea, Checkbox, Field
│   │   ├── layout/             # Layout primitives (Stack, Cluster, Grid, etc.)
│   │   └── svg/                # Inline SVG components
│   ├── content/
│   │   ├── pages/              # Static pages (homepage.md, contact.md, people.md, work.md, press.md)
│   │   ├── press/              # Press collection (folder of entries)
│   │   ├── redirects.json      # Static redirects
│   │   └── settings.json       # Site settings (organisation info, SEO defaults)
│   ├── layouts/
│   │   └── Layout.astro        # Root layout (SEO, header, footer, cookie consent)
│   ├── lib/                    # Helpers (e.g. seo.ts)
│   ├── pages/
│   │   ├── index.astro         # Homepage
│   │   └── [...slug].astro     # Generic page route
│   ├── plugins/
│   │   └── rehype-youtube-plyr.mjs
│   ├── scripts/                # Client scripts (reveal, video-bg, justified-gallery)
│   ├── config.ts               # Site config (@config alias)
│   └── styles/                 # CSS layers, tokens, typography, colours
├── public/                     # Static public assets
├── .pages.yml                  # Pages CMS configuration
├── uno.config.ts               # UnoCSS custom preset
├── astro.config.mjs            # Astro config (sitemap, redirects)
└── postcss.config.cjs          # PostCSS pipeline
```

## Content Management

Content is managed through **Pages CMS**, which edits files directly in this repository. The CMS is configured in `.pages.yml`.

Pages live in `src/content/pages/` as Markdown files with YAML frontmatter. Each page defines its `title`, `slug`, `seo` metadata, and an array of `sections` (blocks) that build the page layout. Press entries live in the `src/content/press/` collection.

`src/content.config.ts` is **auto-generated** from `.pages.yml` — do not edit it manually.

## Commands

All commands are run from the root of the project:

| Command | Action |
|---|---|
| `pnpm install` | Install dependencies |
| `pnpm dev` | Start local dev server at `localhost:4321` |
| `pnpm build` | Production build → `./dist/` |
| `pnpm preview` | Preview production build locally |
| `pnpm astro ...` | Run Astro CLI commands |

## Design System

- **Light theme** — `data-color-scheme="light"` on `<html>`; warm off-white background (`#FEFBF2`) on near-black (`#051519`), black accent
- **Fluid typography & spacing** — [Utopia](https://utopia.fyi/) scales interpolate between 320px and 1660px viewports
- **Semantic colour tokens** — `var(--color-bg)`, `var(--color-foreground)`, `var(--color-accent)`, etc. (defined in `src/styles/color.css`)
- **Never use raw values** — always reference design tokens for colours, spacing, and typography

## Path Aliases

| Alias | Maps to |
|---|---|
| `@assets/*` | `./src/assets/*` |
| `@components/*` | `./src/components/*` |
| `@config` | `./src/config.ts` |
| `@content/*` | `./src/content/*` |
| `@layouts/*` | `./src/layouts/*` |
| `@pages/*` | `./src/pages/*` |
| `@styles/*` | `./src/styles/*` |
| `@utils/*` | `./src/utils/*` |

## Deployment

The site is configured for static deployment. Run `pnpm build` to generate the `./dist/` directory, then deploy the contents of that folder to your hosting platform.

## SEO & Structured Data

- JSON-LD structured data for `Organization` and `WebSite`
- Automatic sitemap generation (`@astrojs/sitemap`)
- Open Graph and Twitter Card meta tags
- Per-page SEO overrides via frontmatter

---

Built with [Astro](https://astro.build/) and [Pages CMS](https://pagescms.org/).
