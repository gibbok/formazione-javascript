# Oggetti

Gli oggetti in Javascript sono strutture dati che consentono di raggruppare dati e funzionalità in un'unica entità. Gli oggetti sono costituiti da coppie chiave-valore, dove una chiave può essere una stringa o un `Symbol` e il valore può essere di qualsiasi tipo di dato. Le chiavi numeriche vengono convertite in stringhe.

## Creazione di un oggetto

Per creare un oggetto in Javascript, possiamo utilizzare la sintassi letterale `{}` o la parola chiave `new` seguita dal costruttore `Object()`.
Ad esempio:

```javascript
// Creazione di un oggetto con la sintassi letterale
let person = {
  name: 'John',
  age: 30,
};

// Creazione di un oggetto con la parola chiave new
let car = new Object();
car.make = 'Toyota';
car.model = 'Corolla';
```

In questo esempio, abbiamo creato due oggetti: `person` e `car`. L'oggetto `person` ha due proprietà `name` e `age`, mentre l'oggetto `car` ha due proprietà `make` e `model`.

## Accesso alle proprietà di un oggetto

Per accedere alle proprietà di un oggetto in Javascript, possiamo utilizzare la notazione a punto `.` o la notazione a parentesi quadre `[]`.

Ad esempio:

```javascript
let person = {
  name: 'John',
  age: 30,
};

console.log(person.name); // Output: John
console.log(person['age']); // Output: 30
```

In questo esempio, stiamo accedendo alle proprietà `name` e `age` dell'oggetto `person` utilizzando entrambe le notazioni.

## Modifica delle proprietà di un oggetto

Per modificare le proprietà di un oggetto in Javascript, possiamo semplicemente assegnare un nuovo valore alla proprietà.

Ad esempio:

```javascript
let person = {
  name: 'John',
  age: 30,
};

person.age = 35;

console.log(person.age); // Output: 35
```

In questo esempio, stiamo modificando la proprietà `age` dell'oggetto `person` da 30 a 35.

## Aggiunta di nuove proprietà a un oggetto

Per aggiungere nuove proprietà a un oggetto in Javascript, possiamo semplicemente assegnare un valore a una nuova chiave.

Ad esempio:

```javascript
let person = {
  name: 'John',
  age: 30,
};

person.city = 'New York';

console.log(person.city); // Output: New York
```

In questo esempio, stiamo aggiungendo una nuova proprietà `city` all'oggetto `person` con il valore `'New York'`.

## Eliminazione di proprietà di un oggetto

Per eliminare una proprietà da un oggetto in Javascript, possiamo utilizzare l'operatore `delete`.

Ad esempio:

```javascript
let person = {
  name: 'John',
  age: 30,
};

delete person.age;

console.log(person.age); // Output: undefined
```

In questo esempio, stiamo eliminando la proprietà `age` dall'oggetto `person`.

## Iterazione sulle proprietà di un oggetto

Per iterare sulle proprietà di un oggetto in Javascript, possiamo utilizzare il ciclo `for...in`.

Ad esempio:

```javascript
let person = {
  name: 'John',
  age: 30,
};

for (let key in person) {
  console.log(key + ': ' + person[key]);
}
```

In questo esempio, stiamo iterando sulle proprietà dell'oggetto `person` e stampando la chiave e il valore di ciascuna proprietà.

## Oggetti annidati

Gli oggetti in Javascript possono contenere altri oggetti come proprietà. Questo è noto come oggetti annidati.

Ad esempio:

```javascript
let person = {
  name: 'John',
  age: 30,
  address: {
    street: '123 Main St',
    city: 'New York',
    zip: '10001',
  },
};

console.log(person.address.city); // Output: New York
```

In questo esempio, l'oggetto `person` ha una proprietà `address` che è a sua volta un oggetto con le proprietà `street`, `city` e `zip`.

## Oggetti come parametri di funzioni

