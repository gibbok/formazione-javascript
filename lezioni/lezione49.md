# Regular expressions

Le espressioni regolari descrivono pattern testuali. Sono utili per ricerche e validazioni semplici, ma non sostituiscono parser per linguaggi complessi.

```javascript
const pattern = /^[a-z]+@[a-z]+\.[a-z]{2,}$/i;
console.log(pattern.test("ada@example.com"));
```

## Metodi comuni

`test` restituisce un booleano; `match` estrae risultati; `replace` sostituisce; `search` restituisce la posizione.

```javascript
const testo = "Ordine 42";
console.log(testo.match(/\d+/)?.[0]); // 42
console.log(testo.replace(/\d+/, "43"));
```

I flag principali sono `i` per case-insensitive, `g` per tutte le occorrenze, `m` per più righe e `u` per Unicode.

Pattern troppo complessi possono causare backtracking costoso. Evitare espressioni ambigue su input non fidato e limitare la lunghezza dei dati.

## Riepilogo

Una regular expression è potente per pattern locali. Leggibilità, test e limiti sull'input sono essenziali.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione48) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione50)
