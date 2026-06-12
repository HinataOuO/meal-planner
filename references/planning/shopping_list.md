# Shopping List

Generate only from final meal plan.

Aggregate total quantities across all days and recipes. Do not list the same
ingredient repeatedly by meal unless the user asks for per-recipe packing.

Group by:
- proteine
- carboidrati
- verdura/frutta
- grassi/condimenti
- latticini/uova
- dispensa

Output:
- ingredient
- total quantity in realistic shopping units
- optional notes for substitutions

## Quantity Rules

- Convert grams to practical units when helpful: kg, g, ml, L, cans, packs,
  eggs, slices, bunches.
- Keep raw shopping weights when recipes use raw ingredients.
- Add a small buffer only for trim/waste on produce or raw meat/fish when useful
  (about 5-10%); do not inflate packaged pantry items.
- For packaged goods, round up to normal buyable packs and note estimated
  leftovers.
- Keep allergen constraints visible in notes when relevant.
- Substitution notes must preserve macro role: protein-for-protein,
  carb-for-carb, fat-for-fat, veg-for-veg.

No generic explanation.
