# ForgeFit ⚡

Minimal, motivational, hypertrophy-focused workout tracker. Single-file PWA. Lives in your browser, installs to your iPhone home screen, works offline.

## Features

**Core tracking**
- Lift sessions: exercise → sets → weight × reps × RPE
- Rest timer (auto-starts when you check off a set, vibrates when done)
- Previous session's numbers shown as placeholders so you know what to beat
- Workout duration timer
- Body weight log
- Badminton sessions (type, duration, intensity, notes)

**Hypertrophy/progression intelligence**
- Per-set RPE for fatigue management
- Auto-calculated volume load (kg lifted)
- Estimated 1RM via Epley formula → PR tracking
- Per-exercise progression history
- Weekly volume per muscle group

**Templates**
- Save any finished workout as a reusable template
- Start a workout with one tap from a template

**Motivation**
- Daily rotating quote
- Streak counter (training days in a row, with one-day grace)
- Clean dark UI, minimal chrome

**AI-ready export** (the killer feature for your use case)
- "Copy AI-Ready Markdown" → puts a fully structured training report on your clipboard
- Includes: every session, weekly volume by muscle group, PRs, body weight trend, and a pre-written analysis prompt
- Paste into Claude/ChatGPT for hypertrophy + progressive overload analysis
- JSON export/import for full backups

---

## How to deploy

### 1. Push to GitHub

```bash
cd forgefit
git init
git add .
git commit -m "ForgeFit initial"
git branch -M main
# Create a new public repo on github.com called "forgefit", then:
git remote add origin https://github.com/YOUR_USERNAME/forgefit.git
git push -u origin main
```

### 2. Enable GitHub Pages

- Go to your repo → **Settings** → **Pages**
- Source: `Deploy from a branch`
- Branch: `main`, folder: `/ (root)`
- Save. Wait ~1 minute.
- Your app is live at: `https://YOUR_USERNAME.github.io/forgefit/`

### 3. Install to iPhone home screen

1. Open the URL above in **Safari** (must be Safari, not Chrome)
2. Tap the **Share** button (square with up-arrow)
3. Scroll down and tap **Add to Home Screen**
4. Name it "ForgeFit", tap Add
5. Done — opens like a native app, full-screen, offline-capable

---

## Data & privacy

- All data lives in `localStorage` on your device only
- Nothing is uploaded anywhere
- **Back up regularly** via the Analyze → Download JSON button (especially before clearing Safari data)

---

## AI analysis workflow

1. Train. Log sessions. Repeat for a few weeks.
2. Open Analyze tab → tap **Copy AI-Ready Markdown**
3. Open Claude → paste → it'll have a structured table of every session, weekly volume per muscle, PRs, and a pre-written prompt
4. Ask follow-ups: "where am I undertrained", "should I deload", "build me a 4-week mesocycle from here"

---

## Stack notes

- Single `index.html`, vanilla JS, no build step
- No dependencies, no framework
- ~1000 lines, all in one file = grep-friendly, easy to mod
- Service worker for offline + install
- Works on any modern browser; designed iPhone-first

## Modding

The exercise library is in the `EXERCISE_LIBRARY` array near the top of the `<script>` block. Add your own machines, accessories, or conditioning movements there. Quotes are in `QUOTES`. Default rest time is `state.defaultRest` (120s).
