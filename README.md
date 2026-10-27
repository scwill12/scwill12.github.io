# scwill12.github.io

Serves two things that have to be at the **root** of this domain:

- `/.well-known/apple-app-site-association` — the Apple App Site Association
  file. Universal Links are only validated from the domain root, which on
  GitHub Pages means this repository rather than a project one.
- `/join` — the page an invitation link points at, for anyone who taps it
  without Firelight installed.

`.nojekyll` is required, not decorative: Jekyll skips any directory beginning
with a dot, so without it `.well-known` is never published.

## The one rule for `/join`

It must never read the invitation out of the URL fragment or transmit it.
Everything after `#` stays on the device, which is the only reason the
credential in an invitation link does not reach a server. One analytics call
or one image URL carrying the fragment would undo it. The page has no
JavaScript for that reason.
