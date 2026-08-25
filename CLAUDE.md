<!-- drafted by wy-claudify using claude-haiku-4-5-20251001; review before trusting -->
# CLAUDE.md

## What this is
Static GitHub Pages site serving per-episode share links for Perfumed Decay podcast. Each path `/pdNN` redirects through a click counter to the actual pod.link URL. **Critical:** the root and 404 page are deliberately inert to avoid triggering certificate-transparency scanners; never make them redirect.

## How to deploy
Push to `main` branch. GitHub Pages deploys automatically to `share.perfumeddecay.com` via CNAME. Custom domain is set in GitHub Pages settings; if TLS certificate is stuck "not requested", remove and re-add the custom domain setting.

## Test files
No test files found in this repo.

## Layout
- `index.html`, `404.html`: static pages, must not redirect to counter (defeats cert-log scanners)
- `pdNN.html` (pd11 through pd21): episode redirect files
- `CNAME`: points to `whole-yield.github.io`
- DNS at Namecheap: `share` CNAME to `whole-yield.github.io`; apex rows point to Transistor (do not touch)

## Adding an episode
1. Copy any existing `pdNN.html`
2. Change both `?e=pdNN` query parameters to the new episode number
3. Use flat filename (no directory), so GitHub Pages serves `/pdXX` directly without a 301 hop

## Critical gotchas
- Root must never redirect: scanners learn hostname from Certificate Transparency logs and probe within minutes with spoofed user agents. On 2026-08-03, root redirect logged 7 "unique" non-humans in under an hour. The root and 404 are inert to humans by design.
- Paths like `/pdNN` are printed in show notes and RSS; once published they are not secret. If click counts spike without organic sharing, suspect crawler following the published feed, not cert-log scanning.