Gli oggetti in Javascript possono essere passati come parametri di funzioni.

Ad esempio:

```javascript
function printPerson(person) {
  console.log('Name: ' + person.name);
  console.log('Age: ' + person.age);
}

let person = {
  name: 'John',
  age: 30,
};

printPerson(person);
```

In questo esempio, stiamo definendo una funzione `printPerson` che accetta un oggetto `person` come parametro e stampa il nome e l'età della persona.

## Oggetti come valori di ritorno delle funzioni

Le funzioni in Javascript possono restituire oggetti come valori di ritorno.

Ad esempio:

```javascript
function createPerson(name, age) {
  return {
    name: name,
    age: age,
  };
}

let person = createPerson('John', 30);

console.log(person.name); // Output: John

console.log(person.age); // Output: 30
```

In questo esempio, stiamo definendo una funzione `createPerson` che restituisce un oggetto con le proprietà `name` e `age` in base ai parametri passati alla funzione.

## Oggetti come costruttori

In Javascript, possiamo utilizzare la parola chiave `function` per creare costruttori di oggetti. I costruttori di oggetti possono essere utilizzati per creare nuovi oggetti con le stesse proprietà e metodi.

Ad esempio:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

let person1 = new Person('John', 30);
let person2 = new Person('Jane', 25);

console.log(person1.name); // Output: John
console.log(person2.name); // Output: Jane
```

In questo esempio, stiamo definendo un costruttore di oggetti `Person` che accetta i parametri `name` e `age` e crea un nuovo oggetto con le proprietà `name` e `age`. Possiamo quindi utilizzare il costruttore per creare nuovi oggetti `person1` e `person2`.

## Prototipi degli oggetti

In Javascript, gli oggetti possono avere un prototipo che definisce le proprietà e i metodi condivisi tra tutti gli oggetti di un determinato tipo.

Ad esempio:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function() {
  console.log('Hello, my name is ' + this.name);
};

let person = new Person('John', 30);

person.greet(); // Output: Hello, my name is John
```

In questo esempio, stiamo definendo un costruttore di oggetti `Person` con una proprietà `name` e `age` e un metodo `greet`. Il metodo `greet` è definito sul prototipo dell'oggetto `Person` e può essere condiviso tra tutti gli oggetti `Person`.

## Controllo di esistenza, operatore “in”

Per controllare se una proprietà esiste in un oggetto in Javascript, possiamo utilizzare l'operatore `in`.

Ad esempio:

```javascript
let person = {
  name: 'John',
  age: 30,
};

console.log('name' in person); // Output: true

console.log('city' in person); // Output: false
```

In questo esempio, stiamo utilizzando l'operatore `in` per controllare se le proprietà `name` e `city` esistono nell'oggetto `person`.

## Controllo di uguaglianza, operatore “==”

Per controllare se due oggetti sono uguali in Javascript, possiamo utilizzare l'operatore `==`.

Ad esempio:

```javascript
let person1 = {
  name: 'John',
  age: 30,
};

let person2 = {
  name: 'John',
  age: 30,
};

console.log(person1 == person2); // Output: false
```

In questo esempio, stiamo confrontando due oggetti `person1` e `person2` utilizzando l'operatore `==`. Poiché gli oggetti sono due entità separate, il risultato sarà `false`.

## Controllo di uguaglianza, operatore “===”

Per controllare se due oggetti sono uguali in Javascript, possiamo utilizzare l'operatore `===`.

Ad esempio:

```javascript
let person1 = {
  name: 'John',
  age: 30,
};

let person2 = person1;

console.log(person1 === person2); // Output: true
```

In questo esempio, stiamo confrontando due oggetti `person1` e `person2` utilizzando l'operatore `===`. Poiché `person2` fa riferimento allo stesso oggetto di `person1`, il risultato sarà `true`.

## Clonazione di oggetti

Per clonare un oggetto in Javascript, possiamo utilizzare l'operatore di assegnazione `=` o il metodo `Object.assign()`.
Ad esempio:

