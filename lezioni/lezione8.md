# Operatori di base

Gli operatori sono simboli speciali che vengono utilizzati per eseguire operazioni su valori e variabili. In JavaScript, ci sono diversi tipi di operatori, tra cui operatori aritmetici, operatori di confronto, operatori logici e altri.

## Termini "unario", "binario" e "ternario

Gli operatori possono essere classificati in base al numero di operandi che accettano:

- **Unario**: un operatore unario accetta un singolo operando. Ad esempio, l'operatore di negazione `-` è un operatore unario che nega il suo operando.
- **Binario**: un operatore binario accetta due operandi. Ad esempio, l'operatore di addizione `+` è un operatore binario che somma i suoi due operandi.
- **Ternario**: un operatore ternario accetta tre operandi. In JavaScript, l'operatore condizionale `? :` è un operatore ternario che valuta una condizione e restituisce un valore in base al risultato della valutazione.

## Operatori aritmetici

Sono supportati seguenti operatori matematici:

- `+` (addizione)
- `-` (sottrazione)
- `*` (moltiplicazione)
- `/` (divisione)
- `%` (modulo)
- `++` (incremento)
- `--` (decremento)

Ecco alcuni esempi di utilizzo degli operatori aritmetici in JavaScript:

```javascript
var x = 10;
var y = 5;

// Addizione
var somma = x + y; // 15

// Sottrazione
var differenza = x - y; // 5

// Moltiplicazione
var prodotto = x * y; // 50

// Divisione
var quoziente = x / y; // 2

// Modulo
var resto = x % y; // 0

// Incremento
x++; // x = 11

// Decremento
y--; // y = 4
```

L'operatore `%` restituisce il resto della divisione, non una percentuale. Per sapere se un intero è pari si può usare `numero % 2 === 0`. Sono disponibili anche `**` per l'elevamento a potenza e gli operatori di assegnazione composta:

```javascript
let totale = 10;
totale += 5; // totale = totale + 5
totale *= 2; // totale = totale * 2
const area = 3 ** 2; // 9
```

Gli operatori `++` e `--` possono essere prefissi o postfissi. In espressioni complesse è più leggibile incrementare una variabile con un'istruzione separata.

## Precedenza degli operatori

Gli operatori aritmetici seguono una precedenza specifica, che determina l'ordine in cui vengono eseguite le operazioni. Ad esempio, la moltiplicazione ha una precedenza maggiore rispetto all'addizione, quindi le operazioni di moltiplicazione vengono eseguite prima delle operazioni di addizione.

Ecco un esempio di utilizzo della precedenza degli operatori in JavaScript:

```javascript
var x = 10;

var risultato = 2 * (3 + x); // 26
```

In questo esempio, l'operazione di addizione `3 + x` viene eseguita prima, quindi il risultato viene moltiplicato per `2`.

Le parentesi rendono esplicito l'intento e riducono gli errori. Se il calcolo diventa lungo, è preferibile dividerlo in variabili con nomi significativi invece di affidarsi alla sola precedenza.

### Conclusione

Gli operatori aritmetici sono utilizzati per eseguire operazioni matematiche su valori e variabili in JavaScript. È importante essere consapevoli della precedenza degli operatori e di come influisce sul comportamento del codice.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione9)
