# Bagi Job — Maintenance Page

This repository contains a single static maintenance page in `public/` designed to be deployed to Vercel. The included `vercel.json` routes all requests to `index.html` and returns HTTP 503 with a `Retry-After` header so crawlers know this is temporary downtime.

Files of interest
- `public/index.html` — maintenance page
- `public/style.css` — styles
- `public/logo-C6iNSJ5X.png`, `public/tab3.jpeg` — brand assets (ensure these exist)
- `vercel.json` — Vercel routing + status config

Quick deploy (recommended):

1) Install Vercel CLI (if not already):

```powershell
npm i -g vercel
```

2) From the project root, run:

```powershell
vercel login
vercel --prod
```

This will upload the repository and deploy the static site. Vercel will use `vercel.json` to return 503 for routes and serve the `index.html` file.

GitHub integration:

- Connect this repository to Vercel in the Vercel dashboard. Every push to the connected branch will create a deployment.
- Ensure `public/` is included in the repo and the assets (`logo-C6iNSJ5X.png`, `tab3.jpeg`) are committed.

Notes & tips
- The `vercel.json` `status` field sets the response status code for the route; Vercel will respond with that code and the content of `dest`.
- `retry-after` in `vercel.json` is set to `3600` seconds (1 hour); change it if needed.
- If you prefer a temporary maintenance deployment, you can deploy this project and then point your production domain to the deployment in Vercel DNS settings.
