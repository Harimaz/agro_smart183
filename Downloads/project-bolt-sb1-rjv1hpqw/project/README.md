# Portfolio (Vite + React + TypeScript)

This folder contains a Vite + React TypeScript portfolio site. The repository is configured to deploy automatically to Netlify using the Netlify GitHub App (no repository secrets required).

Summary
- Local development with Vite
- Production build with `npm run build`
- Automatic deploys on pushes to `main` via the Netlify GitHub App
- Branch deploy previews enabled (push any branch to get a preview site)

Quick start — local development

1. Install dependencies and start the dev server:

```powershell
cd project
npm install
npm run dev
# Open http://localhost:5173/
```

2. Build and locally preview production:

```powershell
cd project
npm run build
npm run preview
# Open the URL printed by Vite (usually http://localhost:4173/)
```

Netlify (recommended) — connect using the GitHub App (no secrets)

1. Go to Netlify and sign in.
2. Click "Add new site" → "Import an existing project".
3. Choose GitHub, then select the repository.
   - When prompted, install or authorize the Netlify GitHub App for your account/organization and grant access to this repository.
4. In the Netlify site settings (Build & deploy → Continuous Deployment → Build settings):
   - Build command: `npm run build`
   - Publish directory: `dist`
   Netlify will automatically detect the root `project/` build settings in many cases; if your project is in a subdirectory, set the base directory to `project` in Netlify's site settings.
5. Enable Branch deploys / Deploy Previews in Netlify (Build & deploy → Deploy contexts) to get live previews for pull requests and branch pushes.

Notes about contexts
- `netlify.toml` includes settings for `production`, `deploy-preview`, and `branch-deploy` so Netlify builds previews with `NODE_ENV=development` and production with `NODE_ENV=production`.

Manual deploy (optional)

If you prefer to deploy manually from your machine, you can use the Netlify CLI:

```powershell
npm install -g netlify-cli
cd project
npm run build
netlify deploy --dir=dist --prod --site <SITE_ID>
```

Commit and push these changes

Run these commands from the repo root to create a commit and push to `main`:

```powershell
git add project/netlify.toml project/README.md .github/workflows/netlify-deploy.yml
git commit -m "Use Netlify GitHub App + branch previews; add README"
git push origin main
```

If you'd like, I can remove the workflow file (so GitHub Actions no longer tries to deploy). Currently the repository does not require any secrets when you connect via the GitHub App.

Need help connecting Netlify to GitHub? I can walk through the Netlify UI steps, or prepare screenshots/commands for you.
