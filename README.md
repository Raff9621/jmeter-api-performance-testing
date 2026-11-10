# API Performance & Regression Testing Suite (Apache JMeter)

Progetto di testing automatizzato e di carico realizzato per validare le prestazioni, la stabilità e la correttezza funzionale di un'API REST pubblica (*JSONPlaceholder*), simulando scenari d'uso reali in ottica DevOps/QA.

## 🚀 Strumenti Utilizzati
* *Apache JMeter (v5.6.3):* Tool principale per la costruzione dello scenario di test, esecuzione del carico e validazione delle risposte.
* *Java (JDK):* Runtime environment per l'esecuzione di JMeter.
* *JSONPath:* Sintassi utilizzata per le asserzioni strutturali dei dati di risposta.

## 📊 Scenari di Test Implementati

1. *Load Testing (Test di Carico):*
   * *Thread Group:* 20 utenti simultanei con un ramp-up period di 10 secondi e 5 loop di esecuzione (Totale: 200 richieste).
   * *Endpoint testati:* 
     * GET /posts (Lettura della lista post)
     * POST /posts (Creazione di un nuovo post con payload JSON e Content-Type: application/json)

2. *Regression Testing (Test di Regressione):*
   * *Asserzioni di stato:* Verifica dei codici HTTP attesi (200 OK per le GET, 201 Created per le POST).
   * *Asserzioni di dati (JSON Assertion):* Validazione della struttura della risposta tramite espressione $.id per garantire l'integrità del contratto API.

## 📈 Risultati Chiave & Metriche (Summary Report)

| Metrica | Valore Rilevato | Spiegazione QA |
| :--- | :--- | :--- |
| *# Samples* | 200 richieste | 100 richieste GET e 100 richieste POST eseguite con successo. |
| *Average Response Time* | 245 ms | Tempo medio di risposta complessivo eccellente sotto carico. |
| *Max Response Time* | 4108 ms (sulla GET) | Picco di latenza registrato durante il recupero massivo della lista post. |
| *Error Rate* | *0.00%* | Stabilità totale del backend (nessun errore http riscontrato). |
| *Throughput* | 19.1 transazioni/sec | Capacità di elaborazione del sistema in esame. |

## 💡 Considerazioni e QA Insights
* *Stabilità e Affidabilità:* Il sistema ha gestito il carico con uno *0% di errori*, dimostrando un'ottima resilienza sulle chiamate di scrittura (POST).
* *Collo di bottiglia individuato:* La chiamata GET /posts ha mostrato una deviazione standard elevata e un picco massimo superiore ai 4 secondi, evidenziando una potenziale criticità di latenza nelle operazioni di lettura sotto concorrenza.
