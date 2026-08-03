# share.perfumeddecay.com

Per-episode share links for the Perfume(D)ecay word-of-mouth CTA.

    share.perfumeddecay.com/pd11  ->  click counter on the 1070 (?e=pd11)  ->  pod.link/1871658278

Each Season 2 episode has its own path, so clicks are attributable to the
episode that earned them, not just to the season.

## Why the ROOT does not redirect, and must never redirect again

Issuing a TLS certificate publishes the hostname to public Certificate
Transparency logs. Scanners watch those logs and probe brand-new hostnames
within minutes; they follow redirects and they SPOOF real browser user agents.
On 2026-08-03 the root redirected to the counter, and within one hour the
counter had logged 7 "unique humans" from DigitalOcean, Cogent and assorted
RIPE hosting ranges, with Dutch and Japanese Accept-Language headers, against a
kill-test threshold of 5. It read PASS before a single listener existed.

Scanners learn the HOSTNAME from the certificate log. They do not learn the
PATH. So the root and the 404 page are deliberately inert: they link onward for
a human but never touch the counter. Only /pdNN counts.

Do not "simplify" this by making the root redirect again.

## Residual risk, stated honestly

/pd11 is not secret once the episode publishes; it is printed in the show notes
and the RSS feed. This design defeats the certificate-log scanning wave, which
is what actually happened, but not a crawler that later reads the published feed
and follows links. If counts drift upward with no plausible sharing behind them,
that is the next thing to suspect, and the fix is classifier hardening rather
than more obscurity.

## Adding an episode

Copy any `pdNN/index.html`, change both `?e=pdNN` occurrences. Season 2
(pd11 to pd21) already exists.

## Publishing

GitHub Pages, `main` / root. `CNAME` holds `share.perfumeddecay.com`. DNS is a
CNAME at Namecheap on the `share` host to `whole-yield.github.io`. The apex rows
point at Transistor and serve the real site; leave them alone.

Note: GitHub only requests the TLS certificate when the custom domain is SET.
Re-PUTting the same value is a no-op. If a certificate is ever stuck at "not
requested", REMOVE the custom domain and RE-ADD it.
