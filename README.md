# 🏋️ Barbell Coach

A mobile-first progressive overload workout tracker built as a single-file PWA. No app store, no account, no backend — just open it in Chrome and lift.

**Live app:** `https://<your-username>.github.io/<your-repo>/barbell-coach.html`

---

## Features

**Workout Tracking**
- Full-body barbell routine with 21 exercises across upper, lower, and core categories
- Muscle group label shown on each exercise card
- Log weight and reps per set with inline input controls
- Rest timer starts automatically after each completed set
- Elapsed workout clock and per-exercise PR detection (Epley 1RM formula)
- Add or remove exercises and sets mid-workout

**Progressive Overload (Double Progression)**
- Tracks whether all sets at max weight hit target reps across recent sessions
- Suggests a weight increase when 2 of the last 5 sessions qualify
- Weights increase in 5 lb increments by default

**Continuous Rotation Scheduling**
- Exercises rotate continuously through the default routine order based on where the previous session ended — no weekly reset
- Core exercises always appear first in every workout regardless of rotation position
- The app tracks a `routinePointer` (the last non-core exercise completed) so the next session picks up exactly where you left off
- Example: finish a session ending at Lat Pulldown → next workout shows Core, then Bent Over Row, Close Grip Bench Press, Skull Crushers, etc.

**Home Screen**
- "Next Workout Order" preview showing the upcoming exercise sequence
- "Muscle Groups This Week" checklist — tracks how many times each major muscle group has been hit this week against a recommended target, with a visual progress bar
- "Current Weights" section showing the suggested working weight for every exercise in your routine

**Progress Tab**
- Per-exercise charts showing estimated 1RM, volume load, and max weight over time
- Trend indicator comparing last session to prior
- Recent session history table per exercise

**Session History**
- Full log of every past session with expandable exercise detail
- Delete individual sessions
- Shows volume load and PR count per session

**Routine Management**
- Edit the default routine (add/remove exercises, change set/rep targets)
- Search all available exercises to add to routine or mid-workout
- Reset custom routine back to default at any time

**Data Portability**
- Export all session data as JSON from the Settings tab
- Import JSON to restore or transfer data
- Data lives in your browser's `localStorage` — nothing leaves your device

---

## Exercises

| Exercise | Category | Muscles |
|---|---|---|
| Barbell Bench Press | Upper | Chest |
| Incline Barbell Bench Press | Upper | Chest · Upper Chest |
| Close Grip Bench Press | Upper | Chest · Triceps |
| Barbell Skull Crushers | Upper | Triceps |
| Barbell Bicep Curl | Upper | Biceps |
| Barbell Overhead Press | Upper | Shoulders · Triceps |
| Barbell Bent Over Row | Upper | Back · Biceps |
| Barbell Shrug | Upper | Traps |
| Lat Pulldown | Upper | Lats · Biceps |
| Pullup | Upper | Lats · Biceps |
| Barbell Upright Row | Upper | Shoulders · Traps |
| Barbell Back Squat | Lower | Quads · Glutes |
| Romanian Deadlift | Lower | Hamstrings · Glutes |
| Barbell Hip Thrust | Lower | Glutes |
| Barbell Deadlift | Lower | Back · Hamstrings |
| Barbell Good Morning | Lower | Hamstrings · Lower Back |
| Barbell Lunges | Lower | Quads · Glutes |
| Barbell Front Squat | Lower | Quads · Core |
| Barbell Sumo Deadlift | Lower | Glutes · Hamstrings |
| Core | Core | Core · Hip Flexors |
| Plank | Core | Core |

---

## Default Routine Order

The default routine cycles through the following exercises in order. The app rotates through this list continuously session to session, always starting Core first:

1. Barbell Back Squat
2. Barbell Bench Press
3. Incline Barbell Bench Press
4. Barbell Overhead Press
5. Romanian Deadlift
6. Barbell Hip Thrust
7. Lat Pulldown
8. Barbell Bent Over Row
9. Close Grip Bench Press
10. Barbell Skull Crushers
11. Barbell Bicep Curl
12. Core *(always presented first regardless of rotation position)*

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

The exported JSON includes your full session history, any custom routine changes, and the current rotation pointer so your exercise order resumes correctly on import.

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
- Rotation state stored as `routinePointer` (index into the non-core portion of the routine), persisted in `localStorage` alongside session data
- Progressive overload and timer constants configurable at the top of the script (`OVERLOAD_SESSIONS`, `LOOK_BACK`, `REST_SEC`)

---

## License

MIT — use it, fork it, modify it however you like.
