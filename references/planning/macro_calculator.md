# Macro Calculator

Use available profile and activity data. Calculations must be deterministic:
same inputs produce same calories and macros.

## Inputs

Required:
- sex: `male` or `female`
- age
- height_cm
- weight_kg
- activity_level
- goal_type

Optional but useful:
- body_fat_percent
- training_days_per_week
- target_rate_percent_bw_per_week

If required body data is missing, ask for it before calculating. If only
`activity_level` or `target_rate_percent_bw_per_week` is missing, calculate with
the defaults below and include the choice in `assumptions`.

## Safety Gate

Before calculating, inspect `safety.flags` from `core.json` or current intake
using `references/core/safety_protocol.md`.

If any hard-stop flag exists, return no calorie/macro target. Use:

```json
{
  "blocked": true,
  "reason": "clinical_safety",
  "safety_flags": [],
  "message": "Non posso darti una prescrizione di calorie/macros per questo caso. Serve validazione di un medico/dietista qualificato.",
  "can_help_with": ["domande per il clinico", "educazione generale", "tracking non prescrittivo", "idee pasti non prescrittive"]
}
```

For soft-stop planning, use conservative bounds, avoid aggressive deficits, and
include active flags in `assumptions`.

## BMR

Use Mifflin-St Jeor:

```text
male:   BMR = 10 * weight_kg + 6.25 * height_cm - 5 * age + 5
female: BMR = 10 * weight_kg + 6.25 * height_cm - 5 * age - 161
```

If sex is unknown or outside `male`/`female`, ask before calculating.

## Activity Multiplier

| activity_level | Use when | Multiplier |
| --- | --- | --- |
| sedentary | desk job, little walking, no structured training | 1.2 |
| light | 6k-8k steps/day or 1-2 training days/week | 1.375 |
| moderate | 8k-12k steps/day or 3-4 training days/week | 1.55 |
| high | physical job or 5-6 training days/week | 1.725 |
| athlete | physical job plus hard training or 2-a-day blocks | 1.9 |

Default to `moderate` only when activity is missing and the user needs an
immediate estimate. Add assumption: `"activity_level defaulted to moderate"`.

Maintenance calories:

```text
maintenance = BMR * activity_multiplier
```

## Goal Adjustment

Use default adjustment unless the user gives a safe explicit rate:

| goal_type | Default adjustment | Allowed range |
| --- | ---: | ---: |
| fat_loss | -20% maintenance | -25% to -10% |
| recomposition | -5% maintenance | -10% to +0% |
| maintenance | 0% maintenance | 0% |
| muscle_gain | +10% maintenance | +5% to +15% |
| performance | +5% maintenance | 0% to +10% |

If the user gives `target_rate_percent_bw_per_week`, convert to calories with:

```text
daily_adjustment_kcal = weight_kg * target_rate_percent_bw_per_week / 100 * 7700 / 7
```

Apply negative adjustment for fat loss and positive adjustment for muscle gain.
Clamp it to the allowed range for the goal and include an assumption when
clamped.

## Safety Bounds

- Female floor: 1200 kcal/day.
- Male floor: 1500 kcal/day.
- Non-clinical deficit cap: no more than 25% below maintenance.
- Non-clinical surplus cap: no more than 15% above maintenance.
- If calculated target falls below floor, raise to floor and add assumption.
- If the user requests a more aggressive target, do not calculate an extreme
  prescription; reduce to the nearest bound and state the constraint.

For high-risk or clinical cases, defer to clinician instead of providing a
prescriptive target.

## Macro Rules

| goal_type | protein_g_per_kg |
| --- | ---: |
| fat_loss | 2.0 |
| recomposition | 1.8 |
| maintenance | 1.6 |
| muscle_gain | 1.8 |
| performance | 1.6 |

If `body_fat_percent` is known and above 35%, use adjusted weight for protein:

```text
adjusted_weight_kg = weight_kg * 0.85
```

Add assumption: `"protein based on adjusted weight due to high body fat"`.

Set fats:

```text
fat_g = max(0.6 * weight_kg, 20% of calories / 9)
```

Cap fats at 35% of calories unless the user specifically asks for a higher-fat
diet. If capped, allocate remaining calories to carbs.

Set carbs from remaining calories:

```text
carbs_g = (calories - protein_g * 4 - fat_g * 9) / 4
```

If carbs fall below 80 g/day for a training user, reduce fats down to the 0.6
g/kg floor first. If carbs are still below 80 g/day, keep the calculated value
and add assumption: `"low carbohydrate target due to calorie limit"`.

## Rounding

Round in this order:

1. Round BMR and maintenance to nearest 1 kcal for internal math.
2. Round final calories to nearest 25 kcal.
3. Round protein, fats, and carbs to nearest 5 g.
4. After rounding, accept macro calories within +/-50 kcal of calorie target.
5. If outside +/-50 kcal, adjust carbs by nearest 5 g until within range.

## Output

Output:
```json
{
  "calories": 0,
  "protein_g": 0,
  "fats_g": 0,
  "carbs_g": 0,
  "maintenance_calories": 0,
  "activity_level": "",
  "goal_adjustment_percent": 0,
  "assumptions": []
}
```

Include `assumptions` for missing defaults, clamped rates, safety floors, adjusted
protein weight, or low carbohydrate outcomes.
