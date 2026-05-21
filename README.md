# ForgeFit ⚡ // Tactical Edition

VALORANT-themed, hypertrophy-focused workout tracker. Single-file web app. Lives in a Safari bookmark, works offline once loaded.

## What's in this version

- **VALORANT theme** — clipped angular cards, red/teal/cream palette, Tomorrow + JetBrains Mono typography, scan-line overlay, tactical HUD vibe
- **Synthesized sound effects** — click, set-complete, PR fanfare, rest-done alarm, workout-complete jingle. All generated via Web Audio API (no audio files needed, works offline). Toggle in header.
- **Backdated badminton logging** — date + time pickers, defaults to "now" but fully editable. Tap "NOW" button to reset.
- **Persistent rest timer** — stores absolute end timestamp. If you switch apps or take a call, the timer keeps counting toward the real end time. When you flip back to Safari, the displayed time is always accurate, and if it expired while you were away, the alarm fires immediately on return.
- **PR detection with screen flash** — screen flashes red + fanfare plays when you check off a set that beats your estimated 1RM.
- **Configurable default rest time** (Analyze → Settings)

## How the rest timer works in Safari bookmark mode

Safari pauses JavaScript when you switch tabs or apps. ForgeFit handles this by storing the **end timestamp** in localStorage instead of running a countdown variable:

1. When you check off a set, the app saves `restEndTime = Date.now() + 120000`
2. Switch to another app / take a call → JS pauses, but the saved timestamp doesn't change
3. Switch back to Safari → the app recalculates `remaining = restEndTime - now()` and renders the correct time
4. If the timer expired while you were away, the alarm sound + vibration fires immediately when you return

## Features

- Lift sessions: exercise → sets → weight × reps × RPE
- Persistent rest timer with last-3-seconds warning ticks + vibration
- Previous session's numbers shown as placeholders → forces progressive overload
- Workout duration timer
- Body weight log
- Badminton sessions with date/time/intensity/duration/notes
- Templates — save any finished workout, start it again with one tap
- Per-exercise progression history
- Personal records (estimated 1RM via Epley formula)
- Weekly volume per muscle group
- AI-ready markdown export with pre-written analysis prompt
- JSON export/import for full backups
- Daily rotating tactical quotes + streak counter

## Deploy

### 1. Push to GitHub

```bash
cd forgefit
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/forgefit.git
git push -u origin main
```

Or upload the files via GitHub's web UI (drag the 5 files into the upload area).

### 2. Enable GitHub Pages

- Repo → Settings → Pages
- Source: Deploy from a branch
- Branch: `main`, folder: `/ (root)`
- Save. Wait ~1 minute.
- Live URL: `https://YOUR_USERNAME.github.io/forgefit/`

### 3. Bookmark in Safari

1. Open the URL on your iPhone in **Safari**
2. Tap the Share button
3. Tap **Add Bookmark** (or "Add to Favorites" if you want it on the start page)
4. Done. The app works offline after the first load.

## Updating

When you push new code to GitHub:
- Wait ~1 minute for GitHub Pages to redeploy
- In Safari, pull-to-refresh the page (or close the tab and reopen the bookmark)
- The service worker uses network-first for HTML, so updates roll out instantly on refresh

If updates won't appear: iPhone Settings → Safari → Advanced → Website Data → search "github" → delete → reopen.

## Data & privacy

All data lives in localStorage on your iPhone. Nothing is uploaded anywhere. Back up regularly via Analyze → Download Backup, especially before clearing Safari data.
