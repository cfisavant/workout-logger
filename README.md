# Workout Logger – plan format for Hans
Single page `index.html`. It loads `plan.json` (same folder) by default; `index.html?plan=other.json` loads another file. The embedded JSON in `index.html` is only an offline fallback. To publish a new workout, replace `plan.json` and push.
```json
{ "title": "Heavy Legs",             // required; with date, forms the save key
  "date": "2026-10-22",              // optional, YYYY-MM-DD (new title/date = fresh log)
  "unit": "lb", "notes": "optional",
  "exercises": [
    { "name": "RDL",                 // required
      "weight": 155,                 // exact number; 0 = bodyweight (shown "BW")
      "sets": 3, "reps": 12,         // exact integers, no ranges
      "repsBySet": [12, 11, 10],     // optional per-set targets; overrides sets/reps
      "rest": 120,                   // seconds, default 90
      "last": "145: 14/12/10",       // optional text shown as "Last:"
      "note": "slow eccentric" },    // optional cue
    { "name": "Farmer Carry (sec)",  // "(sec)" in name, or "unit": "sec" -> reps are seconds
      "weight": 70, "sets": 1, "reps": 50, "rest": 60 }
  ] }
```
Target display: `155 x 12/11/10` (repsBySet) or `175 x 1 x 8`; seconds add ` sec`.
Log output (Copy log): `Squat: 160 x 2 x 10`; same weight, varied reps: `RDL: 155 x 12/11/9 (target 12/11/10)`;
varied weight: `45 x 1 x 10, 50 x 1 x 8`. `(target …)` appears only when a set fell short; `(planned N sets)` if sets were missing; unlogged = `skipped`.
