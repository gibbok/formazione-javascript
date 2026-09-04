# Dimensioni e scrolling

Il browser espone diverse dimensioni: `clientWidth` include contenuto e padding, `offsetWidth` include anche bordi e scrollbar, mentre `scrollWidth` misura il contenuto completo.

```javascript
const elemento = document.querySelector(".contenitore");
console.log(elemento.clientWidth);
console.log(elemento.scrollHeight);
```

## `getBoundingClientRect`

```javascript
const rettangolo = elemento.getBoundingClientRect();
console.log(rettangolo.top, rettangolo.left);
```

Le coordinate sono relative alla viewport. Per coordinate assolute aggiungere `scrollX` e `scrollY`.

## Scorrimento

```javascript
window.scrollTo({ top: 0, behavior: "smooth" });
elemento.scrollIntoView({ behavior: "smooth", block: "center" });
```

Lo scrolling può essere osservato con `scroll`, ma eventi frequenti vanno gestiti con cautela. `IntersectionObserver` è spesso migliore per capire se un elemento è visibile.

## Riepilogo

Scegliere la proprietà in base alla domanda: dimensione interna, dimensione esterna, contenuto completo o posizione nella viewport.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione31) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione33)
