# share.perfumeddecay.com

The single dedicated share link for the Perfume(D)ecay word-of-mouth CTA. It
appears in nothing except the in-episode CTA and the show notes, which is the
property the Word-of-Mouth Playbook actually requires: every click on it is
attributable to word of mouth rather than lost in the direct-traffic blob.

The chain is:

    share.perfumeddecay.com  ->  the click counter on the 1070  ->  pod.link/1871658278

## Why a domain we own rather than the counter's own URL

Show notes of a published episode cannot be edited. A link that points straight
at the counter's host can never be repointed, so if that machine is renamed,
retired, or leaves the tailnet, the link dies permanently in every podcast app
that ever cached the episode. This subdomain can be repointed in a minute.

`index.html` and `404.html` are identical on purpose, same as `holeyield-redirect`:
the 404 copy is what keeps a mistyped subpath redirecting instead of dying on a
GitHub 404. Keep them in sync.

## Publishing

GitHub Pages, `main` / root. `CNAME` holds `share.perfumeddecay.com`. DNS is at
Namecheap: one CNAME row on the `share` host pointing to `whole-yield.github.io`.
Do not touch the apex rows; they point at Transistor and serve the real site.

## Before it matters

The counter it points at only counts what reaches it. Verify the whole chain end
to end from a phone on cellular before the first CTA episode publishes, not after.
