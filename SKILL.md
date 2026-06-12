---
name: meal-planner
description: >
  Meal planning and nutrition coaching for creating diets, calculating calories
  and macros, building meal prep menus, shopping lists, weekly check-ins, and
  adapting plans from weight, hunger, training, adherence, photos, preferences,
  budget, allergies, lifestyle, fat loss, recomposition, muscle gain, or
  performance goals. Use when the user asks to start a diet, define nutrition
  goals, estimate macros, generate meals, organize meal prep, review progress,
  adjust calories/macros, troubleshoot stalled weight or adherence, or delegate
  meal-planning work to a token-efficient subagent.
---

# Meal Planner

Use this skill as a practical, non-medical nutrition-planning workflow.

## Core Files

Read topic files progressively:
- start every nutrition request with `references/core/workflow.md`;
- read `references/core/safety_protocol.md` before calories, macros, meal
  plans, or adaptations;
- read `references/core/reference_routing.md` when selecting phase references;
- read `references/core/output_rules.md` before final user output;
- read `references/core/subagent_contract.md` only when delegation is useful.

- `references/core/workflow.md`: phase selection, memory decision, full-plan
  prerequisites, and high-level execution order.
- `references/core/safety_protocol.md`: hard-stop and soft-stop flags. Read
  before calories, macros, meal plans, or adaptations.
- `references/core/reference_routing.md`: map user intent to exact reference
  files.
- `references/core/subagent_contract.md`: when to delegate, minimum input,
  compact output, and fallback without subagent.
- `references/core/output_rules.md`: language, units, assumptions, and concise
  final output rules.

## Phase References

- Intake: `references/intake/profile_collection.md`; add goal, lifestyle,
  nutrition, or photo refs only when needed.
- Planning: `references/planning/macro_calculator.md`,
  `references/planning/mealprep_generation.md`,
  `references/planning/shopping_list.md`, and
  `references/planning/output_formatter.md` as needed.
- Follow-up: `references/followup/progress_tracking.md`.
- Adaptation: `references/followup/progress_tracking.md` and
  `references/followup/adaptation_engine.md`.
- Memory: `references/profile_memory.md` only when continuing or updating a
  profile.
- Unclear/broad routing: `references/orchestrator.md`.

## Minimum Behavior

- Ask the next missing safety-critical question instead of fabricating a full
  plan.
- Load the smallest useful profile and reference context.
- Preserve safety flags when reading, writing, or compressing profile data.
- Fall back to inline routing when no subagent is available.
