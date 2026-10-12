# Frontend — Svelte / Vite

[Project](../README.md) · [한국어](README.ko.md) · [Interface walkthrough](../docs/wiki/UI-UX.md)

The Korean interface supports image-based onboarding, product browsing, likes and refreshed recommendations. Interface strings and screenshots remain unchanged.

## Historical setup

Install Node.js; the team's environment used `conda install nodejs`. From the repository root:

```bash
cd frontend
npm install
npm run dev
```

`package.json` defines scripts/dependencies; `vite.config.js` defines development configuration. Backend data/model settings must be available for the complete service.
