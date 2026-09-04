# Il modulo File System

`node:fs/promises` offre operazioni asincrone sui file.

```javascript
import { readFile, writeFile } from "node:fs/promises";

const testo = await readFile("dati.txt", "utf8");
await writeFile("copia.txt", testo);
```

## Percorsi portabili

`process.cwd()` è la cartella da cui è stato avviato Node, non necessariamente quella del file corrente. Costruire i percorsi con `node:path`:

```javascript
import path from "node:path";
import { fileURLToPath } from "node:url";

const directory = path.dirname(fileURLToPath(import.meta.url));
const percorso = path.join(directory, "dati", "config.json");
```

Non usare `path.join` come protezione completa contro path traversal: se una parte arriva dall'utente, normalizzare e verificare che il risultato resti dentro la directory autorizzata.

## Operazioni comuni

```javascript
import { mkdir, readdir, stat, unlink } from "node:fs/promises";

await mkdir("backup", { recursive: true });
const nomi = await readdir("dati");
const informazioni = await stat("dati/config.json");
if (informazioni.isFile()) await unlink("backup/vecchio.json");
```

Usare le opzioni `encoding`, `flag` e `mode` consapevolmente. `writeFile` sostituisce il contenuto; `appendFile` aggiunge in coda. Per scritture importanti valutare file temporaneo e rename atomico.

## Errori e concorrenza

```javascript
try {
 await readFile("mancante.txt", "utf8");
} catch (errore) {
 if (errore.code === "ENOENT") {
  console.log("File assente");
 } else {
  throw errore;
 }
}
```

Non lanciare molte scritture concorrenti sullo stesso file senza coordinarle: l'ordine può diventare imprevedibile. Usare una coda o `await` sequenziali quando i risultati dipendono l'uno dall'altro.

## Stream

Per file grandi usare stream invece di caricare tutto in RAM:

```javascript
import { createReadStream, createWriteStream } from "node:fs";
import { pipeline } from "node:stream/promises";

await pipeline(
 createReadStream("origine.log"),
 createWriteStream("copia.log")
);
```

`pipeline` propaga errori e chiude correttamente le risorse. Gli stream applicano backpressure, cioè rallentano la sorgente quando la destinazione non riesce a consumare i dati abbastanza velocemente.

## Watcher

`watch` può notificare cambiamenti, ma gli editor possono generare più eventi per una singola modifica. Non usarlo come meccanismo di sincronizzazione affidabile senza deduplicare e gestire gli errori.

Usare `path` per costruire percorsi portabili e non concatenare input utente senza controlli. Gestire `ENOENT`, permessi e concorrenza. Per file grandi preferire stream invece di caricare tutto in memoria.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione52) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione54)
