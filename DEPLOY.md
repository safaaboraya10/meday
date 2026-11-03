# Free Deployment (Render + Vercel)

- **Backend** → Render free plan (`render.yaml`)
- **Frontend** → Vercel free plan (`vercel.json`)

Total cost: $0. No credit card needed.

> Free Render sleeps after 15 min idle → the first visit takes ~50 s to wake up.
> Data added on the live site (bookings, admin edits) resets on each restart/redeploy.

---

## 0. Put the repo on your own GitHub
The repo is on your partner's account. Fork it (GitHub → **Fork**), or push it to a new repo of yours.

## 1. Backend on Render
1. Sign in at https://render.com with GitHub.
2. **New → Blueprint** → pick your repo → Render reads `render.yaml`.
3. Fill in the secret values it asks for:
   | Key | Value |
   |---|---|
   | `GEMINI_API_KEY` | your Gemini key (https://aistudio.google.com/apikey) |
   | `GOOGLE_CLIENT_ID` | same as `VITE_GOOGLE_CLIENT_ID` in your local `.env` |
   | `ADMIN_PASSWORD` | a strong password for the `admin` login |
4. **Apply** → wait for the deploy → copy the URL, e.g. `https://meday-backend.onrender.com`.
5. Check: open `<that URL>/docs` → you should see the API page.

## 2. Frontend on Vercel
1. Sign in at https://vercel.com with GitHub.
2. **Add New → Project** → import the same repo (framework: Vite, auto-detected).
3. **Environment Variables**:
   | Key | Value |
   |---|---|
   | `VITE_API_BASE_URL` | the Render URL from step 1 (no trailing `/`) |
   | `VITE_GOOGLE_CLIENT_ID` | from your local `.env` |
4. **Deploy** → you get e.g. `https://meday.vercel.app`.
   (Optional: Project → Settings → Domains → rename it.)

## 3. Google login
Google Cloud Console → APIs & Services → Credentials → your OAuth client →
**Authorized JavaScript origins** → add your Vercel URL → Save.

## 4. Resume
- Live demo: your Vercel URL
- Add a 1–2 min demo video (Loom/YouTube) as a backup for the 50 s wake-up.
- Tip: open the site once before an interview so it's awake.
