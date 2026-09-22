# Joshua Brewer Portfolio

A static-first personal engineering portfolio built with Astro and TypeScript. It uses no backend or tracking scripts, and all interactive demonstrations are fictional and sanitized.

## Local development

```bash
npm install
npm run dev
```

Run verification before publishing:

```bash
npm run format:check
npm test
npm run build
```

## Deploy

The site produces static files in `dist/` and can be deployed to Cloudflare Pages, GitHub Pages, or Vercel. Set the production URL in `astro.config.mjs` before deploying if it differs from `https://joshuabrewer.dev`.

For Cloudflare Pages, use build command `npm run build` and output directory `dist`. For Vercel, the Astro framework preset works without further configuration.

## Content and public artifacts

Page content is intentionally kept in `src/pages/` and `src/data/` so it can be moved into Astro content collections as notes and project case studies are published. The public resume source lives in `public/resume/joshua-brewer-resume.md`; its companion PDF is linked from the Resume page.

The GitHub Actions workflow runs formatting, type checks, and a production build on pushes and pull requests.
