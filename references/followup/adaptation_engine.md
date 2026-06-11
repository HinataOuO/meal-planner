# Adaptation Engine

Adapt only after checking trend and adherence.

Rules:
- adherence low: fix execution barriers before changing calories
- weight stable 2+ weeks with high adherence on fat loss: reduce 100-150 kcal/day
  or add activity
- loss too fast, hunger high, or performance down: add 100-150 kcal/day, usually
  carbs around training
- muscle gain with no weight change 2+ weeks: add 100-150 kcal/day
- waist down and performance ok: keep plan even if scale is noisy

Output:
```json
{
  "changes": [],
  "new_calories": null,
  "new_macros": null,
  "next_check_in": []
}
```

Return only concrete changes plus next metric to monitor.
