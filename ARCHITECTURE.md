# FlowRaz Architecture

Frontend:
- React + Vite + TypeScript on Vercel

Backend:
- Cloudflare Workers (TypeScript)
- Cloudflare D1 (SQLite) via Drizzle ORM
- Cloudflare KV
- Cloudflare R2

Auth:
- JWT

Billing:
- Stripe

Monitoring:
- Sentry

Data flow:
Browser -> Vercel Frontend -> Worker API -> D1/KV/R2 -> Response
