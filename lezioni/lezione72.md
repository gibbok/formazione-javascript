# Selezione degli elementi

jQuery usa selettori CSS:

```javascript
$("#menu");
$(".voce.attiva");
$("form input[name=email]");
$("ul > li:first");
```

Per filtrare una collezione usare `filter`, `not`, `first`, `last`, `eq` e `find`:

```javascript
$("li").filter(".selezionata").find("a");
```

## Traversing

```javascript
const voce = $(".voce").first();
voce.parent();
voce.closest("nav");
voce.siblings();
voce.children();
```

`closest` risale fino all'antenato che corrisponde al selettore. Se non trova elementi, l'oggetto jQuery resta valido ma ha `length` uguale a zero.

## Selettori e prestazioni

Conservare il riferimento a una selezione usata più volte e preferire selettori semplici. Per elementi dinamici selezionare un antenato stabile e usare la delegazione degli eventi.

## Riepilogo

I selettori jQuery estendono CSS con filtri e metodi di navigazione. Capire la differenza tra collezione vuota e nodo nativo evita molti errori.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione71) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione73)
