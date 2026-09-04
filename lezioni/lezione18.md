# Destructuring

Il **destructuring** è una sintassi JavaScript che permette di estrarre valori da oggetti e array e assegnarli a variabili. È utile quando una funzione restituisce più informazioni o quando vogliamo usare solo alcune proprietà di una struttura dati.

Il destructuring non modifica l'oggetto o l'array originale: legge i valori e li assegna alle variabili indicate.

## Destructuring degli oggetti

Per estrarre proprietà da un oggetto si usano le parentesi graffe a sinistra dell'assegnazione:

```javascript
const persona = {
    nome: "Ada",
    eta: 36,
    professione: "Programmatrice"
};

const { nome, eta } = persona;

console.log(nome); // Ada
console.log(eta);  // 36
```

Il nome della variabile deve corrispondere al nome della proprietà. L'ordine delle proprietà non è importante:

```javascript
const { professione, nome } = persona;

console.log(professione); // Programmatrice
console.log(nome);        // Ada
```

Se la proprietà non esiste, la variabile riceve il valore `undefined`.

```javascript
const { email } = persona;
console.log(email); // undefined
```

## Rinominare le variabili

Con la sintassi `proprieta: nuovaVariabile` è possibile usare un nome locale diverso da quello della proprietà:

```javascript
const { nome: nomeCompleto, eta: anni } = persona;

console.log(nomeCompleto); // Ada
console.log(anni);         // 36
```

In questo caso non vengono create le variabili `nome` ed `eta`, ma soltanto `nomeCompleto` e `anni`. I due punti non indicano un valore, ma una rinomina.

## Valori predefiniti

È possibile fornire un valore predefinito per una proprietà assente o `undefined`:

```javascript
const { colore = "blu", eta = 18 } = persona;

console.log(colore); // blu
console.log(eta);    // 36
```

Il valore predefinito viene usato solo quando il valore è `undefined`, non quando è `null`:

```javascript
const dati = { valore: null };
const { valore = 10 } = dati;

console.log(valore); // null
```

Per fornire contemporaneamente un nome diverso e un valore predefinito si combinano le due sintassi:

```javascript
const { nome: nomeUtente = "Anonimo" } = {};
console.log(nomeUtente); // Anonimo
```

## Destructuring degli array

Per gli array i valori vengono estratti in base alla posizione:

```javascript
const colori = ["rosso", "verde", "blu"];
const [primo, secondo, terzo] = colori;

console.log(primo);  // rosso
console.log(secondo); // verde
console.log(terzo);  // blu
```

A differenza degli oggetti, qui l'ordine è fondamentale. È possibile saltare un elemento lasciando una posizione vuota:

```javascript
const coordinate = [10, 20, 30];
const [x, , z] = coordinate;

console.log(x); // 10
console.log(z); // 30
```

Anche negli array si possono usare valori predefiniti:

```javascript
const [larghezza = 100, altezza = 50] = [];

console.log(larghezza); // 100
console.log(altezza);   // 50
```

## Operatore rest

L'operatore rest `...` raccoglie gli elementi non ancora assegnati in un nuovo array:

```javascript
const numeri = [1, 2, 3, 4, 5];
const [primo, secondo, ...altri] = numeri;

console.log(primo);  // 1
console.log(secondo); // 2
console.log(altri);  // [3, 4, 5]
```

Il rest deve essere l'ultimo elemento del pattern. Non è possibile scrivere altri elementi dopo `...altri`.

Con gli oggetti il rest raccoglie le proprietà che non sono state estratte:

```javascript
const prodotto = {
    nome: "Tastiera",
    prezzo: 49,
    categoria: "Accessori",
    disponibile: true
};

const { nome, ...dettagli } = prodotto;

console.log(nome);     // Tastiera
console.log(dettagli); // { prezzo: 49, categoria: "Accessori", disponibile: true }
```

Il rest crea una copia superficiale delle proprietà raccolte. Gli oggetti annidati, se presenti, restano condivisi con l'originale.

## Scambiare due variabili

Il destructuring permette di scambiare due valori senza una variabile temporanea:

```javascript
let a = 1;
let b = 2;

[a, b] = [b, a];

console.log(a); // 2
console.log(b); // 1
```

Quando si usa il destructuring per assegnare variabili già dichiarate, le parentesi tonde possono essere necessarie per evitare che `{}` venga interpretato come un blocco:

```javascript
let nome;
let eta;

({ nome, eta } = persona);
```

## Destructuring nei parametri

Una funzione può destrutturare direttamente l'oggetto ricevuto come parametro:

```javascript
function descriviPersona({ nome, eta, professione = "Non specificata" }) {
    return `${nome}, ${eta} anni, ${professione}`;
}

console.log(descriviPersona(persona));
```

Questa forma rende visibili subito i dati usati dalla funzione. Per evitare un errore quando il parametro è omesso, si può assegnare un oggetto vuoto come valore predefinito:

```javascript
function saluta({ nome = "ospite" } = {}) {
    return `Ciao, ${nome}!`;
}

console.log(saluta()); // Ciao, ospite!
```

Il destructuring funziona anche con i parametri array:

```javascript
function primoElemento([primo] = []) {
    return primo;
}

console.log(primoElemento(["JavaScript", "HTML"])); // JavaScript
```

## Destructuring annidato

È possibile estrarre proprietà contenute in oggetti o array annidati:

```javascript
const ordine = {
    id: 42,
    cliente: {
        nome: "Ada",
        indirizzo: {
            citta: "Roma"
        }
    }
};

const {
    cliente: {
        nome,
        indirizzo: { citta }
    }
} = ordine;

console.log(nome);  // Ada
console.log(citta); // Roma
```

Il pattern annidato può diventare difficile da leggere e può generare un errore se un livello intermedio è `null` o `undefined`. In questi casi è spesso preferibile usare l'operatore `?.` oppure normalizzare i dati prima del destructuring.

## Rest e spread: sintassi simile, scopo diverso

La stessa sintassi `...` viene chiamata **rest** quando raccoglie più valori e **spread** quando espande valori:

```javascript
const originali = [1, 2, 3];
const copia = [...originali]; // spread: espande gli elementi

function somma(...numeri) {  // rest: raccoglie gli argomenti
    return numeri.reduce((totale, numero) => totale + numero, 0);
}

console.log(somma(...originali)); // spread nella chiamata: 6
```

Lo spread di un oggetto crea una copia superficiale e le proprietà successive possono sovrascrivere quelle precedenti:

```javascript
const impostazioni = { tema: "chiaro", lingua: "it" };
const personalizzate = { ...impostazioni, tema: "scuro" };

console.log(personalizzate); // { tema: "scuro", lingua: "it" }
```

## Errori comuni

### Destrutturare `null` o `undefined`

```javascript
const valore = null;
// const { nome } = valore; // TypeError
```

Un valore predefinito per l'oggetto risolve il caso `undefined`, ma non `null`:

```javascript
function leggiNome(utente = {}) {
    const { nome = "Anonimo" } = utente;
    return nome;
}

console.log(leggiNome()); // Anonimo
```

Se può arrivare `null`, va gestito prima, per esempio con `utente ?? {}`.

### Confondere proprietà e variabili

```javascript
const account = { nome: "Ada" };
const { nome: visualizzato } = account;

// console.log(nome);       // ReferenceError
console.log(visualizzato);  // Ada
```

### Usare troppo destructuring

Il destructuring è utile quando riduce il rumore, ma un pattern molto annidato o con molti alias può nascondere la forma dei dati. In quel caso estrarre pochi valori alla volta o mantenere il riferimento all'oggetto può rendere il codice più comprensibile.

## Riepilogo

- Il destructuring degli oggetti usa i nomi delle proprietà.
- Il destructuring degli array usa le posizioni.
- `=` assegna valori predefiniti quando il valore è `undefined`.
- `...` raccoglie valori nel rest o li espande con lo spread.
- Il destructuring nei parametri rende chiari i dati usati da una funzione.
- Oggetti e array destrutturati non vengono modificati automaticamente.
- Il destructuring annidato richiede attenzione ai livelli mancanti.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione17) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione19)
