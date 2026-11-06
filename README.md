# 💪 Barbell Coach

A single-file, offline-friendly workout tracker for barbell and dumbbell strength training. It runs a rotating full-body routine, suggests the next weight for each lift, and keeps your history in the browser. There's nothing to install and no server.

**Current version:** v4 (shown in Settings)

---

## Quick start

1. Open `barbell-coach.html` in a mobile or desktop browser. You can add it to your home screen to use it like an app.
2. Tap **▶ Start Workout**. Core and Face Pull load first, then the next lifts in the rotation.
3. For each set, enter the weight and reps, then tap **○** to mark it done. The rest timer starts automatically.
4. Tap **Finish**. The session is saved and the rotation moves forward.

---

## How the routine works

The app uses **one rotating list** instead of fixed day templates. Every session starts with the "every session" exercises. After that, it picks up the rotation where your last workout stopped. Do as many lifts as you have time for. If you work through the list twice a week, every major muscle group gets trained at least twice.

### Every session
| Exercise | Sets × Reps |
|---|---|
| Core | 3 × 8–10 |
| Face Pull | 3 × 15–20 |

### Rotation (v4 order)
| # | Exercise | Sets × Reps | Type |
|---|---|---|---|
| 1 | Barbell Back Squat | 3 × 8 | Legs (loads the spine) |
| 2 | Barbell Bench Press | 3 × 8 | Push |
| 3 | Lat Pulldown | 3 × 8 | Pull |
| 4 | Barbell Overhead Press | 3 × 8–10 | Push |
| 5 | Barbell Bent Over Row | 3 × 8 | Pull (loads the spine) |
| 6 | Barbell Hip Thrust | 3 × 10 | Legs |
| 7 | Incline Barbell Bench Press | 3 × 8 | Push |
| 8 | Chest-Supported Row | 3 × 10 | Pull |
| 9 | Romanian Deadlift | 3 × 10 | Legs (loads the spine) |
| 10 | Barbell Skull Crushers | 3 × 10–12 | Push (arms) |
| 11 | Barbell Bicep Curl | 2 × 10–12 | Pull (arms) |
| 12 | Dumbbell Lateral Raise | 2 × 12–15 | Side delts |

The order is deliberate:
- Legs, push and pull alternate, so no session ends up all pressing.
- The three lifts that load the spine (squat, barbell row and RDL) are four slots apart, so a session rarely includes more than two of them.
- Weekly pulling volume (rows, pulldowns and face pulls) is about equal to or more than pressing volume. This helps prevent the rounded-shoulder posture and upper-back strain that heavy pressing can cause.

You can edit the routine in **Settings → Edit Routine**: change sets and reps, remove lifts, or add any exercise from the library.

---

## Progression rules

The app suggests a weight for every exercise based on your logged history. The smallest jump is **5 lb**, which matches the smallest plates available.

### Standard lifts
(squat, bench, incline, rows, RDL, hip thrust, lat pulldown, and others)

- **Go up 5 lb** after **2 sessions at your current weight** where every planned set hits the target reps.
- Only sessions done at the current weight count. Passing at a lighter weight doesn't count toward the next increase.

### Reps before weight
(overhead press, skull crushers, bicep curls, lateral raises, face pulls)

On smaller lifts, a 5 lb jump is a big percentage increase, so these lifts work up through a rep range first:

| Lift | Range |
|---|---|
| Overhead Press | 8–10 |
| Skull Crushers | 10–12 |
| Bicep Curl | 10–12 |
| Lateral Raise | 12–15 |
| Face Pull | 15–20 |

Each session, the app asks for one more rep per set. Once **every set reaches the top of the range**, it adds 5 lb and drops you back to the bottom of the range.

### Automatic reset
If you **miss the minimum reps 3 sessions in a row at the same weight**, the app drops that lift about **10%** (rounded to 5 lb) so you can build back up with good form. This keeps you from grinding through a plateau. The suggestion box shows the reason whenever a reset happens.

### Training intensity
Leave 1–2 reps in the tank on most sets. Going to failure isn't needed to make progress.

---

## Features

