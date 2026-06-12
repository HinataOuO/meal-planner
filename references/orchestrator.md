# Orchestrator

Route by user intent. Load only listed files.

## Profile Routing

Resolve in this order:
1. Intent: classify intake, planning, follow-up, or adaptation.
2. Need memory: required for existing-plan continuation, named profile,
   follow-up, adaptation, or planning from stored data. Not required for
   first-run intake without a profile id.
3. Resolve id: if memory is needed and no usable id/name/handle is present, ask
   one short question for the profile id. Do not ask other intake questions in
   the same message.
4. Load minimal files:
   - Intake: `profile/index.json` only to match id; then matching `core.json`.
   - Planning: matching `core.json`; `plan.json` only when reusing/updating.
   - Follow-up/adaptation: matching `core.json`, `plan.json`, recent relevant
     `progress.jsonl` lines only.
5. No full-profile scan: never load all `profile/` directories or full progress
   history unless the user explicitly asks for long-term analysis.

If no complete profile exists and the user is new, skip memory and start
first-run intake with the nutrition-goal question.

## Intake

Use when user wants to start, has no complete profile, or asks "che dieta devo
fare?".

Read:
- `references/profile_memory.md` only if profile memory is needed by the routing
  rules above
- `references/intake/profile_collection.md`
- add `references/intake/goal_definition.md` if goal is vague
- add `references/intake/lifestyle_analysis.md` if activity is unknown
- add `references/intake/nutrition_assessment.md` if current diet matters
- add `references/intake/photo_analysis.md` only when photos are provided or
  requested

Output: missing questions or structured profile summary. No full plan yet.

First-run rule: if no complete profile exists, begin with one question about the
nutrition goal. Continue with the fixed sequence in
`references/intake/profile_collection.md`, asking only the next missing field.
Do not ask the full intake checklist at once.

## Planning

Use when profile, goal, constraints, and target calories/macros are available or
the user directly requests meal prep.

Read:
- `references/profile_memory.md` when using stored profile data
- `references/planning/macro_calculator.md` if calories/macros are missing
- `references/planning/mealprep_generation.md`
- `references/planning/shopping_list.md` if shopping list requested
- `references/planning/output_formatter.md` for final formatting

Output: calories/macros, meals, portions, prep, and optional shopping list.

## Follow-Up

Use when user reports weekly progress without asking for changes.

Read:
- `references/profile_memory.md`
- `references/followup/progress_tracking.md`

Output: check-in summary and missing data. No adjustment unless requested.

## Adaptation

Use when user asks to adjust plan, weight is stalled, hunger/performance changed,
or adherence is known.

Read:
- `references/profile_memory.md`
- `references/followup/progress_tracking.md`
- `references/followup/adaptation_engine.md`

Output: only concrete changes and monitoring target for next check-in.
