# Project Agent Behavior

Questo file guida ogni modifica futura alla skill Meal Planner, agli agenti e
alle feature collegate. Prima di editare `SKILL.md`, `agents/`, `references/` o
roadmap, leggere questo file.

## Principio Base

Tenere `SKILL.md` come indice operativo breve. Spostare dettagli, contratti,
regole e casi specifici in sottofile tematici dentro `references/`.

Obiettivo:
- meno contesto caricato all'avvio;
- routing piu chiaro;
- regole riusabili senza duplicazione;
- modifiche piccole e localizzate;
- comportamento invariato quando si riorganizzano i file.

## Approccio Di Suddivisione

Quando una sezione cresce o tratta un argomento autonomo, estrarla in un file
dedicato.

Usare questa struttura:
- `SKILL.md`: trigger, indice, ordine di lettura, comportamento minimo.
- `references/core/`: regole sempre rilevanti o trasversali.
- `references/intake/`: raccolta profilo, obiettivo, lifestyle, dieta, foto.
- `references/planning/`: macro, meal prep, shopping list, formato output.
- `references/followup/`: check-in, tracking, adaptation.
- `agents/`: metadata e subagent opzionali.
- `roadmap/`: task, acceptance criteria, golden/manual tests.

Prima scelta per nuove regole trasversali:
- workflow -> `references/core/workflow.md`
- safety -> `references/core/safety_protocol.md`
- routing -> `references/core/reference_routing.md`
- subagent -> `references/core/subagent_contract.md`
- output finale -> `references/core/output_rules.md`

## Approccio Di Riassunto

Quando si sposta contenuto da `SKILL.md` a sottofile:

1. Conservare il comportamento, non la forma esatta.
2. In `SKILL.md` lasciare solo:
   - quando leggere il file;
   - cosa contiene;
   - regola minima non negoziabile.
3. Nel sottofile mettere dettagli operativi, checklist, JSON shape, limiti,
   esempi brevi.
4. Rimuovere duplicazioni tra `SKILL.md` e sottofile.
5. Se una regola serve a piu fasi, metterla in `references/core/`.
6. Se una regola serve a una sola fase, metterla nel modulo di fase.

Buon riassunto:
- breve;
- imperativo;
- specifico;
- con path espliciti;
- senza teoria generica;
- senza ripetere testo gia presente altrove.

## Ottimizzazione Contesto

Ogni modifica deve ridurre o preservare il carico di contesto.

Regole:
- caricare solo i file necessari alla fase;
- non far leggere tutta `references/`;
- non duplicare safety, routing o output rules in piu file;
- preferire riferimenti a path invece di copiare sezioni lunghe;
- tenere `SKILL.md` sotto 100 righe quando possibile;
- tenere i sottofile tematici piccoli e autonomi;
- se un sottofile supera circa 100 righe, aggiungere indice o dividerlo.

## Modifica Agente O Nuova Feature

Ogni volta che si modifica l'agente o si implementa una nuova funzione:

1. Identificare fase impattata: intake, planning, follow-up, adaptation, memory,
   safety, routing, subagent, output.
2. Leggere `SKILL.md` e il sottofile tematico rilevante.
3. Aggiornare il file piu specifico possibile.
4. Aggiornare `SKILL.md` solo se cambia routing, indice, trigger o comportamento
   minimo.
5. Aggiornare `README.md` solo se cambia struttura o verifica utente.
6. Aggiornare roadmap/golden examples se cambia comportamento verificabile.
7. Non riscrivere file non collegati.

## Checklist Pre-Chiusura

- [ ] `SKILL.md` resta indice breve, non manuale completo.
- [ ] Nuove regole stanno nel sottofile piu specifico.
- [ ] Nessuna duplicazione inutile tra core e phase refs.
- [ ] Safety hard-stop resta leggibile prima di macro/meal/adaptation.
- [ ] Routing punta a path esistenti.
- [ ] README riflette eventuali nuovi file o directory.
- [ ] Golden/manual tests aggiornati se cambia comportamento.
- [ ] Worktree sporco preesistente non viene revertito.

## Stile

- Italiano di default.
- Frasi corte.
- Path espliciti.
- Markdown semplice.
- ASCII salvo contenuto gia non-ASCII o necessita chiara.
- Nessun refactor fuori scope.
