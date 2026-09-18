# Deployment guide

This is the full source of the invisible Facebook-in-app-browser → Google Drive PDF redirect app (TanStack Start + Vite + Tailwind v4).

## Option 1 — Keep building in Lovable (recommended)

1. In Lovable, open the **+ menu** in the chat input → **GitHub → Connect project**.
2. Authorize the Lovable GitHub App, pick your account, and click **Create Repository**.
3. Lovable pushes the full source to a new repo and keeps it in two-way sync — every change in Lovable lands on GitHub and vice versa. This is the simplest path and keeps Lovable's hosting.

## Option 2 — Self-host from GitHub (Cloudflare Workers)

The app targets the Cloudflare Workers (edge) runtime.

1. Push this repo to GitHub (see steps below).
2. Clone it locally and install dependencies with Bun: `bun install`
3. Build: `bun run build`
4. Deploy: `npx wrangler deploy`

Environment variables/secrets used by the app must be configured in your hosting environment (this project currently reads none at runtime — the Google Drive file ID is embedded in `src/routes/index.tsx`).

## Pushing to a GitHub repo from your machine

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<your-user>/<your-repo>.git
git push -u origin main
```

`node_modules`, build output, and logs are already excluded via `.gitignore`.
