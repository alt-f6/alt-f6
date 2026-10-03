# Ismail Yusifli

**Backend engineer — TypeScript, Python, PostgreSQL.** I build the parts of a product that are expensive to get wrong: billing, payment webhooks, auth and integrations. Then I run them in production.

- **Sole engineer** of the platform behind an online school with **300+ active students a month**: site, CRM, LMS and payments, live since Sep 2025.
- **External client, 2026:** a CRM + LMS now used by **25 staff across 3 branches** to manage 200+ students.
- **Available now** for a long-term remote contract (US or EU hours), ideally on backend or product engineering at an early-stage startup.

📧 ismail.yusifli86@gmail.com · [LinkedIn](https://linkedin.com/in/ismail-yusifli) · [Portfolio](https://yusifli-portfolio.vercel.app)

---

## How I build: decisions from a production system

The school platform's code is private. These are the decisions I'm happy to walk through line by line on a call.

| Problem | What I did |
|---|---|
| Two staff members marking the same lesson at the same moment must never charge a student twice | Balance debits run in `SERIALIZABLE` transactions with a `SELECT … FOR UPDATE` lock on the student row; a conflicting write waits or is rejected, never applied twice |
| A payment webhook can be forged, replayed or delivered twice | Timing-safe token check and the provider's IP allowlist; a unique idempotency key turns a duplicate delivery into a no-op (`P2002`); the payment is re-fetched from the provider's API before any balance changes |
| Login timing can reveal which emails have accounts | Unknown emails still run a bcrypt compare against a dummy hash, so both paths cost the same; login rate limits live in Postgres and survive restarts |
| Paid lessons must not leak through shared links | Lesson content is served only after a per-request enrollment check; storage access goes through short-lived presigned URLs |
| Money rules break silently, not loudly | ~1,500 test cases across 194 test files, plus a 24-check suite that runs the real billing, payment, payroll and lead-conversion code against a live database and asserts the financial invariants |

**Scale of that codebase:** ~80K lines of TypeScript and Python, 43 data models, 28 migrations, three apps (landing, CRM, LMS) behind one edge proxy with cross-subdomain SSO.

---

## Public projects

### [cleanroom](https://github.com/alt-f6/cleanroom) — an AI trading agent that survives prompt injection
Most defenses try to *detect* malicious text. cleanroom makes a successful injection useless instead: the only LLM in the pipeline has **no tools**, and the decision to trade or veto is **deterministic code** checking validated fields against market data. In the project's own benchmark, **0 of 15** hardened injection attacks produced an order, with 53 passing tests. Built for the Alpaca × lablab.ai AI Trading Agents hackathon.
`Python` `FastAPI` `Gemini` `Next.js`

### [luxury-beauty-booking](https://github.com/alt-f6/luxury-beauty-booking) — a live booking funnel for a Baku hair studio
Three-step mobile booking flow in Azerbaijani and Russian: the client lands in a prefilled WhatsApp chat, the studio gets an instant Telegram notification.
`Next.js 16` `React 19` `TypeScript` `Tailwind v4`

---

## Stack

**Backend:** TypeScript, Python, Node.js, Next.js (App Router, Server Actions), FastAPI, AsyncIO, REST, webhooks
**Data:** PostgreSQL (isolation levels, row locks, indexing), Prisma, S3-compatible storage (Cloudflare R2)
**Infra:** Docker, Ubuntu VPS, Caddy, systemd, Git
**Testing:** Vitest, pytest

English C1 · Russian native · Azerbaijani conversational · Telegram [@flames_8](https://t.me/flames_8) · Off the clock: competitive ice hockey
