# Progress Tracking

Collect:
- peso medio 7 giorni attuale
- peso medio 7 giorni precedente
- almeno 2 check-in settimanali comparabili; 3 preferiti per adattamenti
- circonferenza vita, se available
- fame, energia, sonno, performance allenamento
- aderenza percentuale
- pasti saltati/sostituiti
- digestione
- passi/cardio, se il piano li usa
- stress, ciclo mestruale, sodio/carboidrati insoliti, alcol, viaggio, malattia,
  DOMS o cambio allenamento, se rilevanti

## Trend Rules

- Use 7-day average weight, not single weigh-ins.
- Trend window: minimum 14 days for observation; 21 days preferred before
  changing calories for a stall.
- Mark trend `unclear` if fewer than 2 comparable 7-day averages exist, weigh-in
  frequency is low, adherence is unknown, or strong noise factors are present.
- Noise factors: cycle phase, high sodium/carbs, late meals, digestion changes,
  stress/sleep loss, alcohol, travel, illness, DOMS, new training, creatine,
  hydration shifts.
- If waist decreases, photos improve, or performance is stable while scale is
  noisy, prefer `stable_or_improving` observation and do not force a calorie
  change.

## Adherence Rules

- High: >=85% plan adherence and no repeated untracked meals.
- Medium: 70-84% adherence or some missing tracking.
- Low: <70%, frequent skipped meals, binges, untracked weekends, or major
  substitutions.
- Separate adherence problems from target problems. Low/medium adherence means
  fix execution barriers before changing calories.

Output:
```json
{
  "trend": "down|stable|up|unclear",
  "adherence": "low|medium|high",
  "recovery": "poor|ok|good",
  "observations": [],
  "decision": "hold|collect_more_data|adjust_adherence|eligible_for_adaptation",
  "next_metric": [],
  "missing_data": []
}
```

Do not modify the plan unless user asks for an adaptation.

Append each check-in as one minified line in
`profile/<profile_id>/progress.jsonl`:

```json
{"d":"YYYY-MM-DD","w7":0,"w7_prev":0,"waist":null,"hunger":0,"energy":0,"sleep":0,"stress":0,"perf":"","steps":null,"adh":0,"miss":[],"dig":"","cycle":"","noise":[],"trend":"","decision":""}
```

Use only available keys. Keep old history unloaded unless long-term analysis is
requested.
