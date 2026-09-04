# Il Browser

Il browser è l'ambiente che interpreta HTML, CSS e JavaScript. Espone API web attraverso oggetti come `window`, `document`, `navigator`, `location` e `history`.

## `window` e `document`

`window` rappresenta la finestra e il contesto globale della pagina. `document` rappresenta il documento HTML caricato.

```javascript
console.log(window.innerWidth);
console.log(document.title);
console.log(location.href);
```

Molte proprietà globali sono accessibili senza scrivere `window`, ma usare il prefisso può rendere più chiaro l'ambiente a cui appartengono.

## Ciclo di vita

Il browser scarica la risposta, costruisce il DOM, calcola gli stili e disegna la pagina. JavaScript può modificare il DOM e provocare un nuovo calcolo del layout.

```javascript
window.addEventListener("load", () => {
  console.log("Pagina e risorse caricate");
});
```

`DOMContentLoaded` arriva quando l'HTML è stato analizzato; `load` aspetta anche immagini e altre risorse.

## Sicurezza e origine

La Same-Origin Policy limita l'accesso tra origini diverse. Un'origine è data da protocollo, dominio e porta. CORS consente a un server di autorizzare esplicitamente alcune richieste cross-origin.

## Riepilogo

Il browser fornisce il runtime e le API, mentre JavaScript fornisce il linguaggio. Conoscere il ciclo di vita e l'origine aiuta a prevedere quando e dove il codice può operare.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione26)
