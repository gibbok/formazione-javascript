# Eventi

`on` registra listener e `off` li rimuove:

```javascript
function apri() {
  $(".pannello").addClass("aperto");
}

$("button.apri").on("click", apri);
$("button.apri").off("click", apri);
```

L'oggetto evento contiene `target`, `currentTarget`, `key` e metodi come `preventDefault` e `stopPropagation`.

## Delegazione

```javascript
$("ul").on("click", "li", function (evento) {
  $(this).toggleClass("selezionato");
});
```

La delegazione ascolta un antenato e funziona anche per figli creati successivamente. Usare namespace per gestire gruppi di listener:

```javascript
$(window).on("resize.layout", aggiorna);
$(window).off("resize.layout");
```

## Form e dati

```javascript
$("form").on("submit", function (evento) {
  evento.preventDefault();
  const valori = $(this).serialize();
  console.log(valori);
});
```

Non impedire comportamenti nativi senza offrire un'alternativa accessibile.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione73) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione75)
