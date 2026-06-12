# Task 003 - Privacy e Consenso Memoria Profilo

Stato: todo
Priorita: P0
Dipendenze: 010

## Progress

- [ ] Scope definito
- [ ] Implementazione completata
- [ ] Acceptance criteria verificati
- [ ] README/istruzioni aggiornate se necessario

## Log

- 2026-06-12: task creato.

## Problema

`references/profile_memory.md` salva dati personali e salute in `profile/`, ma non richiede consenso esplicito, non definisce cancellazione, retention o separazione dati sensibili.

## Obiettivo

Rendere la memoria locale esplicita, minimizzata e gestibile.

## File impattati

- `references/profile_memory.md`
- `references/intake/profile_collection.md`
- `.gitignore`
- `README.md`

## Scope

- [ ] Chiedere consenso prima di salvare dati personali.
- [ ] Permettere modalita senza memoria.
- [ ] Documentare cancellazione profilo.
- [ ] Definire dati minimi salvabili.
- [ ] Separare metadata da dati nutrizionali.
- [ ] Evitare salvataggio PII non necessaria.
- [ ] Confermare che `profile/` resta ignorato da git.

## Acceptance Criteria

- [ ] Primo salvataggio richiede consenso esplicito.
- [ ] Utente puo usare skill senza persistenza.
- [ ] Task di cancellazione profilo documentato.
- [ ] `profile/index.json` non contiene dati salute.
- [ ] Nessun transcript chat salvato.
