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
varied weight: `160x10-2/165x9-1`.
RIR (reps in reserve, optional 0–5 tap buttons per set) is logged as `reps-RIR`, e.g. `RDL: 155 x 12-2/11-2/9-1 (target 12/11/10)`; omitted when not tapped.
Weight and reps are editable per set before tapping Set Complete; the log shows the actual load.
Session notes box (end of page) is appended as a final line `Notes: …`. `(target …)` appears only when a set fell short; `(planned N sets)` if sets were missing; unlogged = `skipped`.

Plate calculator: barbell lifts show plates **per side** under the weight (45 lb bar; plates 45/35/25/10/5/2.5/1.25), updating live as the weight is edited.
Optional exercise field `"barbell": true` forces the calculator on (`"barbell": false` forces it off). Without the field, names containing squat/bench/deadlift/RDL/barbell/OHP/good morning/hip thrust are treated as barbell, except dumbbell/DB/cable/machine/Smith/split squat/goblet/BW/kettlebell.
When the last set of an exercise is completed, the page scrolls the next unfinished exercise to the middle of the screen; undo scrolls back to that exercise.
