# Task 002 - Protocollo Safety Clinica

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
- 2026-06-12: protocollo safety clinica aggiunto a skill, intake, macro,
  adaptation e memoria profilo.

## Problema

La skill dice di riferire a un clinico, ma non specifica trigger operativi. Rischio: piani prescrittivi in casi medici, DCA, gravidanza, farmaci o condizioni ad alto rischio.

## Obiettivo

Creare regole chiare per stop, cautela e piano non-prescrittivo.

## File impattati

- `SKILL.md`
- `references/intake/profile_collection.md`
- `references/planning/macro_calculator.md`
- `references/followup/adaptation_engine.md`
- `references/profile_memory.md`

## Scope

- [x] Definire safety flags hard-stop.
- [x] Definire safety flags soft-stop.
- [x] Gestire minori, gravidanza/allattamento, DCA, patologie, farmaci.
- [x] Gestire obiettivi aggressivi e BMI molto basso.
- [x] Stabilire messaggio standard non-medico.
- [x] Stabilire cosa si puo ancora fare: educazione generale, domande, tracking.

## Acceptance Criteria

- [x] Ogni safety flag ha azione associata.
- [x] Piano calorie/macros non viene generato nei casi hard-stop.
- [x] Output resta utile ma non prescrittivo.
- [x] Safety flags vengono persistiti in `core.json`.
