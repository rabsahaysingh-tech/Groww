# SIP Explainer and Discovery Agent (public version)

Two pages, one small server function that keeps your API key secret.

- `/`            SIP Explainer (MVP)
- `/discovery.html`  Discovery agent
- `/api/claude`  server function (uses ANTHROPIC_API_KEY)

## Deploy on Vercel (about 10 minutes)
1. Put this folder in a new GitHub repository (or use the Vercel CLI: `npm i -g vercel`, then `vercel` in this folder).
2. On vercel.com, click Add New > Project and import the repository. Leave build settings as they are.
3. Before deploying, open Settings > Environment Variables and add `ANTHROPIC_API_KEY` with your key from console.anthropic.com.
4. Deploy. Your site is at `https://<project>.vercel.app`.
5. In the Anthropic console, set a monthly spend limit for the key.

Optional variables: `RATE_LIMIT_PER_10MIN` (default 120 requests per visitor) and `DAILY_CAP` (default 3000 requests per day).

## Test it
- Open `/`, click a sample question, press Explain. Then open Quality evaluation and run it (about 60 requests).
- Open `/discovery.html`, upload a CSV of raw feedback, click Analyse raw feedback with AI.
- Open both links in an incognito window to confirm they work for strangers.

Note: limits are held in memory per server instance, so they are a safety net, not exact accounting. The spend limit in step 5 is your real protection.
