# hercx.ai

Marketing site for Hercx — the hired-gun CTO every founder and CEO can use like a real one.

Static landing using the Hercx seal, Sora + Inter, navy `#090b11`, accent `#2F68FF`.

- Repo: https://github.com/HercxAi/hercx.ai
- Current product page: https://hercx.framer.ai/
- Apex `hercx.ai` still proxies to a Vercel project with **no deployment** (`DEPLOYMENT_NOT_FOUND`)
- Mail is live (`MX 1 smtp.google.com`) — **do not change MX, DKIM, or DMARC**

## Put this site on hercx.ai

Pick **one** origin. Never point the same records at two hosts.

### Cloudflare Pages (fastest — same login as DNS)

1. Cloudflare Dashboard → Workers & Pages → Create → Connect Git → `HercxAi/hercx.ai`
2. Build command: none. Output directory: `/`
3. Custom domains → `hercx.ai` and `www.hercx.ai`
4. Cloudflare will replace the dead Vercel A records. Leave MX alone.

### GitHub Pages

1. This repo → **Settings → Pages**
2. Source: **Deploy from a branch** → `main` / `/ (root)` → Save
3. After https://hercxai.github.io/hercx.ai/ loads, in Cloudflare DNS set **DNS only** (grey cloud):

| Name | Type | Value |
| --- | --- | --- |
| `@` | A | `185.199.108.153` |
| `@` | A | `185.199.109.153` |
| `@` | A | `185.199.110.153` |
| `@` | A | `185.199.111.153` |
| `www` | CNAME | `hercxai.github.io` |

Remove leftover Vercel A/AAAA records. Then Pages → Custom domain `hercx.ai` → Enable HTTPS.

### Existing Framer site (needs a paid Framer plan)

Framer: Site Settings → Hosting → Connect `hercx.ai`. DNS only:

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
