# Task 010 - Risoluzione Worktree Dirty

Stato: done
Priorita: P0
Dipendenze: -

## Progress

- [x] Scope definito
- [x] Implementazione completata
- [x] Acceptance criteria verificati
- [x] README/istruzioni aggiornate se necessario

## Log

- 2026-06-12: task creato.
- 2026-06-12: diff corrente rivisto e classificato. Modifiche memoria/profilo
  considerate baseline desiderata; modifiche macro appartengono al task 001.
  Nessuna modifica utente rimossa.

## Baseline

Classificazione diff:

- `SKILL.md`: desiderato. Sposta protocollo memoria fuori dal file principale e
  instrada verso `references/profile_memory.md`.
- `references/profile_memory.md`: desiderato. Contiene protocollo multiuser,
  layout `profile/`, load/write rules e ottimizzazione token.
- `references/orchestrator.md`: desiderato. Aggiunge regola first-run
  progressiva.
- `references/intake/profile_collection.md`: desiderato. Contiene first-run
  progressivo; le aggiunte `activity_level` e `bf_pct` sono richieste dal task
  001.
- `references/planning/macro_calculator.md`: desiderato. Implementazione task
  001.
- `roadmap/`: desiderato. Board operativo e task tracker.

## Problema

Worktree contiene modifiche non committate su file centrali e nuovo `references/profile_memory.md`. Prima di refactor ampi va chiarito cosa mantenere.

## Obiettivo

Stabilizzare baseline prima delle modifiche successive.

## File impattati

- `SKILL.md`
- `references/intake/profile_collection.md`
- `references/orchestrator.md`
- `references/profile_memory.md`

## Scope

- [x] Rivedere diff corrente.
- [x] Decidere se tenere, modificare o separare in commit.
- [x] Verificare coerenza con README.
- [x] Aggiornare roadmap se emergono nuove criticita.

## Acceptance Criteria

- [x] Diff corrente classificato come desiderato o da correggere.
- [x] Nessuna modifica utente persa.
- [x] Baseline pronta per task 001-009.
