# Task 009 - Contratto Subagent

Stato: done
Priorita: P2
Dipendenze: 004, 008

## Progress

- [x] Scope definito
- [x] Implementazione completata
- [x] Acceptance criteria verificati
- [x] README/istruzioni aggiornate se necessario

## Log

- 2026-06-12: task creato.
- 2026-06-12: definito contratto subagent, aggiunto router YAML e README.

## Problema

`SKILL.md` cita uso subagent per richieste da 3+ riferimenti, ma non esiste contratto operativo chiaro o agente specializzato nella repo.

## Obiettivo

Definire quando delegare e che output deve tornare.

## File impattati

- `SKILL.md`
- `agents/openai.yaml`
- opzionale: `agents/meal-planner-router.yaml`
- `README.md`

## Scope

- [x] Definire trigger delega.
- [x] Definire input minimo passato al subagent.
- [x] Definire formato output compatto.
- [x] Definire limiti: subagent non salva profili se non richiesto.
- [x] Valutare se aggiungere file agente dedicato.

## Acceptance Criteria

- [x] Delegation contract documentato.
- [x] Output subagent contiene file richiesti, fase, assunzioni, missing data.
- [x] Nessun dato personale extra passato.
- [x] Skill funziona anche senza subagent disponibile.
