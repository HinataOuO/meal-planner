# Manual Test Checklist

Run this checklist before marking a Meal Planner behavior change complete.

## Scope

- [ ] Read the changed files and identify affected phase: intake, planning,
      follow-up, adaptation, memory, or safety.
- [ ] Run all cases in `roadmap/examples/golden_examples.md` that touch the
      affected phase.
- [ ] Run the safety hard-stop case for any change touching intake, macros,
      meal prep, follow-up, adaptation, or routing.

## Routing

- [ ] First-run intake loads only intake references and asks the goal first.
- [ ] Existing-profile planning resolves one profile id before loading memory.
- [ ] Follow-up and adaptation load only current `core.json`, `plan.json`, and
      recent relevant `progress.jsonl` lines.
- [ ] Broad or unclear requests use `references/orchestrator.md` first.

## Safety

- [ ] Hard-stop flags block calories, macros, meal plans, shopping lists, and
      calorie/macro adaptations.
- [ ] Soft-stop flags trigger clarification or conservative planning.
- [ ] Safety flags are preserved in `profile/<profile_id>/core.json`.
- [ ] The standard clinical-safety message remains available.

## Planning

- [ ] Macro outputs are deterministic for identical inputs.
- [ ] Missing required body data causes a question, not a fabricated target.
- [ ] Meal prep includes grams, batch size, storage/reheating notes, and swaps.
- [ ] Shopping list aggregates totals by category.

## Follow-Up And Adaptation

- [ ] Check-ins use 7-day average weight.
- [ ] Low/medium adherence leads to execution fixes before target changes.
- [ ] No calorie change occurs with insufficient, noisy, or unsafe data.
- [ ] Adaptation output includes decision, concrete changes, and next metrics.

## Pass Criteria

- [ ] At least 5 golden examples still pass.
- [ ] Safety case passes.
- [ ] README verification instructions still match the files.
- [ ] Task roadmap state is updated when done.
