# Arrow function

Esiste un’altra sintassi molto semplice e concisa per creare funzioni e che spesso è migliore delle Function Expressions.

E’ chiamata “arrow functions”, perché si presenta in questo modo:

```javascript
let func = (arg1, arg2, ...argN) => espressione
```

…oppure, con più di una riga di codice:

```javascript
let func = (arg1, arg2, ...argN) => {
  istruzioni
}
```

In effetti, è solo un’altra forma di sintassi per definire le funzioni, che è più breve e non ha il proprio `this`.

## Arrow function con un solo argomento

Se c’è un solo argomento, possiamo omettere le parentesi tonde:

```javascript
let double = n => n * 2;
```

## Arrow function senza argomenti

Se non ci sono argomenti, le parentesi tonde vanno lasciate vuote:

```javascript
let sayHi = () => alert("Hello!");
```

## Arrow function con più argomenti

Se ci sono più argomenti, le parentesi tonde vanno lasciate:

```javascript
let sum = (a, b) => a + b;
```

## Arrow functions su più linee

Le arrow functions possono contenere più di una riga di codice. In questo caso, le parentesi graffe `{}` sono necessarie:

```javascript
let sum = (a, b) => {
  let result = a + b;
  return result;
};
```

## Arrow functions come callback

Le arrow functions sono particolarmente utili quando si passano funzioni come callback. Ad esempio:

```javascript
let arr = [5, 8, 3];

let sorted = arr.sort((a, b) => a - b);

alert( sorted ); // 3, 5, 8
```

In questo esempio, `arr.sort` prende una funzione di confronto come argomento. Questa funzione di confronto è una arrow function che confronta due numeri e restituisce `a - b`.

## Valore restituito e `this`

Una arrow function con corpo espressione restituisce implicitamente il risultato; con un corpo a blocchi è necessario scrivere `return`:

```javascript
const doppio = numero => numero * 2;
const doppioEsplicito = numero => {
  return numero * 2;
};
const creaUtente = nome => ({ nome });
```

Le arrow function non hanno un proprio `this`, `arguments` o `prototype`: catturano `this` dallo scope esterno. Sono quindi ottime callback e funzioni brevi, ma un metodo che deve avere un `this` dinamico va spesso definito con la sintassi dei metodi o con `function`.

### Conclusioni

Le arrow functions sono una forma più breve e concisa di definire le funzioni in JavaScript. Sono particolarmente utili quando si passano funzioni come callback o quando si desidera scrivere codice più leggibile e conciso.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione16)
