# JSON

JSON è un formato testuale per scambiare dati strutturati. Supporta oggetti, array, stringhe, numeri, booleani e `null`, ma non funzioni, `undefined` o metodi.

```javascript
const oggetto = { nome: "Ada", attivo: true };
const testo = JSON.stringify(oggetto);
const copia = JSON.parse(testo);
```

## Opzioni

`JSON.stringify` accetta una funzione replacer o un array di proprietà e un numero di spazi per la formattazione:

```javascript
console.log(JSON.stringify(oggetto, null, 2));
```

Date diventano stringhe e riferimenti circolari causano un errore. `JSON.parse` può ricevere una reviver per trasformare valori, ma dati esterni vanno sempre validati dopo il parsing.

## Riepilogo

JSON è interoperabile ma limitato. Serializzare non equivale a clonare qualsiasi oggetto: tipi speciali, classi e riferimenti possono perdere informazioni.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione41) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione43)
