# Stili e classi

Per modificare l'aspetto di un elemento è preferibile usare classi CSS, invece di assegnare molti stili inline.

```javascript
const pannello = document.querySelector(".pannello");
pannello.classList.add("aperto");
pannello.classList.toggle("evidenziato");
pannello.classList.remove("nascosto");
```

`contains` verifica una classe e `toggle(nome, condizione)` permette di sincronizzarla con uno stato booleano.

## Stili inline

```javascript
pannello.style.backgroundColor = "white";
pannello.style.setProperty("--accento", "teal");
```

Le proprietà CSS diventano camelCase. Gli stili inline hanno priorità elevata e possono rendere difficile la manutenzione.

## Stili calcolati

```javascript
const stile = getComputedStyle(pannello);
console.log(stile.display);
```

Il valore può provenire da un foglio CSS e non è necessariamente impostabile nello stesso oggetto.

## Riepilogo

`classList` mantiene separati comportamento e presentazione. Usare `style` per valori dinamici puntuali e CSS per regole riutilizzabili.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione30) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione32)
