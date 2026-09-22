# Joshua Brewer Portfolio

A static-first personal engineering portfolio built with Astro and TypeScript. It uses no backend,
database, authentication, or tracking scripts, and every interactive demonstration (the incident
simulator, the architecture explorer) is clearly labeled fictional and sanitized.

## Local development

```bash
npm install
npm run dev
```

Run verification before publishing:

```bash
npm run format:check
npm test        # runs astro check (type checking)
npm run build   # runs astro check, then astro build
```

## Content

- Page content and copy live in `src/pages/` and `src/data/site.ts`.
- **Notes** are real Markdown content collection entries in `src/content/notes/*.md`, with
  frontmatter (`title`, `description`, `category`, `status: draft | planned`, `date`) validated by
  the schema in `src/content.config.ts`. To add a note, drop a new `.md` file in that folder — it
  is picked up automatically by `/notes/` and gets its own `/notes/<slug>/` page.
- The public resume source lives in `public/resume/joshua-brewer-resume.md`; its companion PDF is
  linked from the Resume page.

## Deploying to GitHub Pages

This repo is configured to deploy to GitHub Pages via GitHub Actions
(`.github/workflows/deploy.yml`), which builds the site and publishes `dist/` on every push to
`main`.

**One-time repo setup:**

1. In the GitHub repo, go to **Settings → Pages** and set **Source** to **GitHub Actions**.
2. Push to `main` (or run the "Deploy to GitHub Pages" workflow manually from the Actions tab).
3. The site becomes available at the Pages URL GitHub assigns once the workflow completes.

**Custom domain (joshuabrewer.tech via Cloudflare DNS):**

The site is configured for a custom domain: `astro.config.mjs` sets `site` to
`https://joshuabrewer.tech`, and `public/CNAME` contains `joshuabrewer.tech`. This repo does not
have a `base` path configured, because a custom domain serves from the root — if you ever deploy
without a custom domain (e.g. to `https://<username>.github.io/<repo>/`), add
`base: '/<repo-name>/'` to `astro.config.mjs` and update the `CNAME` file/removal accordingly.

To point the domain at GitHub Pages:

1. In Cloudflare DNS for `joshuabrewer.tech`, add a `CNAME` record at the apex (`@`) pointing to
   `jbrewer3.github.io`, with the proxy status set to **DNS only** (grey cloud) — GitHub Pages
   issues its own TLS certificate and works most predictably without Cloudflare's proxy in front
   of it.
2. In the GitHub repo's **Settings → Pages**, add `joshuabrewer.tech` as the custom domain and
   wait for DNS verification, then enable **Enforce HTTPS**.
3. Confirm `public/CNAME` still contains `joshuabrewer.tech` after any future deploy (GitHub Pages
   removes the custom domain if this file goes missing from a deploy).

No DNS changes or GitHub repo settings are made automatically by this codebase — the steps above
are manual and only need to be done once.

## Quality gates

`.github/workflows/ci.yml` runs on every push and pull request: `npm ci`, Prettier format check,
Astro type checking, and a production build. `.github/workflows/deploy.yml` runs the same checks
before publishing to Pages.
