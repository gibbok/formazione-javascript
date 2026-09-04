# Moduli

I moduli dividono il programma in file indipendenti. Ogni modulo dichiara ciò che esporta e importa solo le dipendenze necessarie, migliorando organizzazione, riuso, testabilità e isolamento.

## Moduli nel browser

```html
<script type="module" src="app.js"></script>
```

Gli script modulo sono differiti automaticamente, supportano `import` ed `export` e hanno uno scope isolato: le variabili non diventano globali. In molti ambienti devono essere serviti tramite HTTP; aprire direttamente un file può causare errori CORS.

## Named export e import

```javascript
// matematica.js
export function somma(a, b) {
  return a + b;
}

export const PI = 3.14159;
```

```javascript
// app.js
import { somma, PI } from "./matematica.js";

console.log(somma(2, 3));
console.log(PI);
```

Nei browser il percorso relativo e l'estensione del file sono importanti. `./matematica.js` indica un file nella stessa cartella.

## Alias e default export

```javascript
import { somma as addizione } from "./matematica.js";
```

Un modulo può avere un solo export predefinito:

```javascript
// utente.js
export default class Utente {
  constructor(nome) {
    this.nome = nome;
  }
}
```

```javascript
import Utente from "./utente.js";
```

Il nome dell'import default viene scelto dal file che importa. Gli export nominati invece mantengono il nome, salvo alias esplicito.

## Riesportare valori

```javascript
// index.js
export { somma, PI } from "./matematica.js";
export { default as Utente } from "./utente.js";
```

Un file indice può offrire un'API pubblica ordinata, ma un barrel file troppo grande può rendere meno chiari i collegamenti tra dipendenze.

## Scope e valutazione

Il codice principale di un modulo viene valutato una volta per URL. Le importazioni ricevono lo stesso binding condiviso:

```javascript
// contatore.js
let valore = 0;

export function incrementa() {
  valore += 1;
  return valore;
}
```

Importare `incrementa` da più file usa lo stesso stato del modulo. È quindi utile per alcuni singleton, ma lo stato globale condiviso va progettato con attenzione.

## Import dinamico

`import()` restituisce una Promise e carica codice solo quando serve:

```javascript
button.addEventListener("click", async () => {
  const modulo = await import("./editor.js");
  modulo.apriEditor();
});
```

È utile per funzionalità poco frequenti e per ridurre il codice iniziale scaricato.

## Moduli in Node.js

Node.js supporta i moduli ECMAScript con file `.mjs` o con questa impostazione in `package.json`:

```json
{
  "type": "module"
}
```

Nei progetti CommonJS sono invece comuni `require` e `module.exports`:

```javascript
const fs = require("node:fs");
module.exports = { leggiFile };
```

È preferibile scegliere un sistema e applicarlo in modo uniforme, seguendo la configurazione del progetto.

## Dipendenze circolari

Se il modulo A importa B e B importa A, alcuni binding possono essere letti prima di essere inizializzati. Le dipendenze circolari sono possibili, ma spesso indicano responsabilità troppo accoppiate; spostare la logica comune in un terzo modulo può rendere la struttura più chiara.

## Buone pratiche

- Usare nomi espliciti per file ed export.
- Importare soltanto ciò che serve.
- Mantenere i moduli piccoli e focalizzati.
- Evitare effetti collaterali durante l'importazione quando non necessari.
- Non esporre dettagli interni che non fanno parte dell'API.
- Usare percorsi coerenti con l'ambiente di esecuzione.

## Riepilogo

`export` rende disponibili valori e `import` li usa in un altro file. Gli export possono essere nominati o predefiniti. I moduli hanno scope isolato, vengono valutati una volta e possono essere caricati dinamicamente con `import()`.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione23) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione25)
