# Operatori di confronto

Gli operatori di confronto vengono utilizzati per confrontare due valori e restituire un valore booleano che indica se il confronto è vero o falso. In JavaScript, ci sono diversi tipi di operatori di confronto, tra cui operatori di uguaglianza, operatori di disuguaglianza, operatori di maggiore e minore e altri.

## Operatori di uguaglianza

Gli operatori di uguaglianza vengono utilizzati per confrontare due valori e restituire `true` se i valori sono uguali, `false` altrimenti. In JavaScript, ci sono due tipi di operatori di uguaglianza:

- `==`: uguaglianza non stretta
- `===`: uguaglianza stretta

L'operatore `==` confronta due valori per l'uguaglianza, ma esegue la conversione di tipo se i valori non sono dello stesso tipo. Ad esempio:

```javascript
var x = 10;
var y = "10";

console.log(x == y); // true
```

L'operatore `===` confronta due valori per l'uguaglianza senza eseguire la conversione di tipo. Ad esempio:

```javascript
var x = 10;
var y = "10";

console.log(x === y); // false
```

## Operatori di disuguaglianza

Gli operatori di disuguaglianza vengono utilizzati per confrontare due valori e restituire `true` se i valori non sono uguali, `false` altrimenti. In JavaScript, ci sono due tipi di operatori di disuguaglianza:

- `!=`: disuguaglianza non stretta
- `!==`: disuguaglianza stretta

L'operatore `!=` confronta due valori per la disuguaglianza, ma esegue la conversione di tipo se i valori non sono dello stesso tipo. Ad esempio:

```javascript
var x = 10;
var y = "10";

console.log(x != y); // false
```

L'operatore `!==` confronta due valori per la disuguaglianza senza eseguire la conversione di tipo. Ad esempio:

```javascript
var x = 10;
var y = "10";

console.log(x !== y); // true
```

## Operatori di maggiore e minore

Gli operatori di maggiore e minore vengono utilizzati per confrontare due valori e restituire `true` se il primo valore è maggiore o minore del secondo valore, `false` altrimenti. In JavaScript, ci sono quattro tipi di operatori di maggiore e minore:

- `>`: maggiore di
- `<`: minore di
- `>=`: maggiore o uguale a
- `<=`: minore o uguale a

Ad esempio:

```javascript
var x = 10;
var y = 5;

console.log(x > y); // true
console.log(x < y); // false
console.log(x >= y); // true
console.log(x <= y); // false
```

## Operatori di confronto logico

Gli operatori di confronto vengono utilizzati per confrontare due valori e restituire `true` se il confronto è vero, `false` altrimenti. In JavaScript, ci sono due tipi di operatori di confronto:

- `&&`: AND logico
- `||`: OR logico

L'operatore `&&` restituisce `true` se entrambi i confronti sono veri, `false` altrimenti. Ad esempio:

```javascript
var x = 10;
var y = 5;

console.log(x > 5 && y < 10); // true
console.log(x > 5 && y > 10); // false
```

L'operatore `||` restituisce `true` se almeno uno dei confronti è vero, `false` altrimenti. Ad esempio:

```javascript
var x = 10;
var y = 5;

console.log(x > 5 || y < 10); // true
console.log(x < 5 || y > 10); // false
```

In generale, gli operatori di confronto sono utilizzati per eseguire confronti tra valori e variabili e per prendere decisioni in base ai risultati dei confronti.

## Quale uguaglianza scegliere?

Nel codice applicativo è normalmente preferibile `===` e `!==`, perché non introducono conversioni nascoste. Il confronto `valore == null` è un idioma specifico per accettare sia `null` sia `undefined`, ma va usato consapevolmente.

I confronti tra oggetti verificano il riferimento, non il contenuto:

```javascript
const primo = { id: 1 };
const secondo = { id: 1 };

console.log(primo === secondo); // false
console.log(primo === primo);   // true
```

## Operatori di confronto con null e undefined

In JavaScript, ci sono due tipi di operatori di confronto specifici per i valori `null` e `undefined`:

- `==` e `===` restituiscono `true` solo se il valore è `null` o `undefined`
- `!=` e `!==` restituiscono `true` solo se il valore non è `null` o `undefined`

Ad esempio:

```javascript
var x = null;
var y;

console.log(x == null); // true
console.log(x === null); // true
console.log(y == null); // true
console.log(y === null); // false
console.log(x != null); // false
console.log(x !== null); // false
console.log(y != null); // true
console.log(y !== null); // true
```

Se entrambi gli operandi sono stringhe, `>` e `<` confrontano la sequenza dei caratteri; in altri casi JavaScript prova una conversione numerica. Per evitare sorprese, normalizzare prima i dati e poi confrontarli.

In generale, gli operatori di confronto con `null` e `undefined` sono utilizzati per verificare se una variabile è stata assegnata a un valore o meno.

### Conclusione

In questo articolo abbiamo esaminato gli operatori di confronto in JavaScript e come possono essere utilizzati per confrontare valori e variabili. Abbiamo esaminato anche la differenza tra gli operatori di uguaglianza non stretta e stretta, gli operatori di disuguaglianza non stretta e stretta, gli operatori di maggiore e minore, e gli operatori di confronto logico. Infine, abbiamo esaminato gli operatori di confronto specifici per i valori `null` e `undefined`. Gli operatori di confronto sono uno strumento fondamentale per eseguire confronti e prendere decisioni in JavaScript.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione10)
