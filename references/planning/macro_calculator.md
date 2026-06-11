# Macro Calculator

Use available profile and activity data. If key inputs are missing, ask first or
state assumptions.

Process:
- estimate maintenance calories from weight, sex, age, height, and activity
- adjust for goal:
  - fat loss: moderate deficit
  - muscle gain: small surplus
  - recomposition: near maintenance or small deficit
  - performance: support training output
- set protein from body weight and goal
- set fats above practical minimum
- assign remaining calories to carbs

Output:
```json
{
  "calories": 0,
  "protein_g": 0,
  "fats_g": 0,
  "carbs_g": 0,
  "assumptions": []
}
```

Avoid extreme targets. For high-risk or clinical cases, defer to clinician.
