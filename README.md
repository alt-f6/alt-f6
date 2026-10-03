# Ismail Yusifli — Backend Engineer

TypeScript · Python · PostgreSQL — payments, auth, integrations.

I build and run production backends end to end: schema design, concurrency, payment webhooks, auth and deployment. Since Sep 2025 I have been the sole engineer behind the platform of an online school with **300+ active students a month**, and I have shipped CRM, LMS and messaging systems for **3 external clients**.

Open to a long-term remote contract (US/EU hours).

## What I'm good at

- **Money that never goes wrong.** Race-safe balance debiting with PostgreSQL `SERIALIZABLE` transactions and `SELECT … FOR UPDATE` row locks; payment webhooks with timing-safe HMAC, IP allowlists, idempotency keys and server-side re-verification.
- **Auth and access control.** Cross-subdomain SSO, RBAC, DB-backed rate limiting, anti-enumeration login, per-request checks on presigned storage URLs.
- **Integrations.** Webhooks, REST APIs, messaging bots (Telegram, MAX), Google Sheets sync, payment providers.
- **Tests that guard the business.** Vitest integration suites with business-invariant checks; strict TypeScript with zero `tsc` errors.

## Selected work

| Project | What it shows | Stack |
|---|---|---|
| [cleanroom](https://github.com/alt-f6/cleanroom) | LLM trading agent built to survive prompt injection from untrusted financial text (Alpaca AI Trading Agents hackathon) | Python, FastAPI, Next.js |
| [webhook-service-max](https://github.com/alt-f6/webhook-service-max) | Production webhook service syncing a client's CRM with MAX messenger | Python, FastAPI, aiogram |
| [luxury-beauty-booking](https://github.com/alt-f6/luxury-beauty-booking) | Mobile-first booking web app for a hair-colorist studio | Next.js 15, TypeScript, Tailwind v4 |

## Stack

**Backend:** TypeScript, Python, Node.js, Next.js (App Router, Server Actions), FastAPI, AsyncIO, REST, webhooks
**Data:** PostgreSQL (isolation levels, row locks, indexing), Prisma, S3-compatible storage (Cloudflare R2)
**Infra:** Docker, Ubuntu VPS, Caddy, systemd, Git
**Testing:** Vitest (unit, integration, invariant tests)

## Contact

- Email: ismail.yusifli86@gmail.com
- LinkedIn: [linkedin.com/in/ismail-yusifli](https://linkedin.com/in/ismail-yusifli)
- Portfolio: [yusifli-portfolio.vercel.app](https://yusifli-portfolio.vercel.app)
- Telegram: [@flames_8](https://t.me/flames_8)

Outside of code I play competitive ice hockey.
