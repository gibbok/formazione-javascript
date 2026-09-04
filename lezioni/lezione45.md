# Web Workers

Un Web Worker esegue JavaScript in un contesto separato e lascia libero il main thread per interfaccia e input.

```javascript
// app.js
const worker = new Worker("worker.js", { type: "module" });
worker.postMessage({ numero: 100000 });
worker.onmessage = evento => console.log(evento.data);
worker.onerror = console.error;
```

```javascript
// worker.js
self.onmessage = evento => {
  const risultato = calcola(evento.data.numero);
  self.postMessage(risultato);
};
```

I worker non accedono direttamente al DOM. I dati passano con structured clone; oggetti trasferibili come `ArrayBuffer` possono essere trasferiti invece che copiati. Chiudere il worker con `terminate()` quando non serve più.

## Riepilogo

Usare worker per calcoli CPU-intensivi, non per ogni operazione. La comunicazione è asincrona e il costo di copia dei dati va considerato.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione44) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione46)
