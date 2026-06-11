# Progress Tracking

Collect:
- peso medio 7 giorni attuale
- peso medio 7 giorni precedente
- circonferenza vita, se available
- fame
- energia
- sonno
- performance allenamento
- aderenza percentuale
- pasti saltati/sostituiti
- digestione

Output:
```json
{
  "trend": "down|stable|up|unclear",
  "adherence": "low|medium|high",
  "recovery": "poor|ok|good",
  "missing_data": []
}
```

Do not modify the plan unless user asks for an adaptation.

Append each check-in as one minified line in
`profile/<profile_id>/progress.jsonl`:

```json
{"d":"YYYY-MM-DD","w7":0,"w7_prev":0,"waist":null,"hunger":0,"energy":0,"sleep":0,"perf":"","adh":0,"miss":[],"dig":"","trend":""}
```

Use only available keys. Keep old history unloaded unless long-term analysis is
requested.
