# Popup e window

`window` rappresenta la finestra del browser e offre API per dialoghi, timer, navigazione e dimensioni.

```javascript
const finestra = window.open("/aiuto.html", "aiuto", "width=600,height=400");
finestra?.focus();
```

I popup possono essere bloccati dal browser se non nascono da un'azione dell'utente. `alert`, `confirm` e `prompt` sono sincroni e vanno usati con moderazione.

## Navigazione e timer

```javascript
window.location.assign("/profilo");
const timer = setTimeout(() => console.log("Fatto"), 1000);
clearTimeout(timer);
```

`setInterval` va cancellato con `clearInterval`. Non usare timer per animazioni: preferire `requestAnimationFrame`.

## Riepilogo

Le API `window` controllano il contesto della pagina, ma popup, navigazione e accesso a finestre diverse sono limitati da sicurezza e permessi.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione42)
