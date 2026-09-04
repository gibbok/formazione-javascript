# Sintassi di Javascript

## Sintassi di base

La sintassi di JavaScript è simile a quella di altri linguaggi di programmazione, come Java, C e C++. JavaScript è un linguaggio di programmazione basato su testo, il che significa che i programmi JavaScript sono costituiti da parole, numeri e simboli. I programmi JavaScript sono costituiti da istruzioni, che sono comandi che vengono eseguiti dal computer.

Ecco un esempio di programma JavaScript:

```javascript
// Dichiarare una variabile
var nome = "Mario";

// Visualizzare un messaggio di saluto
console.log("Ciao, " + nome + "!");
```

In questo esempio, il programma JavaScript dichiara una variabile chiamata `nome` e le assegna il valore `"Mario"`. Successivamente, il programma visualizza un messaggio di saluto che include il valore della variabile `nome`.

## Commenti

I commenti sono porzioni di codice che vengono ignorate dal computer quando esegue un programma. I commenti sono utili per documentare il codice e per rendere più facile la comprensione del codice da parte di altre persone.

In JavaScript, i commenti possono essere inseriti all'interno del codice utilizzando due barre oblique `//` per i commenti su una sola riga e `/* */` per i commenti su più righe.

Ecco un esempio di commenti in JavaScript:

```javascript
// Questo è un commento su una sola riga

/*
  Questo è un commento
  su più righe
*/
```

## Punti e virgola

In JavaScript, i punti e virgola `;` vengono utilizzati per separare le istruzioni. Anche se i punti e virgola non sono obbligatori in JavaScript, è una buona pratica includerli per evitare errori di sintassi.

Ecco un esempio di utilizzo dei punti e virgola in JavaScript:

```javascript
// Visualizzare un messaggio di saluto
console.log("Ciao mondo!");
```

JavaScript applica l'**inserimento automatico dei punti e virgola** (Automatic Semicolon Insertion), ma affidarsi sempre a questo comportamento può rendere ambigui alcuni casi, soprattutto quando una riga inizia con `(`, `[`, `` ` `` o un operatore. Scegli una convenzione coerente: usare i punti e virgola esplicitamente è una scelta chiara per chi sta imparando.

## Case sensitivity

JavaScript è case-sensitive, il che significa che fa distinzione tra maiuscole e minuscole. Ad esempio, le variabili `nome`, `Nome` e `NOME` sono considerate variabili diverse in JavaScript.

Ecco un esempio di case sensitivity in JavaScript:

```javascript
var nome = "Mario";
var Nome = "Luigi";
var NOME = "Peach";

console.log(nome); // Output: Mario
console.log(Nome); // Output: Luigi
console.log(NOME); // Output: Peach
```

## Identificatori

Gli identificatori sono nomi utilizzati per identificare variabili, funzioni, classi e altri elementi del codice. Gli identificatori in JavaScript devono iniziare con una lettera, un carattere di sottolineatura `_` o un simbolo di dollaro `$`. I caratteri successivi possono essere lettere, numeri, caratteri di sottolineatura o simboli di dollaro.

Ecco alcuni esempi di identificatori validi in JavaScript:

```javascript
var nome;
var _eta;
var $cognome;
var NomeCompleto;
var numero1;
var _2numero;
var $numero3;
```

## Parole chiave

Le parole chiave sono riservate per l'uso nel linguaggio di programmazione e non possono essere utilizzate come identificatori. Alcune parole chiave comuni in JavaScript includono `var`, `function`, `if`, `else`, `for`, `while`, `return`, `true`, `false`, `null`, `undefined`, `this`, `new`, `class`, `extends`, `super`, `import`, `export`, `default`, `async`, `await`, `let`, `const`, `break`, `continue`, `switch`, `case`, `default`, `try`, `catch`, `throw`, `finally`, `delete`, `typeof`, `instanceof`, `in`, `with`, `void`, `yield`, `arguments`, `eval`, `debugger`.

Ecco un esempio di utilizzo di parole chiave in JavaScript:

```javascript
var nome = "Mario";
var eta = 30;

function saluta() {
  return "Ciao, " + nome + "!";
}

if (eta >= 18) {
    console.log(saluta());
}
```

## Blocchi e indentazione

Le parentesi graffe definiscono un blocco. Il blocco è importante perché determina dove valgono le istruzioni condizionali e, con `let` e `const`, anche la visibilità delle variabili.

```javascript
const eta = 20;

if (eta >= 18) {
  const messaggio = "Accesso consentito";
  console.log(messaggio);
}

// console.log(messaggio); // ReferenceError: fuori dal blocco
```

L'indentazione non cambia il significato del programma, ma rende visibile la struttura. Un nome descrittivo e un blocco breve sono generalmente più utili di un commento che ripete la stessa istruzione.

## Espressioni e istruzioni

Un'espressione produce un valore, per esempio `2 + 2` o `nome.toUpperCase()`. Un'istruzione esegue un'azione, come una dichiarazione `const`, un `if` o un `return`. Riconoscere questa differenza aiuta a capire perché alcune funzioni restituiscono un valore e altre producono soltanto un effetto.

### Conclusioni

In questa lezione abbiamo visto la sintassi di base di JavaScript, inclusi commenti, punti e virgola, case sensitivity, identificatori e parole chiave. Questi concetti sono fondamentali per la comprensione e la scrittura di programmi JavaScript. Nelle prossime lezioni esploreremo ulteriori concetti e funzionalità di JavaScript.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione3)
