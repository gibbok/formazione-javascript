# Proprietà del nodo: type, tag e content

Ogni nodo DOM espone informazioni sul proprio tipo e sul contenuto. Le proprietà più usate dipendono dal tipo di nodo.

```javascript
const elemento = document.querySelector("h1");
console.log(elemento.nodeType); // 1, elemento
console.log(elemento.nodeName); // H1
console.log(elemento.tagName);  // H1
```

## Contenuto testuale

`textContent` legge o imposta tutto il testo. `innerText` considera anche stile e layout, quindi può essere più costoso. Per inserire testo utente preferire sempre `textContent`.

```javascript
elemento.textContent = "Titolo sicuro";
```

## HTML interno

`innerHTML` permette di leggere o sostituire markup:

```javascript
elemento.innerHTML = "<em>Titolo</em>";
```

Non inserire dati esterni non sanificati con `innerHTML`: può causare XSS. Quando basta un elemento, usare `createElement` e `append`.

## Navigazione

`parentNode`, `children`, `firstChild`, `firstElementChild` e `nextSibling` navigano il documento. Distinguere nodi di testo ed elementi evita di leggere proprietà inesistenti.

## Riepilogo

`nodeType` identifica la categoria del nodo, mentre `textContent` è l'API sicura per il testo. `innerHTML` va riservato a markup controllato.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione27) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione29)
