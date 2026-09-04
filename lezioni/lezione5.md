# Variabili e tipi di dati

Le variabili sono uno degli elementi fondamentali del linguaggio di programmazione JavaScript. Le variabili sono utilizzate per memorizzare e manipolare i dati all'interno di un programma JavaScript. In questo articolo, esamineremo come dichiarare e utilizzare variabili in JavaScript.

## Dichiarazione di variabili

In JavaScript, le variabili vengono dichiarate utilizzando la parola chiave `var`, seguita da un nome di variabile. Ad esempio:

```javascript
var nome;
```

In questo esempio, la variabile `nome` viene dichiarata utilizzando la parola chiave `var`.

## Assegnazione di valori alle variabili

Dopo aver dichiarato una variabile, è possibile assegnare un valore alla variabile utilizzando l'operatore di assegnazione `=`. Ad esempio:

```javascript
var nome;
nome = "Mario";
```

In questo esempio, la variabile `nome` viene assegnata con il valore `"Mario"`.

È anche possibile dichiarare e assegnare una variabile in una singola istruzione. Ad esempio:

```javascript
var nome = "Mario";
```

In questo esempio, la variabile `nome` viene dichiarata e assegnata con il valore `"Mario"` in una singola istruzione.

## Parola chiave const e let

Oltre alla parola chiave `var`, JavaScript supporta anche le parole chiave `const` e `let` per dichiarare variabili. La parola chiave `const` viene utilizzata per dichiarare variabili con valori costanti, che non possono essere modificati dopo essere stati assegnati. La parola chiave `let` viene utilizzata per dichiarare variabili con ambito di blocco, che possono essere modificate all'interno del blocco in cui sono dichiarate.

Ad esempio:

```javascript
const PI = 3.14;
let x = 10;
```

`const` impedisce la riassegnazione del riferimento, ma non rende immutabile un oggetto o un array:

```javascript
const utente = { nome: "Ada" };
utente.nome = "Grace"; // consentito: cambia una proprietà
// utente = {};         // TypeError: il riferimento non può cambiare
```

`let` e `const` hanno scope di blocco e non possono essere usati prima della dichiarazione. `var` ha invece scope di funzione e un comportamento di hoisting più difficile da prevedere; nel codice moderno è generalmente preferibile usare `let` o `const`.

In questo esempio, la variabile `PI` viene dichiarata con la parola chiave `const` e la variabile `x` viene dichiarata con la parola chiave `let`.

### Le costanti maiuscole

Una pratica molto diffusa è di utilizzare le variabili costanti come alias di valori difficili da ricordare, e che sono noti prima dell’esecuzione.

Questo tipo di costanti vengono identificate con lettere maiuscole e underscore.

Come in questo esempio, creiamo delle costanti nel cosidetto formato “web” (esadecimale):

```javascript
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...quando abbiamo bisogno di prelevare un colore
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Benefici:

- `COLOR_ORANGE` è più facile da ricordare di `#FF7F00`.
- E’ più facile commettere errori scrivendo `#FF7F00` piuttosto che COLOR_ORANGE.
- Quando leggiamo il codice, COLOR_ORANGE è molto più significativo di `#FF7F00`.

## Convenzioni di denominazione delle variabili

Nel linguaggio di programmazione JavaScript, le variabili possono essere denominate utilizzando lettere, numeri, underscore e dollari. Tuttavia, ci sono alcune convenzioni di denominazione che è consigliabile seguire per rendere il codice più leggibile e comprensibile.

Alcune delle convenzioni di denominazione più comuni per le variabili in JavaScript includono:

- Utilizzare nomi di variabili significativi e descrittivi.
- Utilizzare la notazione camelCase per i nomi di variabili composti da più parole. Ad esempio: `nomeUtente`, `dataDiNascita`.
- Evitare nomi di variabili generici o ambigui. Ad esempio: `valore`, `dato`.
- Evitare nomi di variabili che iniziano con un numero. Ad esempio: `1valore`.
- Evitare nomi di variabili che sono parole chiave riservate in JavaScript. Ad esempio: `var`, `function`, `let`.

Ad esempio:

```javascript
var nomeUtente;
var dataDiNascita;
var numeroDiTelefono;
```

