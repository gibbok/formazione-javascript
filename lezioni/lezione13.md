# Funzioni

In questo capitolo vedremo come definire e utilizzare le funzioni in Javascript.

Molto spesso abbiamo la necessità di eseguire azioni simili in diverse parti dello script.

Ad esempio, vogliamo mostrare un messaggio quando un utente effettua il login/logout o per qualsiasi altro motivo.

Le funzioni sono le “fondamenta” di un programma. Consentono a un codice di essere utilizzato più volte, evitando ripetizioni.

## Definizione di una funzione

Una funzione è un blocco di codice che può essere eseguito in qualsiasi momento. Per definire una funzione in Javascript, utilizziamo la parola chiave `function`, seguita dal nome della funzione e da parentesi tonde `()`. Il blocco di codice da eseguire è racchiuso tra parentesi graffe `{}`.

Ecco un esempio di definizione di una funzione:

```javascript
function showMessage() {
  alert('Hello, World!');
}
```

In questo esempio, abbiamo definito una funzione chiamata `showMessage` che visualizza un messaggio di alert "Hello, World!".

## Chiamata di una funzione

Per eseguire una funzione, è necessario chiamarla. Per chiamare una funzione in Javascript, è sufficiente scrivere il nome della funzione seguito da parentesi tonde `()`.
Ecco un esempio di chiamata di una funzione:

```javascript
showMessage();
```

In questo esempio, stiamo chiamando la funzione `showMessage`, che visualizzerà un messaggio di alert "Hello, World!".

## Parametri di una funzione

Le funzioni possono accettare parametri, che sono valori passati alla funzione quando viene chiamata. I parametri vengono definiti tra parentesi tonde `()` nella definizione della funzione.

Ecco un esempio di funzione con parametri:

```javascript
function greet(name) {
  alert('Hello, ' + name + '!');
}
```

In questo esempio, abbiamo definito una funzione chiamata `greet` che accetta un parametro `name`. Quando la funzione viene chiamata, il valore del parametro `name` viene sostituito con il valore passato alla funzione.

Ecco un esempio di chiamata di una funzione con parametri:

```javascript
greet('John');
```

In questo esempio, stiamo chiamando la funzione `greet` con il parametro `'John'`, che visualizzerà un messaggio di alert "Hello, John!".

## Valore di ritorno di una funzione

Le funzioni possono restituire un valore. Per restituire un valore da una funzione in Javascript, utilizziamo la parola chiave `return`, seguita dal valore da restituire.

Ecco un esempio di funzione con valore di ritorno:

```javascript
function sum(a, b) {
  return a + b;
}
```

In questo esempio, abbiamo definito una funzione chiamata `sum` che accetta due parametri `a` e `b`. La funzione restituisce la somma dei due parametri.

Per utilizzare il valore restituito da una funzione, è necessario assegnarlo a una variabile o utilizzarlo direttamente.

Ecco un esempio di utilizzo del valore restituito da una funzione:

```javascript
let result = sum(2, 3);
alert(result); // 5
```

In questo esempio, stiamo chiamando la funzione `sum` con i parametri `2` e `3`, e assegnando il valore restituito a una variabile `result`. Successivamente, visualizziamo il valore della variabile `result` con un messaggio di alert.

## Variabili interne e esterne

Le variabili definite all'interno di una funzione sono chiamate variabili locali e sono visibili solo all'interno della funzione stessa. Le variabili definite al di fuori di una funzione sono chiamate variabili globali e sono visibili in tutto il codice.

Ecco un esempio di variabili locali e globali:

```javascript
let global
function showMessage() {
  let local = 'Hello, World!';
  global = 'Hello, Global!';
  alert(local);
}
showMessage();
alert(global);
alert(local); // Uncaught ReferenceError: local is not defined
```

In questo esempio, abbiamo definito una variabile globale `global` e una variabile locale `local`
all'interno della funzione `showMessage`. La variabile `local` è visibile solo all'interno della funzione `showMessage`, mentre la variabile `global` è visibile in tutto il codice.

## Valori di default dei parametri

In Javascript, è possibile definire valori di default per i parametri di una funzione. Se un parametro non viene passato alla funzione, verrà utilizzato il valore di default.

Ecco un esempio di valori di default dei parametri:

```javascript
function greet(name = 'World') {
  alert('Hello, ' + name + '!');
}
greet(); // Hello, World!
greet('John'); // Hello, John!
```

In questo esempio, abbiamo definito una funzione `greet` con un parametro `name` che ha un valore di default `'World'`. Se il parametro `name` non viene passato alla funzione, verrà utilizzato il valore di default `'World'`.

## Denominare una funzione

Le funzioni sono azioni. Solitamente, per il loro nome vengono utilizzati verbi. Dovrebbero essere brevi, il più accurati possibili e descrittivi di ciò che la funzione fa. Un estraneo che legge il codice deve essere in grado di capire ciò che fa la funzione.

Una pratica molto diffusa è quella di iniziare il nome con un verbo, come prefisso, che descriva vagamente l’azione. Deve esserci un accordo con il team riguardo il significato dei prefissi.

Ad esempio, le funzioni che iniziano con "show" solitamente mostrano qualcosa.

Funzioni che iniziano per…

- "get…" – ritornano un valore,
- "calc…" – calcolano qualcosa,
- "create…" – creano qualcosa,
- "check…" – controllano qualcosa e ritornano un booleano, etc.

Esempi di nomi:

```javascript
showMessage(..)     // mostra un messaggio
getAge(..)          // ritorna l'età (prendendola da qualche parte)
calcSum(..)         // calcola la somma e ritorna il risultato
createForm(..)      // crea un form (e solitamente lo ritorna)
checkPermission(..) // controlla i permessi, ritorna true/false
```

Tramite il prefisso, una semplice occhiata al nome della funzione dovrebbe far capire che tipo di lavoro eseguirà e quale sarà il tipo di valore ritornato.

Una funzione dovrebbe fare esattamente ciò che il suo nome descrive, niente di più.

Due azioni separate solitamente meritano due funzioni diverse, anche se molto spesso vengono chiamate insieme (in questo caso potrebbe essere utile creare una terza funzione che chiama entrambe).

## Parametri variabili e responsabilità

I parametri sono locali alla funzione. Se vengono passati meno argomenti, quelli mancanti valgono `undefined`; con il rest operator è possibile raccogliere un numero variabile di argomenti:

```javascript
function somma(...numeri) {
  return numeri.reduce((totale, numero) => totale + numero, 0);
}

console.log(somma(2, 3, 4)); // 9
```

Una funzione senza `return` restituisce `undefined`. È utile decidere se una funzione produce un valore, un effetto collaterale o entrambi, e mantenere questa responsabilità esplicita. Con `let` e `const` anche i blocchi `if`, `for` e `while` creano scope: evitare di modificare variabili globali rende le funzioni più facili da testare.

### Conclusioni

Le funzioni sono uno degli aspetti più importanti di Javascript. Consentono di organizzare il codice in blocchi riutilizzabili, evitando ripetizioni e semplificando la manutenzione del codice.

Le funzioni possono accettare parametri, restituire valori e avere variabili locali e globali. Possono essere denominate o anonime e possono essere assegnate a variabili o passate come argomenti ad altre funzioni.

Le funzioni sono fondamentali per la programmazione in Javascript e sono uno strumento potente per creare applicazioni web dinamiche e interattive.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione14)
