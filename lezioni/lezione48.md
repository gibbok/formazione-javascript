# IndexedDB

IndexedDB è un database asincrono nel browser per quantità di dati maggiori e strutture più ricche rispetto a `localStorage`.

```javascript
const richiesta = indexedDB.open("app", 1);

richiesta.onupgradeneeded = () => {
  richiesta.result.createObjectStore("note", { keyPath: "id", autoIncrement: true });
};

richiesta.onsuccess = () => {
  const db = richiesta.result;
  const transazione = db.transaction("note", "readwrite");
  transazione.objectStore("note").add({ testo: "Studiare IndexedDB" });
};
```

Le modifiche allo schema vanno gestite in `onupgradeneeded`. Le transazioni sono atomiche e devono restare brevi. Per progetti complessi una libreria wrapper può ridurre il codice ripetitivo.

IndexedDB è same-origin e non va considerato un archivio sicuro: il codice della stessa origine può accedervi.

## Riepilogo

IndexedDB è asincrono, transazionale e adatto a dati offline. Progettare schema, versioni, indici e gestione errori prima di usarlo in produzione.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione47) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione49)
