# hercx.ai

Marketing site for Hercx — AI expert for non-technical CEOs.

This repo is a static landing that reuses the live Framer site identity
(Sora + Inter, navy `#090b11`, accent `#2F68FF`) and existing copy.
No new logo was invented. Drop Grok-bot brand assets here when ready.

Live today:
- Product page: https://hercx.framer.ai/
- Domain: https://hercx.ai/ currently 404s (Cloudflare proxy → dead Vercel deployment)

## Option A — Point hercx.ai at the existing Framer site (fastest)

Needs a paid Framer plan.

1. In Framer: Site Settings → Hosting → Domains → Connect a domain you own → `hercx.ai`
2. In Cloudflare DNS for `hercx.ai`, set records to **DNS only** (grey cloud, not proxied):

| Name | Type | Value |
| --- | --- | --- |
| `@` | A | `31.43.160.6` |
| `@` | A | `31.43.161.6` |
| `www` | CNAME | `sites.framer.app` |

3. Remove the current proxied A/AAAA records that send apex traffic to the dead Vercel origin.
4. **Do not touch MX** (`smtp.google.com`) or existing Google DKIM / Cloudflare DMARC TXT records. That mail (`hello@hercx.ai`, `jeff@hercx.ai`) stays live.

Notes:
- `www.hercx.ai` currently does not resolve. The CNAME above creates it.
- Framer does not use IPv6 AAAA records; extra AAAA rows can block SSL.
- DNS usually settles in minutes, sometimes up to 24 hours.

## Option B — Host this repo on Cloudflare Pages (same registrar)

1. Cloudflare Dashboard → Workers & Pages → Create → Pages → Connect Git → `HercxAi/hercx.ai`
2. Build command: none. Output directory: `/`
3. Custom domains → `hercx.ai` and `www.hercx.ai`
4. Keep MX / DKIM / DMARC records as-is.

## Option C — Attach this repo to a new Vercel project

`hercx.ai` already reaches a Vercel edge error (`DEPLOYMENT_NOT_FOUND`).
Create a fresh Vercel project from this repo and add the domain there.
Still keep MX records in Cloudflare.

## Brand tokens from the live Framer site

- Display: Sora
- Body: Inter
- Navy: `#090b11` `#0b0f17` `#0d121c` `#111722`
- Accent: `#2F68FF` `#3E78FF` `#7FA2FF`
- Ice: `#F7F9FF` `#EAF0FF`
- Slate: `#65728A` `#7A879E`
