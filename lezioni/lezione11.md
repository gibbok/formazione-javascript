# Cicli: while e for

In JavaScript, i cicli sono utilizzati per eseguire un blocco di codice ripetutamente fino a quando una condizione specificata è vera. Ci sono diversi tipi di cicli in JavaScript, tra cui `while`, `do...while` e `for`.

## Il ciclo while

Il ciclo `while` esegue un blocco di codice finché una condizione specificata è vera. Ecco un esempio di utilizzo del ciclo `while` in JavaScript:

```javascript
var i = 0;

while (i < 5) {
  console.log(i);
  i++;
}
```

In questo esempio, il ciclo `while` esegue il blocco di codice finché la variabile `i` è minore di 5. Ad ogni iterazione, la variabile `i` viene incrementata di 1.

## Il ciclo do...while

Il ciclo `do...while` è simile al ciclo `while`, ma esegue il blocco di codice almeno una volta, anche se la condizione specificata è falsa. Ecco un esempio di utilizzo del ciclo `do...while` in JavaScript:

```javascript
var i = 0;

do {
  console.log(i);
  i++;
} while (i < 5);
```

In questo esempio, il ciclo `do...while` esegue il blocco di codice almeno una volta, anche se la variabile `i` è maggiore di 5. Successivamente, esegue il blocco di codice finché la variabile `i` è minore di 5.

## Il ciclo for

Il ciclo `for` è utilizzato per eseguire un blocco di codice un numero specificato di volte. Ecco un esempio di utilizzo del ciclo `for` in JavaScript:

```javascript
for (var i = 0; i < 5; i++) {
  console.log(i);
}
```

In questo esempio, il ciclo `for` esegue il blocco di codice finché la variabile `i` è minore di 5. Ad ogni iterazione, la variabile `i` viene incrementata di 1.

La forma `for` è adatta quando esiste un contatore o una sequenza da percorrere. Con `let`, la variabile del ciclo resta confinata al ciclo:

```javascript
for (let indice = 0; indice < 3; indice++) {
  console.log(indice);
}
// indice non è disponibile qui
```

Usare `while` quando il numero di iterazioni dipende da una condizione che cambia durante l'esecuzione. In ogni ciclo è essenziale assicurarsi che la condizione possa diventare falsa, altrimenti si crea un ciclo infinito.

### Il ciclo for in

Il ciclo `for...in` è utilizzato per iterare su tutte le proprietà di un oggetto. Ecco un esempio di utilizzo del ciclo `for...in` in JavaScript:

```javascript
var person = {name: "John", age: 30, city: "New York"};

for (var key in person) {
  console.log(key + ": " + person[key]);
}
```

In questo esempio, il ciclo `for...in` itera su tutte le proprietà dell'oggetto `person` e stampa il nome della proprietà e il suo valore.

### Il ciclo for of

Il ciclo `for...of` è utilizzato per iterare su tutti gli elementi di un oggetto iterabile, come ad esempio un array. Ecco un esempio di utilizzo del ciclo `for...of` in JavaScript:

```javascript
var colors = ["red", "green", "blue"];

for (var color of colors) {
  console.log(color);
}
```

`for...in` restituisce i nomi delle proprietà enumerabili, mentre `for...of` restituisce i valori di un iterabile. Per gli array è quasi sempre preferibile `for...of`, perché `for...in` può includere proprietà aggiunte all'oggetto e restituisce indici come stringhe.

In questo esempio, il ciclo `for...of` itera su tutti gli elementi dell'array `colors` e stampa ciascun elemento.

## Interrompere un ciclo

È possibile interrompere un ciclo in JavaScript utilizzando l'istruzione `break`. Ecco un esempio di utilizzo dell'istruzione `break` in un ciclo `for`:

```javascript
for (var i = 0; i < 5; i++) {
  if (i === 3) {
    break;
  }
  console.log(i);
}
```

In questo esempio, il ciclo `for` viene interrotto quando la variabile `i` è uguale a 3.

## Saltare un'iterazione

È possibile saltare un'iterazione in un ciclo in JavaScript utilizzando l'istruzione `continue`. Ecco un esempio di utilizzo dell'istruzione `continue` in un ciclo `for`:

```javascript
for (var i = 0; i < 5; i++) {
  if (i === 3) {
    continue;
  }
  console.log(i);
}
```

In questo esempio, l'iterazione corrente viene saltata quando la variabile `i` è uguale a 3.

`break` interrompe il ciclo più vicino, mentre `continue` salta alla successiva iterazione. Sono utili per casi di uscita o filtro, ma troppe diramazioni possono rendere più chiaro estrarre il corpo in una funzione.

### Etichette di ciclo

È possibile utilizzare le etichette di ciclo in JavaScript per identificare un ciclo specifico. Ecco un esempio di utilizzo delle etichette di ciclo in JavaScript:

```javascript
outerloop:
for (var i = 0; i < 3; i++) {
  innerloop:
  for (var j = 0; j < 3; j++) {
    if (i === 1 && j === 1) {
      break outerloop;
    }
    console.log(i, j);
  }
}
```

In questo esempio, l'etichetta `outerloop` viene utilizzata per identificare il ciclo esterno, e l'etichetta `innerloop` viene utilizzata per identificare il ciclo interno. Quando la variabile `i` è uguale a 1 e la variabile `j` è uguale a 1, il ciclo esterno viene interrotto utilizzando l'etichetta `outerloop`.

## Cicli annidati

È possibile annidare cicli all'interno di altri cicli in JavaScript. Ecco un esempio di utilizzo di cicli annidati in JavaScript:

```javascript
for (var i = 0; i < 3; i++) {
  for (var j = 0; j < 3; j++) {
    console.log(i, j);
  }
}
```

In questo esempio, il ciclo esterno viene eseguito tre volte, e per ogni iterazione del ciclo esterno, il ciclo interno viene eseguito tre volte.

### Conclusioni

In questo tutorial, abbiamo imparato a utilizzare i cicli `while`, `do...while` e `for` in JavaScript. Abbiamo anche esaminato come interrompere un ciclo utilizzando l'istruzione `break` e come saltare un'iterazione utilizzando l'istruzione `continue`.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione12)
