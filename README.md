# SoccerAI Numbers — live-site starter

This is a deployable live-site starter, not a hosted website yet. Deploy to Vercel (or another Node host), configure environment variables, and connect a football data provider.

## Included
- Responsive live site frontend in `public/index.html`
- Serverless API endpoints for fixtures and odds proxying
- Demo-safe fallback when provider credentials are absent
- Local paper-pick tracker
- No provider API key exposed to the browser

## Deploy to Vercel
1. Create a Vercel account and import this folder as a project (or upload it using a supported Git workflow).
2. In Project Settings → Environment Variables, set:
   - `FOOTBALL_DATA_API_KEY` — API key from football-data.org (fixtures/competition data; odds are not provided by this key)
   - `ODDS_API_KEY` — optional API key from The Odds API for odds
3. Deploy.
4. Open the deployed HTTPS URL on your iPhone in Safari. Use Share → Add to Home Screen if desired.

## Data-provider notes
- `/api/matches` queries football-data.org when `FOOTBALL_DATA_API_KEY` is configured. Provider coverage, competition access and rate limits depend on your plan.
- `/api/odds` queries The Odds API when `ODDS_API_KEY` is configured. Event coverage and bookmaker markets depend on your plan.
- Without keys, endpoints return explicitly labelled sample data so the UI remains usable.
- API terms and licensing apply. Do not scrape bookmakers or expose API keys in HTML.

## Production requirements still to add
A scheduled server job (e.g. Vercel Cron) for reliable daily sync, a database for multi-device accounts/history, real model inference and evaluation, push notification service, and any auth/consent/privacy requirements. A static browser page cannot reliably update while closed.
