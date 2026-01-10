# Deployment

Frontend:
- GitHub -> Vercel auto deploy

Backend:
- GitHub -> Wrangler deploy

Secrets:
- STRIPE_SECRET_KEY
- STRIPE_WEBHOOK_SECRET
- SENTRY_DSN

Commands:

wrangler deploy
wrangler deploy --config wrangler.saas.toml
