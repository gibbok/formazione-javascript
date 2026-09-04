# Operatori condizionali

Gli operatori condizionali vengono utilizzati per eseguire un blocco di codice se una condizione specificata è vera, altrimenti eseguire un altro blocco di codice.

## L'istruzione if

L'istruzione `if` è utilizzata per eseguire un blocco di codice se una condizione specificata è vera. Ecco un esempio di utilizzo dell'istruzione `if` in JavaScript:

```javascript
var x = 10;

if (x > 5) {
  console.log("x è maggiore di 5");
}
```

In questo esempio, l'istruzione `if` valuta la condizione `x > 5` e, se la condizione è vera, esegue il blocco di codice all'interno delle parentesi graffe.

La condizione viene convertita in booleano. È buona pratica usare sempre le parentesi graffe, anche quando il blocco contiene una sola istruzione, e scrivere condizioni che esprimano chiaramente l'intento.

## L'istruzione if...else

L'istruzione `if...else` è utilizzata per eseguire un blocco di codice se una condizione specificata è vera e un altro blocco di codice se la condizione è falsa. Ecco un esempio di utilizzo dell'istruzione `if...else` in JavaScript:

```javascript
var x = 10;

if (x > 5) {
  console.log("x è maggiore di 5");
} else {
  console.log("x non è maggiore di 5");
}
```

In questo esempio, l'istruzione `if` valuta la condizione `x > 5` e, se la condizione è vera, esegue il primo blocco di codice. Altrimenti, esegue il secondo blocco di codice.

## L'istruzione if...else if...else

L'istruzione `if...else if...else` è utilizzata per eseguire un blocco di codice se una condizione specificata è vera, un altro blocco di codice se un'altra condizione specificata è vera e un altro blocco di codice se nessuna delle condizioni specificate è vera. Ecco un esempio di utilizzo dell'istruzione `if...else if...else` in JavaScript:

```javascript
var x = 10;

if (x > 10) {
  console.log("x è maggiore di 10");
} else if (x < 10) {
  console.log("x è minore di 10");
} else {
  console.log("x è uguale a 10");
}
```

In questo esempio, l'istruzione `if` valuta la prima condizione `x > 10` e, se la condizione è vera, esegue il primo blocco di codice. Altrimenti, valuta la seconda condizione `x < 10` e, se la condizione è vera, esegue il secondo blocco di codice. Altrimenti, esegue il terzo blocco di codice.

## L'operatore condizionale `?` o 'ternario'

L'operatore condizionale `?` è un operatore ternario che valuta una condizione e restituisce un valore in base al risultato della valutazione. Ecco un esempio di utilizzo dell'operatore condizionale `?` in JavaScript:

```javascript
var x = 10;
var risultato = (x > 5) ? "x è maggiore di 5" : "x non è maggiore di 5";
console.log(risultato); // "x è maggiore di 5"
```

In questo esempio, l'operatore condizionale `?` valuta la condizione `x > 5` e restituisce il primo valore se la condizione è vera, altrimenti restituisce il secondo valore.

## Nullish coalescing operator `??`

L'operatore di coalescenza nullish `??` è un operatore binario che restituisce il suo secondo operando quando il primo operando è `null` o `undefined`, altrimenti restituisce il suo primo operando. Ecco un esempio di utilizzo dell'operatore di coalescenza nullish `??` in JavaScript:

```javascript
var x = null;
var y = 10;
var risultato = x ?? y;
console.log(risultato); // 10
```

In questo esempio, l'operatore di coalescenza nullish `??` restituisce il valore di `y` perché il valore di `x` è `null`.

## Confronti con `||`

L'operatore `||` può essere utilizzato per eseguire un confronto tra due valori. Se il primo valore è considerato "falso" (ad esempio `null`, `undefined`, `0`, `false`, `NaN`, `""`), allora viene restituito il secondo valore. Altrimenti, viene restituito il primo valore. Ecco un esempio di utilizzo dell'operatore `||` in JavaScript:

```javascript
var x = null;
var y = 10;
var risultato = x || y;
console.log(risultato); // 10
```

In questo esempio, l'operatore `||` restituisce il valore di `y` perché il valore di `x` è `null`.

## Confronti con `&&`

L'operatore `&&` può essere utilizzato per eseguire un confronto tra due valori. Se il primo valore è considerato "falso" (ad esempio `null`, `undefined`, `0`, `false`, `NaN`, `""`), allora viene restituito il primo valore. Altrimenti, viene restituito il secondo valore. Ecco un esempio di utilizzo dell'operatore `&&` in JavaScript:

```javascript
var x = null;
var y = 10;
var risultato = x && y;
console.log(risultato); // null
```

In questo esempio, l'operatore `&&` restituisce il valore di `x` perché il valore di `x` è `null`.

`&&` e `||` usano il corto circuito: il secondo operando viene valutato solo se necessario e il risultato può essere uno degli operandi, non necessariamente un booleano. Questo permette di fornire valori predefiniti, ma va distinto da `??`.

## Confronti con `!!`

L'operatore `!!` può essere utilizzato per convertire un valore in un valore booleano. Se il valore è considerato "falso" (ad esempio `null`, `undefined`, `0`, `false`, `NaN`, `""`), allora viene restituito `false`. Altrimenti, viene restituito `true`. Ecco un esempio di utilizzo dell'operatore `!!` in JavaScript:

```javascript
var x = null;
var risultato = !!x;
console.log(risultato); // false
```

In questo esempio, l'operatore `!!` restituisce `false` perché il valore di `x` è `null`.

## Confronti con `??=`

L'operatore `??=` può essere utilizzato per assegnare un valore a una variabile solo se la variabile è `null` o `undefined`. Ecco un esempio di utilizzo dell'operatore `??=` in JavaScript:

```javascript
var x = null;
x ??= 10;
console.log(x); // 10
```

In questo esempio, l'operatore `??=` assegna il valore di `10` a `x` perché il valore di `x` è `null`.

`??` conserva valori validi ma falsy come `0`, `false` e `""`, mentre `||` li sostituisce:

```javascript
const quantita = 0;
console.log(quantita || 10); // 10
console.log(quantita ?? 10); // 0
```

`??` non può essere mescolato direttamente con `&&` o `||` senza parentesi. L'operatore ternario è adatto a scegliere un valore; per più istruzioni è più chiaro usare `if...else`.

### Conclusione

Gli operatori condizionali sono utilizzati per eseguire un blocco di codice in base al risultato di una condizione specificata. È importante essere consapevoli di come utilizzare correttamente gli operatori condizionali in JavaScript per scrivere codice pulito e leggibile.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione11)
