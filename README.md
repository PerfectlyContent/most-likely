# Most Likely / מי הכי? — party game

A bilingual (EN/HE) real-time "who's most likely to…" party game.
Everyone joins from their own phone via a room code / QR. Backend: Supabase.

## Structure
- `www/index.html` — the entire game (self-contained: HTML/CSS/JS, talks to Supabase).
- `render.yaml` — Render static-site blueprint (serves `www/`).
- Phase 2 will add Capacitor (`ios/`, `android/`) to ship native apps that wrap `www/`.

---

## Phase 1 — Deploy the web version to Render (do this now)

### 1. Put this folder under git and push to GitHub
```bash
cd most-likely
git init
git add .
git commit -m "Most Likely — web build"
# create the repo (either on github.com/new, or with gh):
gh repo create most-likely --public --source=. --push
# ...or if you made the empty repo on github.com:
# git remote add origin https://github.com/<you>/most-likely.git
# git branch -M main && git push -u origin main
```

### 2. Deploy on Render
- Go to https://dashboard.render.com → **New +** → **Static Site**.
- Connect your GitHub and pick the **most-likely** repo.
- **Publish directory:** `www`   ·   **Build command:** *(leave empty)*
- Click **Create Static Site**. In ~1 minute you get a URL like
  `https://most-likely.onrender.com`.
- (Render auto-detects `render.yaml`, so most of this is pre-filled.)

Every `git push` from now on auto-deploys. That URL is the shareable game link.

---

## Phase 2 (next) — native iOS/Android with AdMob + RevenueCat
Handled in the next step. You'll create an AdMob account and a RevenueCat
account; their IDs go into `capacitor/native-config.js`. iOS builds from Xcode
on your Mac; Android from Android Studio.
