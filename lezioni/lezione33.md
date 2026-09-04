# Eventi

Gli eventi notificano che è accaduto qualcosa: un click, un input, il caricamento o una modifica della finestra.

## Ascoltare un evento

```javascript
const button = document.querySelector("button");

function gestisciClick(evento) {
  console.log(evento.type, evento.currentTarget);
}

button.addEventListener("click", gestisciClick);
```

`target` è l'elemento che ha originato l'evento; `currentTarget` è quello a cui è collegato il listener.

## Rimuovere un listener

La funzione deve essere lo stesso riferimento:

```javascript
button.removeEventListener("click", gestisciClick);
```

Le opzioni includono `once`, `passive` e `capture`:

```javascript
button.addEventListener("click", gestisciClick, { once: true });
```

## Prevenire il comportamento predefinito

```javascript
link.addEventListener("click", evento => {
  evento.preventDefault();
});
```

Usare `preventDefault` solo quando si sostituisce davvero il comportamento nativo.

## Riepilogo

Gli eventi separano l'azione dell'utente dalla reazione del programma. Registrare e rimuovere correttamente i listener evita perdite di memoria e comportamenti duplicati.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione32) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione34)
