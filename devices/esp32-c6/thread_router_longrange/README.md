# ESP32-C6 Thread Router (Long Range)

Questo pacchetto configura un **ESP32-C6** come un **Thread Router** (Full Thread Device) ottimizzato per la lunga portata. Agisce come estensore della rete mesh Thread, migliorando la copertura per i dispositivi a batteria (MTD), ma **non** funge da Border Router (non collega la rete Thread alla Wi-Fi/LAN).

## 🛠 Hardware Necessario

Per massimizzare la portata del segnale, è fondamentale utilizzare i seguenti componenti:

*   **Microcontrollore:** ESP32-C6 con connettore **U.FL** integrato (necessario per antenna esterna).
*   **Antenna:** Antenna Wi-Fi/Zigbee/Thread ad alto guadagno (minimo **3dBi**).
*   **Connessione:** Cavo pigtail da **U.FL a SMA** per collegare l'antenna al modulo.

---

## 🚀 Configurazione ESPHome

Copia e adatta il seguente codice nel tuo file YAML di ESPHome per integrare il router.

```yaml
substitutions:
  name: "thread-router-01"
  friendly_name: "Thread Router Long Range"
  api_key: "IL_TUO_API_KEY"
  ota_password: "LA_TUA_OTA_PASSWORD"
  openthread_tlv: "TUO TLV RETE THREAD"

packages:
  remote_package:
    url: https://github.com/perni24/esp_home_script.git
    ref: main
    file: devices/esp32-c6/thread_router_longrange/thread_router_longrange.yaml
    refresh: 1d
```

### 📋 Dettaglio Variabili

| Variabile | Descrizione |
| :--- | :--- |
| `name` | ID univoco del dispositivo (usato per l'hostname). |
| `friendly_name` | Nome visualizzato in Home Assistant. |
| `api_key` | Chiave di sicurezza per le API di ESPHome. |
| `ota_password` | Password per gli aggiornamenti wireless. |
| `openthread_tlv` | Dataset della rete Thread in formato TLV (es. preso da HA). |

---

## 💡 Note d'uso

1. **Antenna:** Assicurati che l'antenna sia ben salda. Una cattiva connessione U.FL può danneggiare il chip radio o ridurre drasticamente le prestazioni.
2. **Posizionamento:** Trattandosi di un router "Long Range", posizionalo in un punto centrale o elevato per fungere da ponte verso i sensori più lontani della tua rete mesh.
3. **Dataset Thread:** Se utilizzi Home Assistant, puoi trovare il dataset TLV nelle impostazioni dell'integrazione Thread.