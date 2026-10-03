# Ismail Yusifli — Backend Engineer

TypeScript · Python · PostgreSQL — payments, auth, integrations.

I build backends that handle money and concurrency correctly, and I run them in production. Since Sep 2025 I have been the sole engineer of the platform behind an online school with **300+ active students a month**: public site, CRM, LMS and payments. In 2026 I also built a CRM + LMS for an external client now used by **25 staff across 3 branches**.

**Available now** for a long-term remote contract, US or EU hours.

## Engineering decisions I can walk you through

The school platform is private, so here is what it does and why, instead of a link:

- **Balance debits can't double-spend.** Two admins marking the same lesson at the same moment must not charge twice. Debits run in `SERIALIZABLE` transactions with `SELECT … FOR UPDATE` on the balance row, so concurrent writes serialize or retry instead of corrupting the ledger.
- **A payment is credited once, and only if it's real.** The YooKassa webhook handler checks a timing-safe HMAC and an IP allowlist, writes an idempotency key under a unique constraint (a duplicate delivery hits `P2002` and is ignored), then re-fetches the payment from the provider's API before changing any state. The webhook body is never trusted on its own.
- **Login doesn't leak who has an account.** Unknown emails still pay the cost of a dummy bcrypt compare, so response time is the same either way; rate limits live in the database and survive restarts.
- **Paid video stays paid.** Every presigned storage URL and every embed from 6 video providers passes a per-request access check against the student's enrollment.
- **Business rules are tested as rules.** 426 integration tests, including 24 business-invariant checks on billing and payroll. Strict TypeScript, zero `tsc` errors.

## Public projects

| Project | What it proves | Stack |
|---|---|---|
| [cleanroom](https://github.com/alt-f6/cleanroom) | An LLM trading agent that stays safe even when its reading model is fully hijacked: the model has no tools, and the trade/veto decision is deterministic code. 0 of 15 hardened injection attacks got through; 53 tests. Built for the Alpaca × lablab.ai AI Trading Agents hackathon. | Python, FastAPI, Gemini, Next.js |
| [luxury-beauty-booking](https://github.com/alt-f6/luxury-beauty-booking) | Mobile-first booking app for a hair-colorist studio, with Telegram notifications | Next.js 15, TypeScript, Tailwind v4 |

## Stack

**Backend:** TypeScript, Python, Node.js, Next.js (App Router, Server Actions), FastAPI, AsyncIO, REST, webhooks
**Data:** PostgreSQL (isolation levels, row locks, indexing), Prisma, S3-compatible storage (Cloudflare R2)
**Infra:** Docker, Ubuntu VPS, Caddy, systemd, Git
**Testing:** Vitest, pytest

## Contact

- Email: ismail.yusifli86@gmail.com
- LinkedIn: [linkedin.com/in/ismail-yusifli](https://linkedin.com/in/ismail-yusifli)
- Portfolio: [yusifli-portfolio.vercel.app](https://yusifli-portfolio.vercel.app)
- Telegram: [@flames_8](https://t.me/flames_8)

English C1 · Russian native · Azerbaijani conversational. Off the clock: competitive ice hockey.
