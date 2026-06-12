# Adaptation Engine

Adapt only after checking trend and adherence.

## Safety Gate

Inspect `safety.flags` with `references/core/safety_protocol.md` before changing
calories/macros.

If present, do not change calories/macros. Return:

```json
{
  "changes": ["calorie_macro_adaptation_blocked_clinical_safety"],
  "new_calories": null,
  "new_macros": null,
  "next_check_in": ["clinician clearance or medical guidance", "non-prescriptive symptoms/adherence tracking"]
}
```

Soft-stop flags require conservative changes only: prefer behavior, meal timing,
adherence barriers, sleep, and training support before calorie changes. If
changing calories, use 100 kcal/day steps and no aggressive deficit.

## Minimum Data

Do not change calories/macros when data is insufficient:
- fewer than 2 comparable weekly check-ins
- no current and previous 7-day average weight
- adherence unknown
- major noise factors explain the change
- safety status unclear

Prefer 3 weekly check-ins before declaring a true plateau. If data is
insufficient, return `changes: []`, keep calories/macros null, and set
`next_check_in` to the missing metrics.

## Decision Tree

1. Safety hard-stop: block calorie/macro adaptation.
2. Low/medium adherence: keep target; change execution only.
   Examples: meal timing, simpler prep, protein anchor, planned snack, weekend
   strategy, shopping/prep fix.
3. Trend unclear or noisy: keep plan; collect another 7-day average plus noise
   factors.
4. Fat loss, high adherence, 14-21 days stable:
   - if hunger/recovery poor: keep calories; improve sleep, steps, food volume,
     or meal timing.
   - if recovery ok: reduce 100-150 kcal/day or add 1-2k steps/day.
5. Fat loss too fast (>1% body weight/week), hunger high, performance down, or
   recovery poor: add 100-150 kcal/day, usually carbs around training.
6. Muscle gain, high adherence, 14-21 days no gain and performance not rising:
   add 100-150 kcal/day.
7. Muscle gain too fast with waist rising: reduce 100-150 kcal/day or tighten
   calorie-dense extras.
8. Recomposition/performance: prefer performance, waist, photos, and adherence
   over scale alone; use meal swaps/timing before calorie changes.

## Hold Conditions

Keep plan unchanged when:
- trend window is too short
- adherence is low/medium
- weight is noisy but waist/performance/photos are improving
- hunger, sleep, stress, digestion, or training disruption likely explains the
  signal
- the user asks for a change but missing data prevents a defensible decision

Output:
```json
{
  "observations": [],
  "decision": "hold|collect_more_data|adjust_adherence|adjust_calories|adjust_activity|meal_swaps",
  "changes": [],
  "new_calories": null,
  "new_macros": null,
  "next_check_in": []
}
```

Return observations, one decision, concrete changes, and the next metric to
monitor. Do not change calories and macros in the same response unless the macro
change is the direct consequence of the calorie change.
