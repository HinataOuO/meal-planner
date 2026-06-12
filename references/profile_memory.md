# Profile Memory

Use `profile/` as local multiuser memory. Create it on first profiling if it
does not exist. Never store user progress in `references/`.

## User Resolution

Use memory only when continuity or stored data is needed:
- existing profile named by user
- continue/update/reuse a plan
- follow-up or adaptation
- planning request that depends on saved profile data

Do not use memory for a new first-run intake with no profile id; ask the
nutrition goal first via `references/intake/profile_collection.md`.

Resolution order:
1. Classify intent.
2. Decide memory need.
3. If memory is needed, resolve exactly one profile id.
4. Load only the minimal file(s) listed below for that phase.

- If the user provides a name, handle, issue id, or explicit profile id,
  normalize it to a filesystem-safe id: lowercase ASCII, spaces to `-`, remove
  symbols.
- If identity is unclear and profile memory is needed, ask one short question
  for the profile id before storing or reading personal data. Ask no other
  intake/planning questions in that message.
- Each user lives in `profile/<profile_id>/`.
- Keep `profile/index.json` as the only cross-user lookup file with compact
  metadata: `profile_id`, `display_name`, `status`, `last_updated`,
  `last_phase`, optional `tags`.

## File Layout

Create only files that are needed:

```text
profile/
  index.json
  <profile_id>/
    core.json
    plan.json
    progress.jsonl
    notes.md
```

- `core.json`: stable intake data, safety flags, goals, preferences,
  constraints.
- `plan.json`: current calories, macros, meals, substitutions, check-in targets.
- `progress.jsonl`: append-only compact check-ins, one minified JSON object per
  line.
- `notes.md`: rare human notes only when JSON would lose important context.

## Load Rules

- Intake: read `profile/index.json` only to resolve existing user; read
  `core.json` only if a matching profile exists. If no match exists, do not scan
  profile directories; start first-run intake.
- Planning: read `core.json`; read `plan.json` only when updating or reusing an
  existing plan.
- Follow-up: read `core.json`, `plan.json`, and only recent relevant
  `progress.jsonl` lines.
- Adaptation: read `core.json`, `plan.json`, and recent `progress.jsonl` lines.
- Do not load all profiles or full progress history unless explicitly requested.

## Write Rules

- After first complete profiling, create/update `profile/<profile_id>/core.json`
  and `profile/index.json`.
- After creating or changing a plan, update `plan.json`.
- After a check-in, append one minified JSON line to `progress.jsonl`.
- Check-in lines should keep fields needed for adaptation decisions when
  available: `d`, `w7`, `w7_prev`, `waist`, `hunger`, `energy`, `sleep`,
  `stress`, `perf`, `steps`, `adh`, `miss`, `dig`, `cycle`, `noise`, `trend`,
  `decision`.
- Keep profile data token optimized: short keys, no duplicated prose, no full
  chat transcripts, no repeated meal descriptions across files.
- Preserve clinically relevant safety flags when compressing. Never remove
  `safety.flags`; hard-stop and soft-stop flags must stay in `core.json` until
  updated by explicit user correction or clinician clearance.
