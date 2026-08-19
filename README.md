# Ritiro

Single Page Application in HTML e JavaScript puri (nessun framework, nessuna dipendenza)
per prenotare il ritiro di **Pacco Petra**: dove passare a prenderla, a che ora, e mandare
il tutto su WhatsApp con un tocco.

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

### Invio su WhatsApp

La conferma mostra l'anteprima del messaggio già pronto:

```
Ciao papà! Puoi venire a prendermi?

🎒 Pacco Petra
📍 Scuola media, Via Verdi 8
🕓 domani (giovedì 20 agosto) alle 16:30
📝 È con Giulia, ha lo zaino grande
```

Il pulsante **Mandalo su WhatsApp** apre un link `wa.me` con il testo già inserito:
sul telefono si apre l'app, sul computer WhatsApp Web. Salvando una volta il numero di
papà, il link punta direttamente alla sua chat (`https://wa.me/<numero>?text=…`);
senza numero WhatsApp chiede a chi mandarlo. C'è anche **Copia il messaggio** come
alternativa.

Il numero si scrive come viene: `+39 333 1234567`, `0039 333 1234567` o `333 1234567`
(a dieci cifre che iniziano per 3 viene aggiunto il prefisso 39). Resta salvato per le
volte successive.

### Regole applicate

- Si prenota da oggi fino a 30 giorni in anticipo.
- Luogo, giorno e ora sono obbligatori; gli errori sono mostrati sotto ai campi.

## Dati e persistenza

Tutto gira lato client: la prenotazione è salvata nel `localStorage` del browser
(chiave `ritiro.petra.v1`, il numero di papà in `ritiro.petra.papa.v1`) e la pagina non
invia nessuna richiesta di rete: l'unica cosa che esce è il link WhatsApp che apri tu.

## Struttura

Un unico file, `index.html`, con HTML, CSS e JavaScript. L'interfaccia è responsive
(desktop e mobile), supporta tema chiaro e scuro secondo le preferenze di sistema, ed è
navigabile da tastiera con etichette e messaggi di errore annunciati agli screen reader.
