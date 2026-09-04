# Introduzione a Node.js

Node.js è un runtime che esegue JavaScript fuori dal browser usando il motore V8. Offre API per rete, file system, processi e stream.

```javascript
console.log(process.version);
console.log("Argomenti:", process.argv.slice(2));
```

Node usa un event loop e API asincrone, quindi è adatto a molti I/O concorrenti. Un calcolo CPU-intensivo può però bloccare il thread principale.

## Il processo e l'event loop

Il processo Node è rappresentato dall'oggetto globale `process`. Oltre agli argomenti della riga di comando, espone variabili d'ambiente, codice di uscita e segnali del sistema:

```javascript
console.log(process.env.NODE_ENV ?? "development");

process.on("SIGTERM", () => {
 console.log("Chiusura richiesta");
 process.exit(0);
});
```

L'event loop coordina callback di rete, file e timer. Un'operazione asincrona libera il thread mentre il sistema operativo lavora; quando termina, Node inserisce il callback nella coda. Le API sincrone come `readFileSync` bloccano invece l'intero processo e sono da usare con cautela in un server.

## Struttura di un progetto

Una struttura iniziale può separare responsabilità e configurazione:

```text
app/
 src/
  server.js
  routes/
  services/
 test/
 package.json
 .env
```

Il file `.env` non va versionato se contiene segreti. In produzione configurare logging, gestione degli errori e chiusura ordinata del server.

## Errori e terminazione

Le Promise devono essere attese o gestite. Un `unhandledRejection` indica spesso un bug, non un normale flusso applicativo. Usare `try...catch` nei confini asincroni e terminare il processo solo dopo aver chiuso risorse come server, pool e connessioni.

## Progetto iniziale

```bash
npm init -y
node app.js
```

Gli script definiti in `package.json` permettono di standardizzare i comandi:

```json
{
 "scripts": {
  "start": "node src/server.js",
  "dev": "node --watch src/server.js"
 }
}
```

Si eseguono con `npm start` e `npm run dev`.

Usare variabili d'ambiente per configurazione e non inserire segreti nel repository.

## Riepilogo

Node.js è un runtime, non un linguaggio diverso. Il codice disponibile dipende dalle API Node e non dal DOM del browser.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione51)
