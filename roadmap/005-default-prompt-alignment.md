# Task 005 - Allineamento Default Prompt

Stato: done
Priorita: P1
Dipendenze: 004

## Progress

- [x] Scope definito
- [x] Implementazione completata
- [x] Acceptance criteria verificati
- [x] README/istruzioni aggiornate se necessario

## Log

- 2026-06-12: task creato.
- 2026-06-12: default prompt e README allineati al flusso reale: raccolta dati
  prima, piano completo solo quando il profilo minimo e safety screen esistono.

## Problema

`agents/openai.yaml` promette subito piano meal prep completo, ma la skill blocca piani se mancano dati e safety screen.

## Obiettivo

Allineare prompt iniziale, README e workflow reale.

## File impattati

- `agents/openai.yaml`
- `README.md`
- `SKILL.md`

## Scope

- [x] Cambiare default prompt per includere raccolta dati se necessari.
- [x] Aggiungere esempi separati: intake, planning, check-in, adaptation.
- [x] Chiarire che il piano completo richiede profilo minimo.

## Acceptance Criteria

- [x] Default prompt non promette piano immediato senza dati.
- [x] README mostra flusso realistico first-run.
- [x] Esempi coprono almeno 4 intenti.
