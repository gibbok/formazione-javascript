# Events in Node.js

Molte API Node sono basate su `EventEmitter`.

```javascript
import { EventEmitter } from "node:events";

const bus = new EventEmitter();
bus.on("utente-creato", utente => console.log(utente));
bus.emit("utente-creato", { id: 1 });
```

`once` ascolta una sola volta, `off` rimuove un listener. Gli emitter con eventi `error` devono avere un listener per evitare terminazioni inattese. Gli eventi coordinano componenti, ma un uso eccessivo può nascondere il flusso dei dati.

## API dell'EventEmitter

```javascript
function ascoltaUnaVolta(emettitore) {
 emettitore.once("pronto", () => console.log("Pronto una sola volta"));
}

function gestisci(utente) {
 console.log("Creato", utente.id);
}

bus.on("utente-creato", gestisci);
bus.off("utente-creato", gestisci);
```

Il riferimento alla callback deve essere lo stesso per poterla rimuovere. `listenerCount`, `eventNames` e `rawListeners` aiutano nel debugging, non dovrebbero diventare parte della logica applicativa.

## Errori

```javascript
const emitter = new EventEmitter();
emitter.on("error", errore => {
 console.error("Errore dell'emitter", errore);
});
```

Un evento `error` senza listener può terminare il processo. Questo non sostituisce `try...catch`: gli errori sincroni nel listener e i rifiuti Promise devono essere gestiti separatamente.

## Eventi asincroni

Per attendere un evento una sola volta si può usare `events.once`:

```javascript
import { once } from "node:events";

const [utente] = await once(bus, "utente-creato");
```

Con `EventEmitter` non esiste automaticamente una coda persistente: un listener registrato dopo `emit` perde l'evento. Per messaggi affidabili usare una coda o uno stream progettato per quel requisito.

## EventEmitter e stream

Molte API Node, inclusi server HTTP e stream, emettono eventi. I listener devono essere leggeri; per lavoro asincrono usare `await` e gestire il backpressure invece di accumulare dati senza limite.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione55) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione57)