```javascript
let person1 = {
  name: 'John',
  age: 30,
};

let person2 = person1;

person2.name = 'Jane';

console.log(person1.name); // Output: Jane

let person3 = Object.assign({}, person2);

person3.age = 25;

console.log(person3.age); // Output: 25
```

L'assegnazione `person2 = person1` non clona l'oggetto: copia il riferimento, quindi modificare `person2` modifica anche `person1`. `Object.assign()` e lo spread `{ ...person1 }` creano una copia superficiale; gli oggetti annidati restano condivisi. Per dati compatibili si può usare `structuredClone(person1)`.

## Oggetti JSON

In Javascript, gli oggetti possono essere convertiti in stringhe JSON utilizzando il metodo `JSON.stringify()` e viceversa utilizzando il metodo `JSON.parse()`.

Ad esempio:

```javascript
let person = {
  name: 'John',
  age: 30,
};

let json = JSON.stringify(person);

console.log(json); // Output: {"name":"John","age":30}

let person2 = JSON.parse(json);

console.log(person2.name); // Output: John
```

In questo esempio, stiamo convertendo l'oggetto `person` in una stringa JSON utilizzando il metodo `JSON.stringify()` e viceversa utilizzando il metodo `JSON.parse()`.

## Oggetti globali

In Javascript, gli oggetti globali sono oggetti predefiniti che sono disponibili in tutto il codice. Alcuni degli oggetti globali più comuni in Javascript includono `Object`, `Array`, `String`, `Number`, `Boolean`, `Date`, `Math`, `RegExp`, `Error`, `JSON`, `console`, `document`, `window`, ecc.

Ad esempio:

```javascript
let array = [1, 2, 3, 4, 5];

console.log(Array.isArray(array)); // Output: true

let date = new Date();

console.log(date.getFullYear()); // Output: 2021
```

In questo esempio, stiamo utilizzando gli oggetti globali `Array` e `Date` per verificare se un oggetto è un array e ottenere l'anno corrente.

## Oggetti built-in

In Javascript, ci sono molti oggetti built-in che forniscono funzionalità utili per lavorare con dati e interagire con l'ambiente di esecuzione. Alcuni degli oggetti built-in più comuni in Javascript includono `Object`, `Array`, `String`, `Number`, `Boolean`, `Date`, `Math`, `RegExp`, `Error`, `JSON`, `console`, `document`, `window`, ecc.

Ad esempio:

```javascript
let array = [1, 2, 3, 4, 5];

console.log(array.length); // Output: 5

let string = 'Hello, World!';

console.log(string.toUpperCase()); // Output: HELLO, WORLD!
```

In questo esempio, stiamo utilizzando gli oggetti built-in `Array` e `String` per ottenere la lunghezza di un array e convertire una stringa in maiuscolo.

## Oggetti personalizzati

In Javascript, possiamo creare oggetti personalizzati utilizzando costruttori di oggetti, prototipi e metodi.

Ad esempio:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function() {
  console.log('Hello, my name is ' + this.name);
};

let person = new Person('John', 30);

person.greet(); // Output: Hello, my name is John
```

In questo esempio, stiamo creando un oggetto personalizzato `Person` utilizzando un costruttore di oggetti e un prototipo con un metodo `greet`.

## Metodi degli oggetti,"this"

In Javascript, il riferimento `this` all'interno di un metodo di un oggetto si riferisce all'oggetto stesso.

Ad esempio:

```javascript
let person = {
  name: 'John',
  age: 30,
  greet: function() {
    console.log('Hello, my name is ' + this.name);
  },
};

