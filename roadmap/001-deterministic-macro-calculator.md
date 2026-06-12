# Task 001 - Macro Calculator Deterministico

Stato: done
Priorita: P0
Dipendenze: 010

## Progress

- [x] Scope definito
- [x] Implementazione completata
- [x] Acceptance criteria verificati
- [x] README/istruzioni aggiornate se necessario

## Log

- 2026-06-12: task creato.
- 2026-06-12: aggiunte formula Mifflin-St Jeor, activity multiplier, adjustment
  per goal, safety bounds, macro rules, rounding ed esempi fat loss/massa.

## Problema

`references/planning/macro_calculator.md` usa indicazioni vaghe: maintenance, moderate deficit, small surplus, protein by body weight. Mancano formula, range, limiti minimi e arrotondamenti.

## Obiettivo

Rendere i calcoli calorie/macros ripetibili e verificabili.

## File impattati

- `references/planning/macro_calculator.md`
- `references/intake/profile_collection.md`
- opzionale: `roadmap/examples/`

## Scope

- [x] Definire formula BMR/TDEE primaria.
- [x] Definire fallback se mancano dati.
- [x] Definire moltiplicatori attivita.
- [x] Definire deficit/surplus per goal.
- [x] Definire range proteine, grassi, carboidrati.
- [x] Definire soglie di sicurezza e arrotondamenti.
- [x] Aggiungere esempi input/output.

## Acceptance Criteria

- [x] Stesso profilo produce stessi kcal/macros.
- [x] Ogni assunzione numerica e documentata.
- [x] Target estremi vengono bloccati o ridotti.
- [x] Output include `assumptions` quando mancano dati.
- [x] Esempio fat loss e massa presenti.
