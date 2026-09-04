# Bubbling e cattura degli eventi

Quando un evento si verifica su un elemento annidato, attraversa il DOM in tre fasi: cattura dall'antenato verso il bersaglio, target e bubbling dal bersaglio verso gli antenati.

```javascript
parent.addEventListener("click", () => console.log("bubbling"));
parent.addEventListener("click", () => console.log("capture"), { capture: true });
```

## Fermare la propagazione

`stopPropagation()` impedisce all'evento di continuare verso altri elementi. `stopImmediatePropagation()` impedisce anche altri listener sullo stesso elemento. Usarli raramente, perché possono rompere componenti indipendenti.

## Delegazione degli eventi

Il bubbling permette di gestire molti figli con un solo listener:

```javascript
lista.addEventListener("click", evento => {
  const voce = evento.target.closest("li");
  if (!voce || !lista.contains(voce)) return;
  console.log(voce.dataset.id);
});
```

La delegazione funziona anche per elementi aggiunti dopo il listener e riduce il numero di callback.

## Riepilogo

La fase di cattura è opzionale; il bubbling è il comportamento predefinito. La delegazione è utile per liste e interfacce dinamiche.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione33) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione35)