person.greet(); // Output: Hello, my name is John
```

In questo esempio, stiamo definendo un metodo `greet` sull'oggetto `person` che utilizza il riferimento `this` per accedere alla proprietà `name` dell'oggetto stesso.

Il valore di `this` dipende da come una funzione viene chiamata, non solo da dove è scritta. `person.greet()` usa `person`, mentre se il metodo viene estratto (`const saluta = person.greet`) il riferimento all'oggetto si perde. Le arrow function catturano invece il `this` esterno.

## Concatenamento opzionale '?.'

In Javascript, l'operatore di concatenamento opzionale `?.` può essere utilizzato per accedere alle proprietà di un oggetto in modo sicuro, evitando errori se l'oggetto o la proprietà non esistono.

Ad esempio:

```javascript
let person = {
  name: 'John',
  age: 30,
};

console.log(person?.name); // Output: John

console.log(person?.city); // Output: undefined
```

In questo esempio, stiamo utilizzando l'operatore di concatenamento opzionale `?.` per accedere alle proprietà `name` e `city` dell'oggetto `person`.

## Corto circuito

Come detto in precedenza, il costrutto ?. interrompe immediatamente (manda in “corto circuito”) la valutazione se la proprietà a destra non esiste.

Quindi, nel caso ci siano ulteriori chiamate a funzione o side-effects, questi non verranno eseguiti.

Ad esempio:

```javascript
let user = null;
let x = 0;

user?.sayHi(x++); // non esiste "sayHi", quindi l'esecuzione non raggiungerà x++

alert(x); // 0, valore non incrementato
```

In questo esempio, l'operazione `x++` non viene eseguita perché l'operatore di concatenamento opzionale `?.` interrompe la valutazione se la proprietà `sayHi` non esiste.

## Altre varianti: `?.()`, `?.[]`

La concatenazione opzionale `?.` non è un operatore, ma uno speciale costrutto sintattico, che funziona anche con le funzioni e le parentesi quadre.

Ad esempio, `?.()` viene utilizzato per invocare una funzione che potrebbe non esistere.

Nel codice sotto, alcuni dei nostri utenti possiedono il metodo admin, mentre altri no:

```javascript
let userAdmin = {
  admin() {
    alert("I am admin");
  }
};

let userGuest = {};

userAdmin.admin?.(); // I am admin

userGuest.admin?.(); // niente (il metodo non esiste)
```

Qui, in entrambe le righe, come prima cosa abbiamo utilizzato il punto (`user1.admin`) per ottenere la proprietà admin, poiché l’oggetto user deve necessariamente esistere, quindi l’accesso è sicuro.

Successivamente `?.()` controlla la parte sinistra: se la funzione admin esiste, allora viene eseguita (ciò che accade con `user1`). Altrimenti (con `user2`) la valutazione si interrompe senza errori.

La sintassi `?.` funziona anche con le parentesi `[]` (invece del punto `.`). Come nei casi precedenti, possiamo accedere con sicurezza alla proprietà di un oggetto che potrebbe non esistere.

Ad esempio:

```javascript
let key = "firstName";

let user1 = {
  firstName: "John"
};

let user2 = null;

alert( user1?.[key] ); // John
alert( user2?.[key] ); // undefined
```

Possiamo anche utilizzare `?.` con delete:

```javascript
delete user?.name; // cancella user.name se l'utente esiste
```

## Destructuring e sintassi abbreviata

Il destructuring permette di estrarre proprietà e di assegnare valori predefiniti:

```javascript
const persona = { name: "Ada", age: 36 };
const { name, age } = persona;
const copia = { ...persona, active: true };
```

La sintassi abbreviata dei metodi (`greet() {}`), le proprietà calcolate (`{ [chiave]: valore }`) e lo spread rendono gli oggetti più espressivi, ma non cambiano il fatto che siano mutabili e passati per riferimento.

### Conclusioni

Gli oggetti in Javascript sono una parte fondamentale del linguaggio e ci consentono di raggruppare dati e funzionalità in un'unica entità. Possiamo creare, accedere, modificare, aggiungere e eliminare proprietà di un oggetto utilizzando le varie tecniche descritte in questo articolo.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione18)
