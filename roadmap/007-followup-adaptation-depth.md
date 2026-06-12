# Task 007 - Follow-Up e Adaptation piu Robusti

Stato: done
Priorita: P1
Dipendenze: 001, 002, 003

## Progress

- [x] Scope definito
- [x] Implementazione completata
- [x] Acceptance criteria verificati
- [x] README/istruzioni aggiornate se necessario

## Log

- 2026-06-12: task creato.
- 2026-06-12: aggiunti trend window, fattori rumore, aderenza vs target,
  decision tree, hold conditions e campi JSONL per adaptation.

## Problema

`adaptation_engine.md` usa regole utili ma semplici. Mancano gestione rumore peso, ciclo, sodio, stress, training, digestione e trend multi-settimana.

## Obiettivo

Evitare aggiustamenti prematuri e rendere le modifiche piu contestuali.

## File impattati

- `references/followup/progress_tracking.md`
- `references/followup/adaptation_engine.md`
- `references/profile_memory.md`

## Scope

- [x] Definire finestra minima trend.
- [x] Gestire cause comuni di rumore peso.
- [x] Separare problema aderenza da problema target.
- [x] Aggiungere decision tree per kcal, passi, meal swaps.
- [x] Definire quando mantenere piano invariato.

## Acceptance Criteria

- [x] Nessuna modifica kcal con dati insufficienti.
- [x] Stallo richiede alta aderenza e trend sufficiente.
- [x] Output distingue osservazione, decisione, metrica prossima.
- [x] Check-in JSONL contiene campi minimi per decisione.
