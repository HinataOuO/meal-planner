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
|   `-- openai.yaml                  # Agent display metadata and default prompt
|-- references/
|   |-- orchestrator.md              # Routes each user request to needed refs
|   |-- intake/                      # Profile, goal, lifestyle, diet, photo refs
|   |-- planning/                    # Macro, meal prep, shopping, formatting refs
|   `-- followup/                    # Progress tracking and adaptation refs
`-- profile/                         # Local user memory, created/updated at runtime
```

## Reference Modules

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

## Usage

Invoke the skill when the user asks for nutrition planning, for example:

```text
Use $meal-planner to create a practical weekly meal prep plan with calories,
macros, and a shopping list.
```

Example requests:

- "I want to start a diet."
- "Calculate calories and macros for body recomposition."
- "Create a 5-day meal prep plan with a shopping list."
- "My weight has stalled for 3 weeks. What should I change?"
- "This is my weekly check-in."

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
