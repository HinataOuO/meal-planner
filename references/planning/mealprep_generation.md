# Meal Prep Generation

Inputs: calories/macros, meals/day, preferences/exclusions, allergies, budget,
cooking time, storage capacity.

Do not generate a meal prep plan until calories/macros, allergies/exclusions,
meal count, and basic storage/cooking constraints are known or explicitly
assumed.

## Practical Rules

- Define batch size: number of days, meals per day, total portions, and portions
  per recipe.
- Keep batch duration realistic: 3-4 fridge days by default; freeze extra
  portions when planning beyond 4 days.
- Use cooked or raw weights consistently and label them. Prefer raw weights for
  shopping and cooked weights for portioning only when useful.
- Reuse core ingredients for efficiency, but keep at least 1-2 simple swaps if
  the user wants variety.
- Respect available cooking time, tools, budget, and storage capacity. If
  unknown, assume basic stovetop/oven, 60-90 minutes prep, and standard fridge.

## Food Safety

- Cool cooked food before sealing; refrigerate within about 2 hours.
- Fridge: use most cooked meals within 3-4 days.
- Freezer: freeze portions intended for later days; label meal/date.
- Reheat cooked meals until steaming hot throughout.
- Keep raw meat/fish separate from ready-to-eat foods during prep.
- Do not suggest unsafe room-temperature storage.

These are generic food-safety notes, not medical advice.

## Allergens And Cross-Contact

- List known allergies/intolerances as explicit constraints before the meal
  table.
- Exclude known allergens from ingredients and swaps.
- If allergy is severe or complex, mention cross-contact risk and prefer sealed,
  clearly labeled products; do not guarantee allergen-free kitchens.
- If allergen status is missing, ask before planning when the user requests a
  full meal prep plan.

## Macro-Safe Swaps

Swaps stay close to original meal: about +/-10 g protein and +/-100 kcal per
meal. Adjust fats/carbs to keep daily target close. Give gram portions and state
what they replace. Avoid swaps that break allergies, exclusions, budget, or
cooking constraints.

Output:
- daily calories/macros
- meal table with ingredients and grams
- prep schedule
- storage/reheating notes
- substitutions

Keep plan practical and repeatable. Do not over-optimize variety if user asked
for meal prep efficiency.
