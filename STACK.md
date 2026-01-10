# FlowRaz Tech Stack

## Core Infrastructure
- Cloudflare Workers (TypeScript)
- Wrangler CLI
- Cloudflare D1 (SQLite) with Drizzle ORM
- Cloudflare KV
- Cloudflare R2

## Backend
- TypeScript only
- Drizzle ORM (no raw SQL)
- Zod validation
- JWT authentication
- Stripe billing integration
- Sentry error monitoring (env-based DSN)

## Frontend
- React
- Vite
- TypeScript
- Hosted on Vercel
- API via VITE_API_BASE_URL

## SaaS Architecture
- Multi-tenant + single-tenant modes
- Widget embed support
- WordPress / Elementor integration
- GitHub as source of truth

## Dev Tools
- Cursor IDE
- GitHub Copilot / Codex
- GitHub for version control
- Cloudflare for infra
- Vercel for frontend hosting

## Principles
- No raw SQL
- Type-safe by default
- Step-by-step migrations
- Performance-first
- Clean architecture
- AI-assisted development
