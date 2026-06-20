# MIGRATION (Phase 1 — Blueprints, CI, i18n)

Questa fase introduce:
- blueprint riutilizzabili,
- validazione YAML via GitHub Actions,
- selettore lingua (`input_select.language_gui`) IT/EN per notifiche e testi generati dai blueprint,
- viste Lovelace separate `it`/`en` (limite tecnico: Lovelace non valuta Jinja ovunque).

## Passi
1. Copia `packages/i18n.yaml` nella tua config (o caricalo come package).
2. Copia `blueprints/automation/ha_irrigation/*.yaml`.
3. (Opzionale) Aggiungi `logging/logging_irrigation.yaml`.
4. Scegli la vista Lovelace: `lovelace/view_garden_irrigation.it.yaml` o `.en.yaml`.
5. Istanzia i blueprint al posto delle automazioni duplicate.

## Esempio istanza (default WiFi)
```yaml
use_blueprint:
  path: ha_irrigation/default_controller_wifi_signal.yaml
  input:
    wifi_input_text: input_text.irrigation_external_sensor_controller_1_wifi
    default_value_it: "Non impostato"
    default_value_en: "Not set"
```
