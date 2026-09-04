# Introduzione a jQuery

jQuery è una libreria JavaScript che semplifica selezione DOM, eventi, manipolazione e richieste AJAX. È stata molto importante prima delle API moderne del browser; oggi va introdotta anche in rapporto a `querySelector`, `fetch` e moduli nativi.

## Installazione

```html
<script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
<script src="app.js"></script>
```

In produzione preferire una dipendenza versionata e verificare integrità, licenza e compatibilità. Con NPM:

```bash
npm install jquery
```

```javascript
import $ from "jquery";
```

## Primo utilizzo

```javascript
$(function () {
  $("#titolo").text("Pagina pronta");
});
```

`$` è l'alias della funzione jQuery. `$(callback)` esegue il codice quando il DOM è pronto.

## Collezioni jQuery

Un oggetto jQuery può contenere zero, uno o più elementi. I metodi spesso applicano l'operazione a tutta la collezione e restituiscono la collezione per il chaining:

```javascript
$(".scheda").addClass("visibile").attr("data-pronta", "true");
```

Controllare `.length` quando un elemento è obbligatorio. jQuery non è il DOM: per ottenere il nodo nativo usare `[0]` o `.get(0)`.

## Riepilogo

jQuery è una API coerente per il DOM, ma le API native restano importanti per progetti moderni. Evitare di mescolare indiscriminatamente wrapper jQuery e nodi nativi.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione72)