In questo esempio, vengono utilizzate convenzioni di denominazione significative e descrittive per le variabili.

## Tipi di dati delle variabili

In JavaScript, le variabili possono memorizzare diversi tipi di dati, tra cui:

- Numeri: ad esempio `10`, `3.14`, `-5`.
- Stringhe: ad esempio `"Ciao"`, `"Mondo"`, `"JavaScript"`.
- Booleani: ad esempio `true`, `false`.
- Oggetti: ad esempio `{nome: "Mario", cognome: "Rossi"}`.
- Array: ad esempio `["Mela", "Banana", "Arancia"]`.
- Null: ad esempio `null`.
- Undefined: ad esempio `undefined`.

Ad esempio:

```javascript
var numero = 10;
var nome = "Mario";
var isAttivo = true;
var persona = {nome: "Mario", cognome: "Rossi"};
var frutta = ["Mela", "Banana", "Arancia"];
var nullo = null;
var nonDefinito = undefined;
```

In questo esempio, vengono dichiarate variabili con diversi tipi di dati.

### Tipo Number

Il tipo number viene utilizzato sia per i numeri interi che per quelli in virgola mobile.

Con i valori di tipo number si hanno diverse operazioni a disposizione, ad esempio la moltiplicazione *, la divisione /, l’addizione +, la sottrazione - e molte altre.

Oltre a i normali valori numeri, esistono anche i “valori numerici speciali” che appartengono sempre al tipo numerico:

- `Infinity` rappresenta il concetto matematico Infinito ∞. E’ un valore speciale che è più grande di qualsiasi altro numero.
- `-Infinity` rappresenta il concetto matematico -Infinito -∞. E’ un valore speciale che è più piccolo di qualsiasi altro numero.
- `NaN` rappresenta un errore di calcolo. E’ il risultato di un’operazione non corretta o indefinita, ad esempio la divisione di 0 per 0.

Ad esempio:

```javascript
alert( 1 / 0 ); // Infinity
alert( Infinity ); // Infinity

alert( "non un numero" / 2 ); // NaN, such division is erroneous
```

I numeri JavaScript sono normalmente rappresentati in virgola mobile. Per questo alcuni decimali non sono rappresentabili esattamente:

```javascript
console.log(0.1 + 0.2); // 0.30000000000000004
console.log((0.1 + 0.2).toFixed(2)); // "0.30"
```

`toFixed()` restituisce una stringa. Per confrontare risultati calcolati è spesso meglio usare una tolleranza, mentre `Number.isNaN(valore)` verifica in modo esplicito la presenza di `NaN`.

### Tipo BigInt

Il tipo BigInt è stato introdotto nel 2020 per rappresentare numeri interi di lunghezza arbitraria.

Un numero BigInt è creato aggiungendo n alla fine di un numero:

```javascript
const bigInt = 1234567890123456789012345678901234567890n;
```

### Tipo String

Il tipo stringa è usato per rappresentare dati testuali: stringhe di testo.

Una stringa in JavaScript deve essere racchiusa tra apici singoli, doppi o backtick.

Ad esempio:

```javascript
let stringa = "Ciao";
let nome = 'Mario';
let frase = `Ciao, mi chiamo ${nome}`; // Ciao, mi chiamo Mario
```

Nota:

Non c’è il tipo carattere. Una stringa con un singolo carattere è ancora una stringa.

### Tipo Boolean

Il tipo booleano può avere solo due valori: `true` e `false`.

Questo tipo è comunemente usato per memorizzare valori di verità: `true` per vero, `false` per falso.

Ad esempio:

```javascript
let isGreater = 4 > 1;
alert( isGreater ); // true
```

### Tipo Null

Il tipo null ha un solo valore: `null`.

Viene utilizzato come “valore vuoto” o “valore sconosciuto”.

Ad esempio:

```javascript
let eta = null;
```

### Tipo Undefined

Il tipo undefined ha un solo valore: `undefined`.

Se una variabile è stata dichiarata, ma non assegnata, il suo valore è `undefined`.

Ad esempio:

```javascript
let eta;

alert(eta); // undefined
```

#### La differenza tra null e undefined

