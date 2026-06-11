# Profile Collection

Collect only missing data needed for safe planning.

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

Optional:
- foto progresso
- budget
- strumenti cucina
- numero pasti

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
  "bio":{"sex":"","age":0,"h_cm":0,"w_kg":0,"waist_cm":null},
  "goal":{"type":"","target":"","rate":""},
  "diet":{"allergies":[],"avoid":[],"prefs":[],"meals":null},
  "life":{"training":"","activity":"","sleep":"","budget":"","kitchen":[]},
  "safety":{"flags":[],"notes":""},
  "updated":"YYYY-MM-DD"
}
```

Keep empty optional fields out when unknown. Do not store chat transcripts.
