# Macro Calculator Examples

Examples use `references/planning/macro_calculator.md` rules.

## Fat Loss

Input:

```json
{
  "sex": "male",
  "age": 35,
  "height_cm": 180,
  "weight_kg": 90,
  "activity_level": "moderate",
  "goal_type": "fat_loss"
}
```

Math:

```text
BMR = 10 * 90 + 6.25 * 180 - 5 * 35 + 5 = 1855
maintenance = 1855 * 1.55 = 2875.25
target = 2875.25 * 0.8 = 2300.2
```

Output:

```json
{
  "calories": 2300,
  "protein_g": 180,
  "fats_g": 55,
  "carbs_g": 270,
  "maintenance_calories": 2875,
  "activity_level": "moderate",
  "goal_adjustment_percent": -20,
  "assumptions": []
}
```

## Muscle Gain

Input:

```json
{
  "sex": "female",
  "age": 28,
  "height_cm": 165,
  "weight_kg": 60,
  "activity_level": "light",
  "goal_type": "muscle_gain"
}
```

Math:

```text
BMR = 10 * 60 + 6.25 * 165 - 5 * 28 - 161 = 1330.25
maintenance = 1330.25 * 1.375 = 1829.09
target = 1829.09 * 1.1 = 2012
```

Output:

```json
{
  "calories": 2000,
  "protein_g": 110,
  "fats_g": 45,
  "carbs_g": 290,
  "maintenance_calories": 1829,
  "activity_level": "light",
  "goal_adjustment_percent": 10,
  "assumptions": []
}
```
