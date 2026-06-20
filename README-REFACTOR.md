# Refactor Notes (Phase 1, i18n)

- Introdotti blueprint **i18n** (IT/EN) con dizionario interno e selezione via `input_select.language_gui`.
- Aggiunta CI (yamllint) e struttura cartelle pulita.
- Lovelace: due viste `it`/`en` per aggirare i limiti dei template nei titoli/etichette.

Suggerimenti futuri:
- Aggiungere custom cards (es. config-template-card) per rendere dinamiche anche le label delle card in base alla lingua.
- Creare preset stagionali e scheduler centralizzato.
