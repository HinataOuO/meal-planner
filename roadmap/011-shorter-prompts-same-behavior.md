# Task 011 - Prompt piu corti a parita comportamento

Stato: done
Priorita: P2
Dipendenze: 008, 009

## Progress

- [x] Scope definito
- [x] Implementazione completata
- [x] Acceptance criteria verificati
- [x] README/istruzioni aggiornate se necessario

## Log

- 2026-06-12: task creato e completato. Compressi default prompt, router
  subagent e core refs senza cambiare regole operative.

## Problema

Dopo split e contratto subagent, alcuni prompt/testi operativi ripetono concetti
gia presenti in `SKILL.md` o nei core refs.

## Obiettivo

Ridurre token e verbosita mantenendo trigger, safety, routing, output e fallback
invariati.

## File impattati

- `agents/openai.yaml`
- `agents/meal-planner-router.yaml`
- `references/core/`
- `README.md`
- `roadmap/README.md`

## Scope

- [x] Accorciare default prompt senza promettere piano immediato.
- [x] Comprimere istruzioni subagent mantenendo input minimo e output shape.
- [x] Comprimere core refs senza perdere safety/routing/fallback.
- [x] Allineare README e roadmap.

## Acceptance Criteria

- [x] Prompt piu corti.
- [x] Comportamento safety invariato.
- [x] Subagent contract ancora contiene fase, file, assunzioni, missing data.
- [x] Skill continua a funzionare senza subagent.
