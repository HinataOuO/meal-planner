# Meal Planner

```
+--------------------------------------------+
|  macros | meal prep | check-in | adaptation |
+--------------------------------------------+
```

Meal Planner is a Codex skill for practical nutrition planning. It helps collect
user context, define goals, estimate calories and macros, generate weekly meal
prep plans, build shopping lists, track progress, and adapt plans over time.

The skill is designed for useful coaching, not medical diagnosis. It keeps
advice non-medical, asks for safety-critical missing data, and refers users to a
qualified clinician when medical conditions, eating disorders, pregnancy,
medications, or disease-specific diets are involved.

## What It Does

```
[ intake ] -> [ planning ] -> [ follow-up ] -> [ adaptation ]
```

- Builds a nutrition profile from goals, body data, preferences, constraints,
  lifestyle, activity, current eating habits, and optional photos.
- Calculates calorie and macro targets for fat loss, recomposition, muscle gain,
  maintenance, or performance goals.
- Creates structured meal prep plans with portions, macros, prep notes, and
  substitutions.
- Produces shopping lists grouped by category.
- Tracks weekly check-ins using weight, hunger, training, adherence, and notes.
- Adjusts the plan when progress stalls, hunger rises, performance drops, or
  adherence changes.

## Project Layout

```text
.
|-- SKILL.md                         # Main skill instructions and routing rules
|-- agents/
|   |-- openai.yaml                  # Agent display metadata and default prompt
|   `-- meal-planner-router.yaml     # Optional compact subagent contract
|-- references/
|   |-- core/                        # Workflow, safety, routing, output rules
|   |-- orchestrator.md              # Routes each user request to needed refs
|   |-- intake/                      # Profile, goal, lifestyle, diet, photo refs
|   |-- planning/                    # Macro, meal prep, shopping, formatting refs
|   `-- followup/                    # Progress tracking and adaptation refs
`-- profile/                         # Local user memory, created/updated at runtime
```

## Reference Modules

### Core

- `workflow.md`: phase selection, memory decision, and execution order.
- `safety_protocol.md`: hard-stop/soft-stop flags and clinical-safety response.
- `reference_routing.md`: map intent to exact reference files.
- `subagent_contract.md`: delegation triggers, minimal input, compact output.
- `output_rules.md`: language, units, assumptions, and concise final format.

### Intake

- `profile_collection.md`: required profile fields and safety checks.
- `goal_definition.md`: target selection and goal clarity.
- `lifestyle_analysis.md`: schedule, training, activity, sleep, and constraints.
- `nutrition_assessment.md`: current diet, habits, appetite, and adherence risks.
- `photo_analysis.md`: optional visual progress context.

### Planning

- `macro_calculator.md`: calorie and macro target logic.
- `mealprep_generation.md`: weekly meals, portions, substitutions, and prep.
- `shopping_list.md`: grouped shopping output.
- `output_formatter.md`: final response format.

### Follow-Up

- `progress_tracking.md`: weekly trend analysis.
- `adaptation_engine.md`: concrete plan changes based on progress and adherence.

## Memory Model

User data lives in `profile/` and is loaded in the smallest useful unit:

```text
profile/
|-- index.json
`-- <profile_id>/
    |-- core.json       # Stable intake data and safety flags
    |-- plan.json       # Current calories, macros, meals, and targets
    |-- progress.jsonl  # Append-only compact check-ins
    `-- notes.md        # Rare human notes when JSON would lose context
```

The skill avoids loading all profiles or all history. For follow-ups and
adaptations, it reads only the current user files and recent relevant progress
lines.

## Subagent Use

`agents/meal-planner-router.yaml` defines an optional compact helper for broad
requests. Use it when a request likely needs 3+ reference files, such as full
planning from intake data, meal prep with recalculated macros, or check-in plus
adaptation.

The main agent must pass only minimal data: request summary, candidate reference
paths, needed profile fields, relevant safety flags, current targets, and recent
progress summary when required. The subagent returns phase, required files,
missing data, assumptions, safety flags, and a compact handoff. It does not save
profiles or change plans unless explicitly asked for a draft artifact. If no
subagent is available, the skill runs inline with the same routing rules.

## Usage

Invoke the skill when the user asks for nutrition planning, for example:

```text
Use $meal-planner: collect missing profile/safety first, then create
calorie/macro targets, meal prep, shopping list.
```

First-run flow:

```text
user asks for help -> nutrition goal question -> body/activity/safety screen
-> preferences -> calories/macros -> meal prep/shopping list when complete
```

A complete plan requires minimum profile data, goal, activity level,
preferences, allergies/intolerances, and safety screen. If those are missing,
the skill asks the next required question instead of producing a full plan.

Example requests by intent:

- Intake: "I want to start a diet."
- Planning: "Calculate calories and macros for body recomposition."
- Meal prep: "Create a 5-day meal prep plan with a shopping list from my saved profile."
- Check-in: "This is my weekly check-in: weight, hunger, training, adherence."
- Adaptation: "My weight has stalled for 3 weeks. What should I change?"

## Verification

Use the roadmap examples as manual regression tests before changing behavior:

- `roadmap/examples/golden_examples.md`: intake, safety, macro, meal prep,
  check-in, and adaptation input/output cases.
- `roadmap/examples/manual_test_checklist.md`: routing, safety, planning, and
  follow-up checklist.

Minimum pass set for any skill change:

1. Run the golden case for each affected phase.
2. Always run the safety hard-stop case when changing routing, intake, macros,
   meal prep, follow-up, or adaptation.
3. Confirm outputs preserve the expected behavior, even if prose differs.
4. Update the matching roadmap task when verification is complete.

## Design Principles

```
small context in  -> concrete plan out
safe boundaries   -> no medical overreach
local memory      -> useful continuity
modular refs      -> load only what matters
```

- **Practical first:** output should be directly usable, with grams, calories,
  macros, meals, prep steps, and shopping lists when needed.
- **Token efficient:** route through only the reference files required for the
  active phase.
- **Safety aware:** preserve clinically relevant flags and avoid extreme calorie
  prescriptions.
- **Italian by default:** respond in Italian unless the user writes in another
  language.

## Status

This repository contains the skill definition, reference playbooks, agent
metadata, and runtime profile storage used by the Meal Planner workflow.
