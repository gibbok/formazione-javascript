# Eventi di tastiera

Gli eventi principali sono `keydown` e `keyup`. `keypress` è deprecato e non va usato per nuovo codice.

```javascript
document.addEventListener("keydown", evento => {
  if (evento.key === "Escape") chiudiDialogo();
  if (evento.key === "Enter" && evento.ctrlKey) invia();
});
```

`key` descrive il tasto, mentre `code` descrive la posizione fisica. `repeat` indica che il tasto è mantenuto premuto.

## Accessibilità

Non sostituire i controlli HTML con `div` cliccabili quando un `button` risolve il problema. Un pulsante riceve già focus e attiva correttamente la tastiera.

## Input di testo

Per leggere testo in un campo usare l'evento `input`. Evitare di intercettare ogni tasto per bloccare caratteri: validare il valore completo permette incolla, dettatura e layout internazionali.

## Riepilogo

Gestire combinazioni di tasti con `key` e modificatori, ma mantenere sempre un'alternativa accessibile e non impedire comportamenti standard senza motivo.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione36) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione38)