- **Suggested weights** in every exercise card, with a note explaining why (increase, stay, or reset).
- **⇄ Swap:** swap an exercise for one session without changing the routine. The swapped lift is logged under its own name, so it doesn't affect the original lift's progression.
  - Back Squat → Goblet Squat, Bulgarian Split Squat, Front Squat, Lunges
  - Bent Over Row ↔ Chest-Supported Row
  - Bench ↔ Close Grip / Incline; RDL → Hip Thrust / Good Morning; Lat Pulldown → Pull-up; Skull Crushers → Close Grip Bench
- **📝 Set notes:** add a note to any set ("back tight", "felt easy"). Notes show up in History.
- **Rest timer by exercise:** 120 s for heavy compound lifts, 90 s for medium lifts, and 60 s for accessories.
- **Weekly muscle-group tracker** on the Home screen, including **Upper Back** (face pulls and rows).
- **PR detection** based on estimated 1-rep max (Epley formula).
- **Progress charts** for each exercise: estimated 1RM, volume, or max weight.
- **History** of every session with total volume and PRs.

---

## Starting weights (exercises with no history)

Estimated from current working weights (as of 11/2026: squat 230, RDL 220, row 195, bench 190, overhead press 130). Each estimate is replaced by your real numbers after your first logged session.

| Exercise | Start | Notes |
|---|---|---|
| Face Pull | 30 lb (cable) | Light, posture-focused |
| Chest-Supported Row | 45 lb per hand | Lie face-down on an incline bench |
| Dumbbell Lateral Raise | 15 lb per hand | Strict; raise only to shoulder height |
| Goblet Squat | 60 lb dumbbell | No bar on your back |
| Bulgarian Split Squat | 30 lb per hand | Reps are per leg |
| Barbell Front Squat | 155 | About 70% of back squat |
| Barbell Lunges | 95 | |
| Barbell Deadlift / Sumo Deadlift | 225 | Conservative |
| Barbell Good Morning | 95 | Loads the spine; use with care |
| Barbell Shrug | 185 | |
| Barbell Upright Row | 75 | Wide grip, to chest height |
| Pull-up / Plank | Bodyweight | |

---

## Data, backup & transfer

Your data is saved in the browser's **localStorage** under the key `barbell-coach-v2`, and it stays on your device.

- **📤 Export JSON** (Settings): downloads `barbell-coach-YYYY-MM-DD.json` with all sessions, your custom routine, your place in the rotation, and the data version.
- **📥 Import JSON** (Settings): **merges** the file into what's already in the app.
  - Sessions already in the app are kept as they are.
  - Sessions in the file that the app doesn't have yet are added (matched by session ID).
  - Importing an old backup can't overwrite newer data.
  - Works with exports from **any earlier version**, including the original Monday/Friday app format. Sets without a "done" flag count as done if they have reps.
- **Upgrading:** if you replace the HTML file in the same place (same browser and URL), your saved data loads automatically. The app updates your routine and keeps your place in the rotation. If you open the new version somewhere else, export from the old copy and import into the new one.
- **🗑 Clear All Data** resets the app to the built-in history.

> Browser storage can be cleared by the browser or the device. **Export regularly** as a backup.

---

## Version history

### v4
- Reordered the rotation so legs, push and pull alternate, with the spine-loading lifts spread out.
- Added **reps before weight** for overhead press, skull crushers, curls, lateral raises and face pulls.
- Added an **automatic reset** (about −10%) after 3 sessions in a row of missed reps at the same weight.
- Added **Dumbbell Lateral Raise** (2 × 12–15, starting at 15 lb per hand).
- Upgrades keep your place in the rotation.

### v3
- Fixed a progression bug where the weight kept going up while reps were being missed. Only sessions at the current weight now count.
- Added **Face Pull** as an every-session exercise.
- Replaced Close Grip Bench Press with **Chest-Supported Row** in the default routine.
- Added Goblet Squat and Bulgarian Split Squat, plus the **⇄ Swap** button.
- Added per-set **notes**, rest times by exercise, and the **Upper Back** muscle-group tracker.
- Added starting-weight estimates for exercises with no history.
- Import now merges instead of replacing, and accepts older export formats.

### v2
- Single rotating full-body routine with a rotation pointer.
- Added incline bench, skull crushers, hip thrust and lat pulldown.

---

## Notes

This app gives general training suggestions, not medical advice. If you have pain that's sharp, spreads, or comes with numbness or tingling, see a healthcare professional before continuing to train through it.
