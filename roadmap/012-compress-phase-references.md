# Task 012 - Compressione References Di Fase

Stato: done
Priorita: P2
Dipendenze: 008, 011

## Progress

- [x] Scope definito
- [x] Implementazione completata
- [x] Acceptance criteria verificati
- [x] README/istruzioni aggiornate se necessario

## Log

- 2026-06-12: task creato dopo audit dimensioni reference.
- 2026-06-12: compresse refs fase; nessun cambio behavior/golden previsto.

## Problema

Le core refs sono state compresse, ma alcune phase refs restano lunghe o
duplicano regole gia centralizzate in `references/core/`, soprattutto safety,
routing, output e fallback.

## Obiettivo

Comprimere le reference di intake, planning e follow-up mantenendo invariati:
safety, determinismo macro, meal prep pratico, tracking/adaptation e golden
examples.

## File impattati

- `references/intake/*.md`
- `references/planning/*.md`
- `references/followup/*.md`
- `roadmap/examples/golden_examples.md`, se serve aggiornare expected behavior
- `roadmap/examples/manual_test_checklist.md`, se cambia verifica

## Scope

### Intake

- [x] `references/intake/profile_collection.md`
  - Rimuovere duplicazione safety gia in `references/core/safety_protocol.md`.
  - Mantenere first-run sequence e regola "una domanda alla volta".
  - Mantenere required/optional fields e schema `core.json`.
- [x] `references/intake/goal_definition.md`
  - Verificare se gia compatto; comprimere solo ridondanze.
- [x] `references/intake/lifestyle_analysis.md`
  - Verificare se gia compatto; comprimere solo ridondanze.
- [x] `references/intake/nutrition_assessment.md`
  - Verificare se gia compatto; comprimere solo ridondanze.
- [x] `references/intake/photo_analysis.md`
  - Verificare se gia compatto; preservare divieti diagnostici.

### Planning

- [x] `references/planning/macro_calculator.md`
  - Compressione prioritaria.
  - Preservare formule, multiplier, adjustment, bounds, macro rules, rounding,
    output JSON e safety gate.
  - Non cambiare risultati dei golden examples.
- [x] `references/planning/mealprep_generation.md`
  - Comprimere practical rules, food safety, allergeni, swaps e output.
  - Preservare note frigo/freezer/reheat e cross-contact.
- [x] `references/planning/shopping_list.md`
  - Verificare compattezza; preservare aggregazione e categorie.
- [x] `references/planning/output_formatter.md`
  - Verificare compattezza; preservare ordine sezioni.

### Follow-Up

- [x] `references/followup/adaptation_engine.md`
  - Compressione prioritaria.
  - Preservare safety gate, minimum data, decision tree, hold conditions e
    output JSON.
- [x] `references/followup/progress_tracking.md`
  - Comprimere trend/adherence rules se possibile.
  - Preservare 7-day average, noise factors, JSON output e append JSONL.

## Acceptance Criteria

- [x] Phase refs piu corte o con motivazione esplicita se non compresse.
- [x] Nessuna regola safety persa.
- [x] Golden examples ancora validi.
- [x] Macro calculator produce stessi output per esempi esistenti.
- [x] Meal prep mantiene storage/reheating/allergen rules.
- [x] Adaptation non cambia target con dati insufficienti o safety hard-stop.
- [x] `SKILL.md` resta indice breve.
