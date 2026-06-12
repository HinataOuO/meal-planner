# Profile Collection

Collect only missing data needed for safe planning. In first-run configuration,
ask progressively and stop after each question. Do not ask the full checklist in
one message.

Read `references/core/safety_protocol.md` before planning or when safety data
appears. This file keeps intake order and profile schema only.

## First-Run Sequence

Start here when no complete `core.json` exists:

1. Nutrition goal: "Qual e il tuo obiettivo alimentare principale?"
2. Goal details: target, deadline, priority, acceptable pace when the first
   answer is vague or aggressive.
3. Identity/profile id: ask only if needed to store or distinguish the profile.
4. Basic body data: sesso, eta, altezza, peso.
5. Waist: circonferenza vita, if available.
6. Safety screen: allergie/intolleranze, patologie rilevanti, farmaci,
   gravidanza/allattamento.
7. Preferences: cibi esclusi, stile alimentare, pasti desiderati.
8. Lifestyle: training, activity, sleep, kitchen tools, budget only when needed
   for planning.

Question rules:
- Ask exactly one short question first, always about the nutrition goal.
- After the first answer, ask at most 1-2 closely related fields per message.
- Prefer the next missing required field over optional details.
- If the user wants to continue an existing profile but gives no id/name, stop
  intake and ask one short profile-id question.
- If no profile exists or no continuity is requested, do not read all `profile/`;
  continue first-run intake from the sequence above.
- If a safety flag appears, apply `references/core/safety_protocol.md`.
- Do not create calories, macros, meal plans, or shopping lists until required
  fields and safety screen are complete.

Required:
- sesso
- eta
- altezza
- peso
- circonferenza vita, se disponibile
- obiettivo dichiarato
- allergie/intolleranze
- patologie rilevanti, farmaci, gravidanza/allattamento
- preferenze alimentari e cibi esclusi
- livello attivita per macro: sedentary, light, moderate, high, athlete

Optional:
- foto progresso
- budget
- strumenti cucina
- numero pasti
- body fat percent, se disponibile

Output:
```json
{
  "profile_completed": true,
  "missing_fields": [],
  "safety_flags": []
}
```

If safety flags exist, avoid prescriptive plan and recommend clinician review.

When profile is complete, persist compact memory in
`profile/<profile_id>/core.json`:

```json
{
  "v":1,
  "id":"",
  "name":"",
  "bio":{"sex":"","age":0,"h_cm":0,"w_kg":0,"waist_cm":null,"bf_pct":null},
  "goal":{"type":"","target":"","rate":""},
  "diet":{"allergies":[],"avoid":[],"prefs":[],"meals":null},
  "life":{"training":"","activity_level":"","sleep":"","budget":"","kitchen":[]},
  "safety":{"flags":[],"notes":""},
  "updated":"YYYY-MM-DD"
}
```

Keep empty optional fields out when unknown. Do not store chat transcripts.
Never drop `safety.flags` when updating or compressing `core.json`.
