# Make the Vercel page show content – step by step

Follow these in order. After each step, check the Vercel URL.

---

## Step 1: Deploy the latest code

1. Open PowerShell and run:
   ```powershell
   cd "c:\Warm Horizon\warm-horizon-frontend-deploy"
   git add index.html
   git status
   ```
   You should see `index.html` as modified.

2. Commit and push:
   ```powershell
   git commit -m "Fix blank page: safe localStorage and error handling"
   git push
   ```

3. In **Vercel**: open your **warm-horizon-care-frontend** project → **Deployments**. Wait until the latest deployment shows **Ready** (green). If it fails, open it and check **Logs**.

---

## Step 2: Confirm what Vercel is serving

1. Open your Vercel site URL (e.g. `https://warm-horizon-care-frontend.vercel.app`).

2. **View Page Source** (right‑click → “View Page Source”, or Ctrl+U). You should see:
   - Full HTML with `<title>Warm Horizon Care...</title>`
   - `<div id="app">` with “Loading…” inside
   - A long `<script>` block with your app code

   If you see that, the correct `index.html` is being served. If the source is empty or different, the wrong project or branch is deployed.

---

## Step 3: Check the browser console for errors

1. On the same Vercel page, open **Developer Tools** (F12).
2. Go to the **Console** tab.
3. Refresh the page (F5).

   - If you see **red errors**, copy the full message and the file/line (if shown). Fix or share that error.
   - If there are no red errors but the page is still blank, look for yellow warnings (e.g. blocked scripts or mixed content).

---

## Step 4: Vercel project settings

In Vercel → your frontend project → **Settings**:

1. **General**
   - **Root Directory**: leave **empty** (this repo has only the frontend).

2. **Build and Deployment**
   - **Framework Preset**: **Other**
   - **Build Command**: leave **empty**
   - **Install Command**: leave **empty**
   - **Output Directory**: leave **empty**

3. **Git**
   - **Production Branch**: `main` (or the branch you push to).

Save if you changed anything, then trigger a **Redeploy** from the **Deployments** tab.

---

## Step 5: Test in a private/incognito window

1. Open a **new incognito/private** window.
2. Go to your Vercel URL again.

   If it works in incognito but not in your normal window, clear **cache and site data** for the Vercel domain in your browser (e.g. Settings → Privacy → Clear data for that site), then reload.

---

## Step 6: If the page is still blank

1. **Exact URL you’re opening**  
   Make sure it’s the URL of the **frontend** project (e.g. `...warm-horizon-care-frontend.vercel.app`), not the old monorepo project that had the fsPath error.

2. **What you see**
   - Do you see “Loading…” and then it goes blank? → Likely a JavaScript error after the first render; use the Console (Step 3).
   - Do you see “Something went wrong” and a message? → That’s the catch block; the message is the error to fix.
   - Completely white with no text? → Check Step 2 (source) and Step 4 (settings).

3. **Share**
   - Result of **View Page Source** (does it show the full Warm Horizon HTML?).
   - Any **red errors** from the Console (copy the full text).
   - A screenshot of the **Vercel Deployment** and **Build and Deployment** settings (with secrets blurred).

---

## Summary checklist

| # | Action |
|---|--------|
| 1 | Push latest `index.html` and wait for Vercel deploy to be Ready |
| 2 | View Page Source and confirm it’s the full Warm Horizon HTML |
| 3 | Open Console (F12), refresh, note any red errors |
| 4 | Settings: Root Directory empty, Framework Other, no Build/Install command |
| 5 | Try incognito and/or clear cache for the Vercel domain |
| 6 | If still blank: note exact URL, what you see, and Console errors |
