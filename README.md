[barbell-coach-readme.md](https://github.com/user-attachments/files/32567237/barbell-coach-readme.md)
# 🏋️ Barbell Coach

A mobile-first progressive overload workout tracker built as a single-file PWA. No app store, no account, no backend — just open it in Chrome and lift.

**Live app:** `https://<your-username>.github.io/<your-repo>/barbell-coach.html`

---

## Features

**Workout Tracking**
- Full-body barbell routine with 14 exercises across upper, lower, and core categories
- Log weight and reps per set with inline +/− nudge controls
- Rest timer starts automatically after each completed set
- Elapsed workout clock and per-exercise PR detection (Epley 1RM formula)
- Add or remove exercises and sets mid-workout

**Progressive Overload (Double Progression)**
- Tracks whether all sets at max weight hit target reps across recent sessions
- Suggests a weight increase when 2 of the last 5 sessions qualify
- Weights increase in 5 lb increments by default

**Smart Exercise Priority**
- Exercises skipped in the previous session bubble to the top of the next workout with a `↩ Missed` badge so you catch up before fatigue sets in

**Progress Tab**
- Per-exercise sparkline charts showing estimated 1RM, volume load, and max weight over time
- Trend indicators comparing last session to prior average
- 8-session history table per exercise

**Session History**
- Full log of every past session with expandable exercise detail
- Delete individual sessions
- Shows volume load and PR highlights

**Routine Management**
- Edit the default routine (add/remove exercises, change set/rep targets, reorder)
- Save custom named routines
- Start ad-hoc sessions outside your normal routine

**Data Portability**
- Export all session data as JSON from the Settings tab
- Import JSON to restore or transfer data
- Data lives in your browser's `localStorage` — nothing leaves your device

---

## Exercises

| Exercise | Category |
|---|---|
| Barbell Bench Press | Upper |
| Incline Barbell Bench Press | Upper |
| Close Grip Bench Press | Upper |
| Barbell Skull Crushers | Upper |
| Barbell Bicep Curl | Upper |
| Barbell Bent Over Row | Upper |
| Barbell Overhead Press | Upper |
| Barbell Shrug | Upper |
| Barbell Back Squat | Lower |
| Romanian Deadlift | Lower |
| Barbell Hip Thrust | Lower |
| Barbell Deadlift | Lower |
| Barbell Good Morning | Lower |
| Ab Wheel Rollouts | Core |

---

## Deployment

This is a single HTML file with no build step, no dependencies, and no server required.

**GitHub Pages (recommended)**

1. Push `barbell-coach.html` to a GitHub repository
2. Go to **Settings → Pages**
3. Set source to your main branch, root folder
4. Access the app at `https://<username>.github.io/<repo>/barbell-coach.html`

**Add to Home Screen (Chrome on Android)**

1. Open the app URL in Chrome
2. Tap the three-dot menu → **Add to Home screen**
3. The app opens full-screen like a native app

---

## Data & Privacy

All data is stored in `localStorage` in your browser under the key `barbell-coach-v2`. Nothing is sent to any server. Clearing your browser data will erase your workout history — use the **Export** button in Settings regularly to back up your data as a JSON file.

**Cross-device sync:** Because the app is a static page with no backend, data does not automatically sync across devices. To move your data:
1. Export JSON from the Settings tab on your source device
2. Open the app on your target device
3. Import the JSON file from Settings

---

## Technical Details

- Single-file HTML — no framework, no build toolchain, no external dependencies
- Vanilla JavaScript with inline CSS
- Progressive Web App metadata (theme color, viewport, mobile web app capable)
- All chart rendering done with inline SVG
- 1RM estimation uses the Epley formula: `weight × (1 + reps / 30)`
- Progressive overload constants are configurable at the top of the script (`OVERLOAD_SESSIONS`, `LOOK_BACK`, `REST_SEC`)

---

## License

MIT — use it, fork it, modify it however you like.
