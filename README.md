# Ritiro

Single Page Application in HTML e JavaScript puri (nessun framework, nessuna dipendenza)
per prenotare il ritiro di **Pacco Petra**: dove passare a prenderla e a che ora.

## Come si usa

Apri `index.html` in un browser — anche con doppio clic, senza web server.
In alternativa, per servirlo localmente:

```bash
python3 -m http.server 8000   # poi apri http://localhost:8000
```

## Funzionalità

Il pacco è sempre lo stesso — Pacco Petra, 1 collo, fragile — quindi il modulo chiede
soltanto l'essenziale:

- **Dove la prendo** (obbligatorio)
- **Giorno** e **ora** (obbligatori)
- **Note** (facoltativo): con chi è, cosa deve portare, dove aspetta

Alla conferma compare il riepilogo con il giorno in forma leggibile ("oggi", "domani",
"dopodomani" o la data estesa), l'ora, il luogo e un codice ritiro.
Da lì si può **modificare** la prenotazione (il codice resta lo stesso) oppure
**annullarla**.

C'è una sola prenotazione alla volta: riaprendo la pagina si ritrova quella attiva.

### Regole applicate

- Si prenota da oggi fino a 30 giorni in anticipo.
- Luogo, giorno e ora sono obbligatori; gli errori sono mostrati sotto ai campi.

## Dati e persistenza

Tutto gira lato client: la prenotazione è salvata nel `localStorage` del browser
(chiave `ritiro.petra.v1`) e non viene inviata alcuna richiesta di rete.

## Struttura

Un unico file, `index.html`, con HTML, CSS e JavaScript. L'interfaccia è responsive
(desktop e mobile), supporta tema chiaro e scuro secondo le preferenze di sistema, ed è
navigabile da tastiera con etichette e messaggi di errore annunciati agli screen reader.
