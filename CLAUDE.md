<!-- drafted by wy-claudify using claude-haiku-4-5-20251001; review before trusting -->
# share.perfumeddecay.com

Static GitHub Pages redirect site for Perfumed Decay Season 2 episode share links. Each `/pdNN` path counts clicks before redirecting to pod.link. The root and 404 pages are deliberately inert to avoid triggering certificate scanners.

## How to run it

GitHub Pages handles this automatically. Deploy by pushing to `main` branch. Domain is configured via CNAME file (`share.perfumeddecay.com`) and DNS (Namecheap CNAME to `whole-yield.github.io`).

## How to test it

No test command found in this repo. Verify manually: `/pdNN` paths should hit the counter on the 1070 with `?e=pdNN` parameter before redirecting to pod.link. The root `/` and `/404.html` must never reach the counter.

## Layout

- `pdNN.html` (pd11-pd21): flat HTML files serving as `/pdNN` paths. Each contains two `?e=pdNN` references that must be changed when copying to a new episode.
- `index.html`: root page, deliberately inert with links only.
- `404.html`: error page, deliberately inert.
- `CNAME`: holds `share.perfumeddecay.com`.

## Critical: Root and 404 must never redirect

Root redirects trigger Certificate Transparency scanners within minutes. They spoof user agents and pollute click counts. Only `/pdNN` paths hit the counter.

## Adding an episode

Copy an existing `pdNN.html`, rename it (e.g., `pd22.html`), and change both `?e=pdNN` occurrences to `?e=pd22`. Files must be flat (no subdirectories) so GitHub Pages serves them without a 301 hop.

## Deployment gotchas

- GitHub only requests a TLS certificate when the custom domain is SET. If stuck at "not requested", remove the custom domain in settings and re-add it.
- Re-PUTting the same CNAME value is a no-op; only adding/removing triggers a cert request.
