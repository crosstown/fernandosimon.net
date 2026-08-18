# fernandosimon.net

Personal site. Single self-contained `index.html` — no build step, no external
requests at runtime (fonts are embedded as base64 `@font-face` data URIs).

## What's on the page

- Animated wave banner (Canvas, layered sine waves — not a video/gif)
- Scroll-triggered slot-machine letter reveal on the name (re-fires each time
  it re-enters the viewport, via `IntersectionObserver`)
- A generated QR code linking to [LinkedIn](https://www.linkedin.com/in/fernandojsimon/)
  (verified against an independent decoder at generation time, not just trusted)
- Respects `prefers-reduced-motion` throughout

## Fonts

- Anton (display)
- JetBrains Mono (nav / ticker / utility text)
- Source Serif 4 (about-section body copy)

All embedded directly in `index.html`; nothing is fetched from Google Fonts
or any CDN at runtime.

## Deployment

Currently hosted on AWS:

- **Domain**: Route 53 (registrar + hosted zone)
- **Content**: S3 bucket (`fernandosimon-net-site`), private, CloudFront-only access
- **CDN / HTTPS**: CloudFront distribution, ACM certificate covering
  `fernandosimon.net` and `www.fernandosimon.net`

Deploys are manual right now — sync `index.html` to the S3 bucket and
invalidate the CloudFront cache. No CI/CD yet.

## Status

Under construction — the about-section copy is a placeholder until there's
real bio content to put there.
