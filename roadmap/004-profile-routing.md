# Task 004 - Routing Profilo e Memoria

Stato: done
Priorita: P1
Dipendenze: 003

## Progress

- [x] Scope definito
- [x] Implementazione completata
- [x] Acceptance criteria verificati
- [x] README/istruzioni aggiornate se necessario

## Log

- 2026-06-12: task creato.
- 2026-06-12: routing profilo definito: intent -> need memory -> resolve id ->
  minimal load; first-run senza memoria parte dal goal.

## Problema

Le istruzioni dicono di leggere la memoria solo quando serve, ma anche di sapere se esiste un profilo completo. Ambiguita tra nuovo utente, utente esistente e profilo non identificato.

## Obiettivo

Definire una sequenza chiara di risoluzione profilo.

## File impattati

- `SKILL.md`
- `references/orchestrator.md`
- `references/profile_memory.md`
- `references/intake/profile_collection.md`

## Scope

- [x] Definire quando serve memoria.
- [x] Definire ordine: intent -> need memory -> resolve id -> load minimal file.
- [x] Definire comportamento se identita manca.
- [x] Definire comportamento first-run senza memoria.
- [x] Evitare letture complete di `profile/`.

## Acceptance Criteria

- [x] Nuovo utente riceve prima domanda goal.
- [x] Utente esistente puo riprendere piano con id.
- [x] Se memoria serve ma id manca, viene chiesto un solo identificativo.
- [x] Nessuna istruzione contraddittoria tra `SKILL.md` e orchestrator.
