# Closure e scope

In questo capitolo vedremo cosa sono le closure in Javascript e come funzionano.

Una closure è una funzione che cattura le variabili dall'ambiente circostante in cui è stata definita. In altre parole, una closure è una funzione interna che ha accesso alle variabili della funzione esterna in cui è stata definita.

Ecco un esempio di closure in Javascript:

```javascript
function outerFunction() {
  var outerVariable = "I am from the outer function";

  function innerFunction() {
    console.log(outerVariable);
  }

  return innerFunction;
}

var inner = outerFunction();
inner(); // Output: I am from the outer function
```

In questo esempio, abbiamo definito una funzione esterna `outerFunction` che contiene una variabile `outerVariable` e una funzione interna `innerFunction`. La funzione interna `innerFunction` ha accesso alla variabile `outerVariable` della funzione esterna `outerFunction`.

Le closure sono utili per creare funzioni che mantengono lo stato tra le chiamate. Ad esempio, possiamo utilizzare le closure per creare funzioni che contano il numero di volte che vengono chiamate.

Ecco un esempio di utilizzo delle closure per creare una funzione che conta il numero di volte che viene chiamata:

```javascript
function counter() {
  var count = 0;

  function increment() {
    count++;
    console.log(count);
  }

  return increment;
}

var incrementCounter = counter();
incrementCounter(); // Output: 1
incrementCounter(); // Output: 2
incrementCounter(); // Output: 3
```

In questo esempio, abbiamo definito una funzione `counter` che contiene una variabile `count` e una funzione interna `increment`. La funzione interna `increment` incrementa la variabile `count` di 1 e stampa il valore.

## Scope

Lo scope in Javascript si riferisce alla visibilità delle variabili in una determinata parte del codice. Le variabili possono essere dichiarate all'interno di una funzione o all'esterno di essa, e il loro scope determina dove possono essere utilizzate.

Esistono due tipi di scope in Javascript: lo scope globale e lo scope locale.

### Scope globale

Le variabili dichiarate al di fuori di una funzione sono definite nello scope globale e sono visibili in tutto il codice.

Ecco un esempio di variabile globale:

```javascript
var globalVariable = "I am a global variable";

function showMessage() {
  console.log(globalVariable);
}

showMessage(); // Output: I am a global variable
```

In questo esempio, abbiamo definito una variabile globale `globalVariable` al di fuori della funzione `showMessage`. La variabile globale è visibile all'interno della funzione `showMessage` e può essere utilizzata all'interno di essa.

### Scope locale

Le variabili dichiarate all'interno di una funzione sono definite nello scope locale e sono visibili solo all'interno della funzione stessa.

Ecco un esempio di variabile locale:

```javascript
function showMessage() {
  var localVariable = "I am a local variable";
  console.log(localVariable);
}

showMessage(); // Output: I am a local variable

console.log(localVariable); // Uncaught ReferenceError: localVariable is not defined
```

In questo esempio, abbiamo definito una variabile locale `localVariable` all'interno della funzione `showMessage`. La variabile locale è visibile solo all'interno della funzione `showMessage` e non può essere utilizzata al di fuori di essa.

## Scope Chain

Lo scope chain in Javascript si riferisce all'ordine in cui le variabili vengono cercate all'interno di una funzione. Quando si cerca una variabile all'interno di una funzione, il motore Javascript inizia a cercare la variabile all'interno della funzione stessa, e se non la trova, continua a cercare all'interno delle funzioni genitore.

Ecco un esempio di scope chain in Javascript:

```javascript
var saluto = "Buongiorno";
var visualizzaSaluto;
function saluta(persona) {
  var nomeCognome = persona.nome + " " + persona.cognome;
  return function () {
    console.log(saluto + " " + nomeCognome);
  };
}
visualizzaSaluto = saluta({ nome: "Mario", cognome: "Rossi" });
visualizzaSaluto();
```

In questo caso la funzione `saluta()` non visualizza direttamente la stringa ma restituisce una funzione che assolve questo compito. Pertanto, quando la funzione restituita viene invocata, la funzione `saluta()` (la sua funzione esterna) ha terminato la sua esecuzione e quindi il suo contesto di esecuzione non esiste più. Nonostante ciò è ancora possibile accedere alla variabile `nomeCognome` presente nel suo `scope locale`.

## Closure e stato privato

Una closure conserva l'accesso alle variabili del proprio ambiente lessicale anche dopo il ritorno della funzione esterna. La variabile resta nello stesso ambiente condiviso dalle funzioni che la catturano.

```javascript
function creaContatore(iniziale = 0) {
  let valore = iniziale;

  return {
    incrementa() {
      valore += 1;
      return valore;
    },
    leggi() {
      return valore;
    }
  };
}

const contatore = creaContatore(10);
contatore.incrementa(); // 11
// contatore.valore non è accessibile dall'esterno
```

Le closure sono utili per incapsulare stato, creare factory e configurare callback. Poiché l'ambiente resta raggiungibile, una closure può mantenere in memoria dati voluminosi: listener e risorse non più necessari vanno rimossi.

### Conclusioni

In questo capitolo abbiamo visto cosa sono le closure e lo scope in Javascript. Le closure sono funzioni che catturano le variabili dall'ambiente circostante in cui sono state definite, mentre lo scope si riferisce alla visibilità delle variabili in una determinata parte del codice. Le closure sono utili per creare funzioni che mantengono lo stato tra le chiamate, mentre lo scope determina dove le variabili possono essere utilizzate.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione17)
