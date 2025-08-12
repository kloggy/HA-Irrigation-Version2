# 💧 HA Irrigation — Sistema di Irrigazione per Home Assistant (IT/EN)

Benvenuto nella versione **rifattorizzata** e **ottimizzata** di *HA Irrigation*.
Questa edizione introduce:

- 🌍 **Multilingua**: Italiano 🇮🇹 & Inglese 🇬🇧 (selettore `input_select.language_gui`)
- 🔄 **Blueprint riutilizzabili** (meno duplicazioni, più ordine)
- ☁️ **Adattamenti meteo** (pioggia/temperatura) pronti all’uso
- 🧰 **Struttura pulita** (pacchetti, logging dedicato, viste Lovelace IT/EN)
- 🛡️ **CI YAML** (yamllint) per prevenire errori di sintassi
- 📚 Documentazione semplice con esempi rapidi

> **Compatibilità:** Home Assistant Core/OS. È richiesto l’accesso alla cartella `config/` e la possibilità di aggiungere blueprint/pacchetti.

---

## 🚀 Installazione rapida (5 minuti)

1. **Copia file nella tua config HA**
   - `blueprints/automation/ha_irrigation/*.yaml`
   - `packages/i18n.yaml` *(selettore lingua + helper pausa pioggia)*
   - `logging/logging_irrigation.yaml` *(opzionale, consigliato)*
   - `lovelace/view_garden_irrigation.it.yaml` e/o `.en.yaml`
   - Se usi i *packages* in `configuration.yaml`, verifica di avere:
     ```yaml
     homeassistant:
       packages: !include_dir_merge_named packages
     ```

2. **Importa i Blueprint**
   - **Impostazioni → Automazioni e Scenari → Blueprint → Importa**
   - Seleziona i file in `blueprints/automation/ha_irrigation/`

3. **Scegli la lingua GUI**
   - **Impostazioni → Dispositivi e Servizi → Helper** → `input_select.language_gui`
   - Valori: `it` / `en`

4. **Aggiungi la vista Lovelace**
   - Dashboard → Modifica → **Modalità YAML** → includi la vista desiderata:
     ```yaml
     views:
       - !include lovelace/view_garden_irrigation.it.yaml
     ```

---

## 🧩 Blueprint inclusi

- **Default Controller WiFi** — imposta valore di default su `input_text` Wi‑Fi
- **Run Section Cycle** — avvia sezione per X minuti (con notifiche i18n)
- **Weather Adjust (Rainfall)** — pausa irrigazione se mm ≥ soglia
- **Weather Adjust (Temperature)** — scala i minuti in base ai °C
- **Cancel Program** — annulla subito i cicli in corso

> Tutti i blueprint supportano messaggi/localizzazione **IT/EN**.

---

## 📝 Esempi rapidi

### 1) Default Wi‑Fi
```yaml
use_blueprint:
  path: ha_irrigation/default_controller_wifi_signal.yaml
  input:
    wifi_input_text: input_text.irrigation_external_sensor_controller_1_wifi
    default_value_it: "Non impostato"
    default_value_en: "Not set"
```

### 2) Esecuzione sezione con notifica
```yaml
use_blueprint:
  path: ha_irrigation/run_section_cycle.yaml
  input:
    section_switch: switch.pompa_giardino
    duration_minutes: 15
    notify_service: notify.mobile_app_gianvito
```

### 3) Pausa per pioggia
```yaml
use_blueprint:
  path: ha_irrigation/weather_adjust_rainfall.yaml
  input:
    rainfall_sensor: sensor.rain_mm_today
    threshold_mm: 3.0
    boolean_pause_entity: input_boolean.irrigation_pause_due_rain
    notify_service: notify.mobile_app_gianvito
```

---

## 🧪 Manutenzione & qualità

- **CI YAML**: workflow GitHub Actions `yaml-validate.yml` con `yamllint`
- **Struttura pulita**: cartelle per blueprint, packages, logging, lovelace
- **Backup**: prima di grandi cambi, salva la tua `config/`

---

## 📦 Contenuti principali del progetto

```
blueprints/automation/ha_irrigation/
  ├─ default_controller_wifi_signal.yaml
  ├─ run_section_cycle.yaml
  ├─ weather_adjust_rainfall.yaml
  ├─ weather_adjust_temperature.yaml
  └─ cancel_program.yaml
packages/
  └─ i18n.yaml
logging/
  └─ logging_irrigation.yaml
lovelace/
  ├─ view_garden_irrigation.it.yaml
  └─ view_garden_irrigation.en.yaml
.github/workflows/
  └─ yaml-validate.yml
```

---

## ❓Supporto

- Apri una **Issue** con: versione HA, log/traceback, screenshot della dashboard.
- Specifica sensori/meteo usati (es. met.no, OpenWeather, SmartWeather).

---

## 🗺️ Roadmap (idee)

- Integrazione sensori umidità suolo
- Scheduler stagionale avanzato
- Modalità “Eco” con calcolo ottimizzato durate

> *Questo progetto è pensato per essere chiaro, modulare e facilmente estendibile.*
