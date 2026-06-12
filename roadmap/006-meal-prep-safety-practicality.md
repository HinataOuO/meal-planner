# Task 006 - Meal Prep Sicuro e Pratico

Stato: done
Priorita: P1
Dipendenze: 001, 002

## Progress

- [x] Scope definito
- [x] Implementazione completata
- [x] Acceptance criteria verificati
- [x] README/istruzioni aggiornate se necessario

## Log

- 2026-06-12: task creato.
- 2026-06-12: aggiunte regole per storage/reheating, allergeni, batch sizing,
  quantita shopping aggregate e swap macro-safe.

## Problema

`mealprep_generation.md` produce struttura meal prep, ma manca dettaglio su conservazione, sicurezza alimentare, allergeni, batch sizing e quantita spesa realistiche.

## Obiettivo

Rendere i meal prep piu pratici, sicuri e acquistabili.

## File impattati

- `references/planning/mealprep_generation.md`
- `references/planning/shopping_list.md`
- `references/planning/output_formatter.md`

## Scope

- [x] Aggiungere regole frigo/freezer/reheating generiche.
- [x] Evidenziare allergeni e cross-contact quando rilevante.
- [x] Definire porzioni batch e durata.
- [x] Normalizzare quantita lista spesa.
- [x] Aggiungere swap equivalenti per macro e vincoli.

## Acceptance Criteria

- [x] Ogni piano meal prep include storage/reheating.
- [x] Shopping list aggrega quantita totali.
- [x] Allergie note appaiono come vincolo esplicito.
- [x] Swap non rompono macro target in modo rilevante.
