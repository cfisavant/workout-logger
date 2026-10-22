# Workout Logger – plan format for Hans
Single file `index.html`. Replace the JSON inside `<script type="application/json" id="plan">`, or host a `plan.json` next to it and open `index.html?plan=plan.json`.
```json
{ "title": "Pull & Shoulders",      // required; with date, forms the save key
  "date": "2026-10-26",              // optional, YYYY-MM-DD
  "unit": "lb", "notes": "optional",
  "exercises": [
    { "name": "DB Shoulder Press",   // required
      "weight": 45,                  // exact number; 0 = bodyweight (shown "BW")
      "sets": 3, "reps": 10,         // exact integers, no ranges
      "rest": 90,                    // seconds, default 90
      "last": "40 x 3 x 10",         // optional text shown as "Last:"
      "note": "slow eccentric" }     // optional cue
  ] }
```
Log output (Copy log): `DB Shoulder Press: 45 x 3 x 10`; if sets differ: `45 x 1 x 10, 45 x 1 x 8`.