In JavaScript, `null` e `undefined` sono valori speciali che rappresentano l'assenza di un valore. Tuttavia, esistono alcune differenze importanti tra `null` e `undefined`.

- `null` è un valore primitivo che rappresenta l'assenza di un valore. Viene utilizzato per indicare che una variabile è stata dichiarata, ma non ha un valore assegnato.
- `undefined` è un valore primitivo che rappresenta una variabile che è stata dichiarata, ma non ha un valore assegnato. Viene utilizzato per indicare che una variabile non è stata inizializzata.

### Tipo Object

Il tipo oggetto è usato per i più complessi dati strutturati.

Un oggetto può essere creato con le parentesi graffe `{…}` con un elenco di coppie chiave: valore all’interno.

Ad esempio:

```javascript
let persona = {
  nome: "Mario",
  eta: 30
};

alert(persona.nome); // Mario
alert(persona.eta); // 30
```

### Tipo Symbol

Il tipo symbol è usato per creare identificatori univoci per gli oggetti.

Ad esempio:

```javascript
let id = Symbol("id");
```

### Tipo Function

Il tipo function è usato per memorizzare funzioni.

Le funzioni sono un tipo speciale di oggetto, che può essere chiamato.

Ad esempio:

```javascript
function saluta(nome) {
  alert( `Ciao, ${nome}` );
}
```

### Tipo Array

Il tipo array è usato per memorizzare una collezione ordinata di elementi.

Ad esempio:

```javascript
let frutta = ["Mela", "Banana", "Arancia"];
alert( frutta[0] ); // Mela

frutta[2] = "Pera"; // sostituire un elemento
alert( frutta ); // Mela, Banana, Pera
```

Gli array sono oggetti indicizzati a partire da zero e possiedono la proprietà `length`. Per verificare che un valore sia un array usare `Array.isArray(valore)`, perché `typeof []` restituisce `"object"`.

### L'operatore typeof

L'operatore `typeof` può essere utilizzato per determinare il tipo di dati di una variabile o di un'espressione. Ad esempio:

```javascript
var numero = 10;
var nome = "Mario";
var isAttivo = true;
var persona = {nome: "Mario", cognome: "Rossi"};
var frutta = ["Mela", "Banana", "Arancia"];
var nullo = null;
var nonDefinito = undefined;

console.log(typeof numero); // number
console.log(typeof nome); // string
console.log(typeof isAttivo); // boolean
console.log(typeof persona); // object
console.log(typeof frutta); // object
console.log(typeof nullo); // object
console.log(typeof nonDefinito); // undefined
console.log(typeof Math); // "object"
```

`typeof` è utile per controlli semplici, ma non distingue array, date e `null` dagli altri oggetti. Per i valori mancanti, `valore === undefined` è esplicito; per accettare sia `null` sia `undefined` si può usare intenzionalmente `valore == null`.

In questo esempio, l'operatore `typeof` viene utilizzato per determinare il tipo di dati di diverse variabili.

Nota:

- Math è un oggetto integrato che fornisce operazioni matematiche avanzate. Lo studieremo nel capitolo Numeri. Qui ha il semplice scopo di rappresentare un oggetto.
- Il risultato di typeof null è "object". Questo è un errore del linguaggio, ufficialmente riconosciuto e mantenuto per retro-compatibilità. Ovviamente, null non è un oggetto. E’ un valore speciale che fa da tipo a se stesso. Quindi, nuovamente, questo è un errore del linguaggio.
- Il risultato di typeof alert è "function", poiché alert è una funzione del linguaggio. Studieremo le funzioni nel prossimo capitolo, e vedremo che non c’e nessun tipo “funzione” nel linguaggio. Le funzioni appartengono al tipo oggetto. Ma typeof le tratta differentemente. Formalmente, è errato, ma molto utile nella pratica.

### Conclusione

In questo articolo, abbiamo esaminato come dichiarare e utilizzare variabili in JavaScript. Abbiamo esaminato la dichiarazione di variabili utilizzando le parole chiave `var`, `const` e `let`, l'assegnazione di valori alle variabili, le convenzioni di denominazione delle variabili, i tipi di dati delle variabili e l'operatore `typeof` per determinare il tipo di dati di una variabile o di un'espressione.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione6)
