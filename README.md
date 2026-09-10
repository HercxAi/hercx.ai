# hercx.ai

Marketing site for Hercx — AI expert for non-technical CEOs.

Static landing using the live Framer identity (Sora + Inter, navy `#090b11`, accent `#2F68FF`) and existing product copy. Wordmark only until Grok-bot logo files are supplied.

- Source: https://github.com/HercxAi/hercx.ai
- Current product page: https://hercx.framer.ai/
- Apex `hercx.ai` is on Cloudflare and still proxies to a Vercel project with **no deployment** (`DEPLOYMENT_NOT_FOUND`). Mail (`MX 1 smtp.google.com`) is live — do not change it.

## Go live on hercx.ai (one DNS change)

Pick **one** origin. Never point the same records at two hosts. **Do not touch MX, DKIM, or DMARC.**

### A — Cloudflare Pages (recommended, same registrar)

1. Cloudflare Dashboard → Workers & Pages → Create → Connect Git → `HercxAi/hercx.ai`
2. Build command: none. Output directory: `/`
3. Custom domains → `hercx.ai` and `www.hercx.ai`
4. Cloudflare will replace the dead Vercel A records. Leave MX alone.

### B — GitHub Pages custom domain

This repo deploys to GitHub Pages from `main`. After the first green Actions run:

1. Confirm https://hercxai.github.io/hercx.ai/ loads
2. In Cloudflare DNS, **grey cloud / DNS only**:

| Name | Type | Value |
| --- | --- | --- |
| `@` | A | `185.199.108.153` |
| `@` | A | `185.199.109.153` |
| `@` | A | `185.199.110.153` |
| `@` | A | `185.199.111.153` |
| `www` | CNAME | `hercxai.github.io` |

3. Remove leftover Vercel A/AAAA records on the apex.
4. In the repo: Settings → Pages → Custom domain `hercx.ai` → enable HTTPS.

### C — Point the existing Framer site at hercx.ai

Needs a paid Framer plan. In Framer: Site Settings → Hosting → Connect `hercx.ai`. Then DNS-only:

| Name | Type | Value |
| --- | --- | --- |
| `@` | A | `31.43.160.6` |
| `@` | A | `31.43.161.6` |
| `www` | CNAME | `sites.framer.app` |

## Brand tokens

- Display: Sora · Body: Inter
- Navy: `#090b11` `#0b0f17` `#0d121c` `#111722`
- Accent: `#2F68FF` `#3E78FF` `#7FA2FF`
- Ice: `#F7F9FF` `#EAF0FF`
- Slate: `#65728A` `#7A879E`
