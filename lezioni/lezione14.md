# Function expression

In JavaScript, una funzione non è una “struttura magica del linguaggio”, ma un valore speciale.

La sintassi che abbiamo utilizzato finora viene chiamata Dichiarazione di Funzione:

```javascript
function sayHi() {
  alert( "Hello" );
}
```

E’ disponibile un’altra sintassi per creare una funzione, chiamata function expression.

La sintassi:

```javascript
let sayHi = function() {
  alert( "Hello" );
};
```

Qui la funzione viene esplicitamente creata ed assegnata ad una variabile, proprio come un qualsiasi altro valore. Non ha importanza come la funzione viene definita, è solo un valore salvato nella variabile sayHi.

Il significato di questo esempio è lo stesso di: “crea una funzione e mettila dentro la variabile sayHi”.

## Funzioni anonime

Le funzioni create con la function expression sono sempre funzioni anonime. Non hanno un nome, come le funzioni definite con la dichiarazione di funzione.

Per esempio, questa funzione expression:

```javascript
let sayHi = function() {
  alert( "Hello" );
};
```

Non ha un nome. In realtà, potremmo assegnarle uno:

```javascript
let sayHi = function func(who) {
  alert( `Hello, ${who}` );
};
```

Ma non è molto utile, perché non possiamo fare riferimento alla funzione dall’interno di se stessa.

## Callback functions

Le funzioni possono essere passate come valori ad altre funzioni. Quando una funzione viene passata come argomento ad un’altra funzione, viene chiamata callback function.

Per esempio, possiamo scrivere una funzione che prenda un’altra funzione come argomento e la chiami:

```javascript
function ask(question, yes, no) {
  if (confirm(question)) yes();
  else no();
}

function yes() {
  alert( "You agreed." );
}

function no() {
  alert( "You canceled the execution." );
}

ask("Do you agree?", yes, no);
```

In questo esempio, la funzione `ask` prende tre argomenti:

- `question` è la domanda da fare
- `yes` è la funzione da chiamare se l’utente risponde “sì”
- `no` è la funzione da chiamare se l’utente risponde “no”

La funzione `ask` mostra la domanda e, a seconda della risposta, chiama `yes()` o `no()`.

## Function expression vs Dichiarazione di Funzioni

Le funzioni create con la function expression sono diverse dalle dichiarazioni di funzione. La principale differenza è quando vengono create e come vengono trattate dal motore JavaScript.

### 1. Prima dell’esecuzione: le dichiarazioni di funzione

Una dichiarazione di funzione può essere chiamata “prima” della sua dichiarazione. Per esempio:

```javascript
sayHi("John"); // Hello, John

function sayHi(name) {
  alert( `Hello, ${name}` );
}
```

Questo è possibile grazie al concetto di “sollevamento” (hoisting). Prima che il codice venga eseguito, il motore JavaScript cerca tutte le dichiarazioni di funzione e le “solleva” all’inizio del blocco di codice.

### 2. Dopo l’esecuzione: le funzioni expression

Le funzioni create con la function expression sono diverse. Non vengono sollevate. Non possono essere chiamate prima della loro dichiarazione.

Per esempio, questo codice non funziona:

```javascript
sayHi("John"); // errore!

let sayHi = function(name) {  // (*) non possiamo chiamare sayHi prima della sua dichiarazione
  alert( `Hello, ${name}` );
};
```

## Passare una callback correttamente

Quando una callback viene passata, si passa il riferimento senza parentesi: `ask("...", yes, no)`. Scrivere `yes()` la eseguirebbe immediatamente e passerebbe il suo risultato.

```javascript
function applica(valore, trasformazione) {
  return trasformazione(valore);
}

const risultato = applica(3, function (numero) {
  return numero * 2;
});
```

Una dichiarazione di funzione viene resa disponibile prima dell'esecuzione. Una function expression assegnata a `let` o `const` segue invece le regole della variabile e non va usata prima della dichiarazione.

### Conclusioni

Le funzioni create con la function expression sono diverse dalle dichiarazioni di funzione. Non vengono sollevate e non possono essere chiamate prima della loro dichiarazione. Sono sempre funzioni anonime, anche se assegniamo loro un nome. Le funzioni expression sono utili per passare funzioni come argomenti ad altre funzioni, ad esempio per creare callback functions.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione15)
