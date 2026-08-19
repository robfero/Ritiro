# Ritiro

Single Page Application in HTML e JavaScript puri (nessun framework, nessuna dipendenza)
per prenotare il ritiro a domicilio di un pacco.

## Come si usa

Apri `index.html` in un browser — anche con doppio clic, senza web server.
In alternativa, per servirlo localmente:

```bash
python3 -m http.server 8000   # poi apri http://localhost:8000
```

## Funzionalità

**Prenotazione in 4 passi**, con barra di avanzamento e validazione a ogni passo:

1. **Ritiro** — contatti del mittente e indirizzo di ritiro (via, CAP, città, provincia, note per il corriere).
2. **Pacco** — contenuto, numero di colli, peso, dimensioni, opzioni fragile/assicurazione e dati del destinatario.
3. **Data e ora** — data del ritiro e fascia oraria, con servizio standard o express.
4. **Conferma** — riepilogo completo, preventivo dettagliato e accettazione delle condizioni.

Al termine viene generato un codice di prenotazione (`RIT-XXXXXX`) e il riepilogo del ritiro.

### Regole applicate

- Il ritiro si prenota da domani fino a 30 giorni in anticipo; la domenica non è disponibile.
- Ogni fascia oraria accetta al massimo 3 ritiri: le fasce piene vengono mostrate come "Al completo" e disabilitate.
- Validazione dei campi: email, telefono, CAP a 5 cifre, sigla provincia, 1–10 colli, peso 0,1–50 kg, misure 1–200 cm.
- Preventivo calcolato su base + peso oltre il primo kg + colli aggiuntivi + fragile + assicurazione + express.

### Le mie prenotazioni

Sezione con l'elenco dei ritiri prenotati, il loro stato (confermato / completato / annullato)
e la possibilità di annullare una prenotazione fino al giorno prima. L'annullamento libera
subito il posto nella fascia oraria.

## Dati e persistenza

Tutto gira lato client: i dati vengono salvati nel `localStorage` del browser e non viene
inviata alcuna richiesta di rete.

- `ritiro.bookings.v1` — le prenotazioni effettuate
- `ritiro.draft.v1` — la bozza del modulo, ripristinata se ricarichi la pagina

## Struttura

Un unico file, `index.html`, con HTML, CSS e JavaScript. L'interfaccia è responsive
(desktop e mobile), supporta tema chiaro e scuro secondo le preferenze di sistema, ed è
navigabile da tastiera con etichette e messaggi di errore annunciati agli screen reader.
