# FORMA STUDIO V3

Production: https://forma-studio-site.pages.dev/

This repository deploys automatically to Cloudflare Pages (branch main, no build command, output /).

## Demos
- /bloome/ — flower storefront with search, filters, sorting, cart, favorites where relevant and demo checkout.
- /motorwerk/ — service catalog, vehicle-dependent estimate, demonstration appointment form.
- /forma-living/ — furniture catalog and formula-based estimator with saved parameters.
- /atelier-object/ — object store with favorites, cart and demo checkout.

All demo products, services, prices and images are illustrative. No payments or real appointments are processed.

## Lead form setup (not active without secrets)
The POST /api/lead endpoint is implemented in functions/api/lead.js. In Cloudflare Pages > Settings > Variables and Secrets add:
- TELEGRAM_BOT_TOKEN (secret): token from a Telegram bot created by the studio owner.
- TELEGRAM_CHAT_ID (secret): destination chat ID for the studio owner's bot notifications.
- TURNSTILE_SECRET (recommended secret): Cloudflare Turnstile secret; client-side widget must also be configured before enabling this validation.
- RATE_LIMIT_KV (recommended KV binding): KV namespace used for basic rate limiting; stronger production controls should use WAF rate limiting and/or Durable Objects.

Redeploy after setting secrets. Test a real form submission and verify the notification is received before considering the form operational. Without secrets, API responds with 503 and no false success.

The frontend does not store or log lead data. Add a privacy notice and retention policy appropriate to applicable laws before accepting production submissions.

## Known limitations
- The four demos are interactive prototypes, not integrated with payment gateways or real back offices.
- Photo assets are externally hosted and must be licensed/verified and ideally self-hosted before commercial use.
- Mobile visual regression, Lighthouse and cross-browser QA are not yet fully completed.
- Case pages embed live responsive pages, not actual screenshot files.
- No real customer cases or testimonials are claimed.
