# Il DOM

Il DOM (Document Object Model) è la rappresentazione ad albero del documento HTML. Ogni elemento diventa un nodo che JavaScript può leggere e modificare.

```html
<body>
  <h1 id="titolo">Benvenuto</h1>
  <p>Testo introduttivo</p>
</body>
```

```javascript
console.log(document.body);
console.log(document.body.children[0].textContent);
```

## Nodi ed elementi

Il documento contiene elementi, testo e commenti. `children` restituisce solo elementi figli, mentre `childNodes` include anche nodi di testo. `parentElement`, `firstElementChild` e `nextElementSibling` permettono di navigare l'albero.

## Aggiornare il contenuto

```javascript
const titolo = document.querySelector("h1");
titolo.textContent = "Titolo aggiornato";
```

`textContent` tratta il valore come testo. `innerHTML` interpreta markup e va usato solo con contenuto fidato o sanificato.

## Creare nodi

```javascript
const elemento = document.createElement("p");
elemento.textContent = "Creato con JavaScript";
document.body.append(elemento);
```

## Riepilogo

Il DOM è un albero vivo: leggere o modificare i nodi cambia la pagina. Preferire API testuali e operazioni mirate evita problemi di sicurezza e prestazioni.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione25) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione27)
