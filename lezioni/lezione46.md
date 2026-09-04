# Local storage e session storage

`localStorage` conserva stringhe associate all'origine anche dopo la chiusura del browser; `sessionStorage` dura per la sessione della scheda.

```javascript
localStorage.setItem("tema", "scuro");
const tema = localStorage.getItem("tema");
localStorage.removeItem("tema");
```

Per oggetti usare JSON:

```javascript
localStorage.setItem("preferenze", JSON.stringify({ tema: "scuro" }));
const preferenze = JSON.parse(localStorage.getItem("preferenze") ?? "null");
```

Lo storage è sincrono, ha spazio limitato e non va usato per segreti o grandi quantità di dati. Gli eventi `storage` notificano altre schede della stessa origine.

## Riepilogo

Usare storage per preferenze semplici e non sensibili. Gestire quota, dati corrotti e indisponibilità in modalità privata.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione45) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione47)
