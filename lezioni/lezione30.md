# Modificare il documento

JavaScript può creare, inserire, spostare e rimuovere elementi del DOM.

## Creare e inserire

```javascript
const lista = document.querySelector("ul");
const elemento = document.createElement("li");
elemento.textContent = "Nuovo elemento";
lista.append(elemento);
```

`append` accetta nodi e stringhe, mentre `appendChild` accetta un nodo e restituisce il nodo inserito. `prepend`, `before` e `after` coprono altri punti di inserimento.

## Spostare e rimuovere

Inserire un nodo già presente lo sposta, non lo duplica:

```javascript
lista.prepend(elemento);
elemento.remove();
```

## Frammenti

Per molte modifiche, `DocumentFragment` riduce gli aggiornamenti intermedi:

```javascript
const frammento = document.createDocumentFragment();
for (const nome of ["Ada", "Grace"]) {
  const li = document.createElement("li");
  li.textContent = nome;
  frammento.append(li);
}
lista.append(frammento);
```

## Template

`template.content.cloneNode(true)` è utile per riusare markup controllato. Evitare di inserire dati utente con `innerHTML`.

## Riepilogo

Creare nodi separa contenuto e struttura. Usare API DOM, frammenti per molti elementi e `textContent` per dati non fidati.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione29) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione31)
