# Orchestrator

Route by user intent. Load only listed files.

## Intake

Use when user wants to start, has no complete profile, or asks "che dieta devo
fare?".

Read:
- `references/intake/profile_collection.md`
- add `references/intake/goal_definition.md` if goal is vague
- add `references/intake/lifestyle_analysis.md` if activity is unknown
- add `references/intake/nutrition_assessment.md` if current diet matters
- add `references/intake/photo_analysis.md` only when photos are provided or
  requested

Output: missing questions or structured profile summary. No full plan yet.

## Planning

Use when profile, goal, constraints, and target calories/macros are available or
the user directly requests meal prep.

Read:
- `references/planning/macro_calculator.md` if calories/macros are missing
- `references/planning/mealprep_generation.md`
- `references/planning/shopping_list.md` if shopping list requested
- `references/planning/output_formatter.md` for final formatting

Output: calories/macros, meals, portions, prep, and optional shopping list.

## Follow-Up

Use when user reports weekly progress without asking for changes.

Read:
- `references/followup/progress_tracking.md`

Output: check-in summary and missing data. No adjustment unless requested.

## Adaptation

Use when user asks to adjust plan, weight is stalled, hunger/performance changed,
or adherence is known.

Read:
- `references/followup/progress_tracking.md`
- `references/followup/adaptation_engine.md`

Output: only concrete changes and monitoring target for next check-in.
