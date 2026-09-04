# Conversione di tipi

In JavaScript, la conversione di tipi si verifica quando un valore di un tipo viene convertito in un altro tipo. Questo può accadere in diverse situazioni, ad esempio quando si utilizzano operatori o funzioni che richiedono un tipo di dato specifico, o quando si confrontano valori di tipi diversi.

JavaScript esegue la conversione di tipi in modo implicito e automatico in molte situazioni. Ad esempio, quando si utilizza l'operatore `+` per concatenare stringhe e numeri, JavaScript converte automaticamente i numeri in stringhe prima di eseguire la concatenazione.

Ecco alcuni esempi di conversione di tipi in JavaScript:

```javascript
// Conversione di numeri in stringhe
var numero = 123;
var stringa = numero + ""; // Conversione implicita in una stringa

// Conversione di stringhe in numeri
var stringa = "123";
var numero = +stringa; // Conversione implicita in un numero

// Conversione di stringhe in booleani
var stringa = "true";
var booleano = stringa === "true"; // Conversione implicita in un booleano
```

In alcuni casi, è possibile eseguire la conversione di tipi in modo esplicito utilizzando funzioni come `parseInt()` e `parseFloat()` per convertire stringhe in numeri, o `String()` per convertire numeri in stringhe.

Ecco alcuni esempi di conversione di tipi esplicita in JavaScript:

```javascript
// Conversione esplicita di stringhe in numeri
var stringa = "123";
var numero = parseInt(stringa); // Conversione esplicita in un numero

// Conversione esplicita di numeri in stringhe
var numero = 123;
var stringa = String(numero); // Conversione esplicita in una stringa
```

In generale, è importante essere consapevoli della conversione di tipi in JavaScript e di come può influenzare il comportamento del codice. La conversione di tipi può portare a comportamenti imprevisti e errori, quindi è importante prestare attenzione quando si lavora con valori di tipi diversi.

## Conversione implicita e input esterni

L'operatore `+` concatena se almeno un operando è una stringa:

```javascript
console.log(2 + 3);       // 5
console.log("2" + 3);     // "23"
console.log(2 + 3 + "4"); // "54"
```

Per dati provenienti da form o URL è meglio convertire esplicitamente vicino all'ingresso. `parseInt("42px", 10)` restituisce `42`, mentre `Number("42px")` restituisce `NaN`: il primo legge una parte iniziale, il secondo richiede che tutta la stringa sia numerica. `Number.isFinite()` permette di rifiutare anche gli infiniti.

## Conversione Number(), String() e Boolean()

In JavaScript, è possibile eseguire la conversione esplicita di valori in numeri, stringhe e booleani utilizzando le funzioni `Number()`, `String()` e `Boolean()`.

La funzione `Number()` può essere utilizzata per convertire un valore in un numero. Ad esempio:

```javascript
var stringa = "123";
var numero = Number(stringa); // Conversione esplicita in un numero
```

La funzione `String()` può essere utilizzata per convertire un valore in una stringa. Ad esempio:

```javascript
var numero = 123;
var stringa = String(numero); // Conversione esplicita in una stringa
```

La funzione `Boolean()` può essere utilizzata per convertire un valore in un booleano. Ad esempio:

```javascript
var stringa = "true";
var booleano = Boolean(stringa); // Conversione esplicita in un booleano
```

Queste funzioni possono essere utili quando è necessario eseguire la conversione esplicita di valori in JavaScript.

### Le regole di conversione numerica

In JavaScript, la conversione di valori in numeri segue alcune regole specifiche. Ad esempio, le stringhe che rappresentano numeri possono essere convertite in numeri, ma le stringhe che non rappresentano numeri restituiranno `NaN` (Not a Number).

Ecco alcuni esempi di conversione di stringhe in numeri in JavaScript:

```javascript
var stringa1 = "123";
var numero1 = Number(stringa1); // Conversione in un numero

var stringa2 = "abc";
var numero2 = Number(stringa2); // Conversione in NaN
```

Inoltre, i valori booleani possono essere convertiti in numeri, con `true` che viene convertito in `1` e `false` che viene convertito in `0`.

Ecco un esempio di conversione di valori booleani in numeri in JavaScript:

```javascript
var booleano1 = true;
var numero1 = Number(booleano1); // Conversione in 1

var booleano2 = false;
var numero2 = Number(booleano2); // Conversione in 0
```

È importante essere consapevoli di queste regole di conversione numerica quando si lavora con valori in JavaScript.

### Le regole di conversione di stringhe

In JavaScript, la conversione di valori in stringhe segue alcune regole specifiche. Ad esempio, i numeri possono essere convertiti in stringhe, ma i valori booleani vengono convertiti in "true" e "false".

Ecco alcuni esempi di conversione di numeri e booleani in stringhe in JavaScript:

```javascript
var numero = 123;
var stringa1 = String(numero); // Conversione in una stringa

var booleano = true;
var stringa2 = String(booleano); // Conversione in "true"
```

Inoltre, `null` e `undefined` vengono convertiti in "null" e "undefined", rispettivamente.

Ecco un esempio di conversione di `null` e `undefined` in stringhe in JavaScript:

```javascript
var valore1 = null;
var stringa1 = String(valore1); // Conversione in "null"

var valore2 = undefined;
var stringa2 = String(valore2); // Conversione in "undefined"
```

È importante essere consapevoli di queste regole di conversione di stringhe quando si lavora con valori in JavaScript.

### Le regole di conversione booleana

In JavaScript, la conversione di valori in booleani segue alcune regole specifiche. Ad esempio, i numeri diversi da zero e le stringhe non vuote vengono convertiti in `true`, mentre `0`, `NaN`, `null`, `undefined`, `""` (stringa vuota) vengono convertiti in `false`.

Ecco alcuni esempi di conversione di numeri e stringhe in booleani in JavaScript:

```javascript
var numero1 = 123;
var booleano1 = Boolean(numero1); // Conversione in true

var stringa1 = "abc";
var booleano2 = Boolean(stringa1); // Conversione in true

var numero2 = 0;
var booleano3 = Boolean(numero2); // Conversione in false

var stringa2 = "";
var booleano4 = Boolean(stringa2); // Conversione in false
```

Sono falsy anche `-0` e `0n`. Invece stringhe come `"false"`, `"0"` e `"null"` non sono vuote e diventano `true`, un dettaglio importante quando si validano input testuali.

È importante essere consapevoli di queste regole di conversione booleana quando si lavora con valori in JavaScript.

### Conclusione

In JavaScript, è possibile eseguire la conversione esplicita di valori in numeri, stringhe e booleani utilizzando le funzioni `Number()`, `String()` e `Boolean()`. È importante essere consapevoli delle regole di conversione numerica, di stringhe e booleana quando si lavora con valori in JavaScript.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione8)
