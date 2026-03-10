# Warm Horizon Care – Frontend (Vercel deploy)

This folder contains **only** the static frontend. Deploy it from a **separate** Git repo to avoid Vercel’s `fsPath` error.

## Deploy steps

1. **Create a new GitHub repo** (e.g. `warm-horizon-care-frontend`). Do not add a README or .gitignore.

2. **Push this folder as that repo:**
   ```bash
   cd "c:\Warm Horizon\warm-horizon-frontend-deploy"
   git init
   git add index.html vercel.json README.md
   git commit -m "Initial frontend"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/warm-horizon-care-frontend.git
   git push -u origin main
   ```
   Replace `YOUR_USERNAME` with your GitHub username or org.

3. **In Vercel:** New Project → Import the new repo (`warm-horizon-care-frontend`).  
   - Root Directory: **leave empty**  
   - Build Command: **leave empty**  
   - Deploy.

4. **Optional:** Point your existing Vercel project to this new repo (Settings → Git → change Connected Git Repository to the new repo), or keep it as a new project and use the new URL.

Your backend stays in the original repo and on Railway; the frontend just needs to call the Railway API URL.
