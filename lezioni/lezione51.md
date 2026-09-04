# Moduli in Node.js

Node.js supporta moduli ECMAScript e CommonJS. Nei progetti moderni usare `type: module` per `import` ed `export`.

```json
{ "type": "module" }
```

```javascript
import fs from "node:fs/promises";
export async function leggi(percorso) {
  return fs.readFile(percorso, "utf8");
}
```

I moduli built-in usano il prefisso `node:`. Evitare dipendenze circolari e mantenere API piccole. Non confondere moduli Node con script browser: API e risoluzione dei percorsi sono diverse.

## CommonJS ed ECMAScript Modules

Node supporta due sistemi di moduli. CommonJS usa `require` e `module.exports`:

```javascript
// somma.cjs
function somma(a, b) {
  return a + b;
}

module.exports = { somma };
```

```javascript
const { somma } = require("./somma.cjs");
```

Gli ECMAScript Modules usano `import` ed `export`. Si attivano con l'estensione `.mjs` oppure con `"type": "module"` nel `package.json`:

```json
{
  "type": "module"
}
```

```javascript
// somma.js
export function somma(a, b) {
  return a + b;
}
```

Non mescolare i due sistemi senza una strategia chiara. In un modulo ESM `__dirname` e `__filename` non sono globali; per ottenere il percorso del file si può usare `import.meta.url`:

```javascript
import { fileURLToPath } from "node:url";
import { dirname } from "node:path";

const filename = fileURLToPath(import.meta.url);
const directory = dirname(filename);
```

## Moduli built-in e pacchetti

Il prefisso `node:` rende esplicito che il modulo è fornito da Node:

```javascript
import path from "node:path";
import { readFile } from "node:fs/promises";
```

Un import senza `./` o `../` viene cercato tra i pacchetti installati in `node_modules`. Non importare percorsi costruiti con input utente: la risoluzione dei moduli deve essere statica e controllata.

## Default, named export e API pubblica

```javascript
// configurazione.js
export const porta = 3000;
export default function creaConfigurazione() {
  return { porta };
}
```

```javascript
import creaConfigurazione, { porta } from "./configurazione.js";
```

Esportare solo ciò che fa parte del contratto del modulo. Le dipendenze circolari possono esporre binding non ancora inizializzati; spesso indicano che serve estrarre una responsabilità comune.

## Risoluzione e caching

Un modulo viene valutato una volta per specifico URL/percorso e le importazioni successive riusano il risultato. Questo comportamento è utile per configurazioni e singleton, ma lo stato mutabile esportato deve essere documentato.

## Import dinamico

```javascript
const plugin = await import("./plugin.js");
plugin.avvia();
```

`import()` restituisce una Promise e permette di caricare una funzionalità solo quando necessaria. Gli errori di caricamento vanno gestiti e il percorso deve essere compatibile con il bundler o il runtime.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione50) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione52)
