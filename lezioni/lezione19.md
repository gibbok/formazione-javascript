# Prototypes e inheritance

JavaScript usa un modello di ereditarietà basato sui **prototipi**. Ogni oggetto può avere un altro oggetto come prototipo; quando una proprietà non viene trovata direttamente, il motore la cerca lungo la catena dei prototipi.

Le classi della lezione successiva sono una sintassi più comoda costruita sopra questo meccanismo.

## Proprietà proprie e proprietà ereditate

```javascript
const animale = {
  mangia() {
    return "Sto mangiando";
  }
};

const cane = Object.create(animale);
cane.nome = "Luna";

console.log(cane.nome); // proprietà propria
console.log(cane.mangia()); // metodo ereditato
console.log(Object.hasOwn(cane, "mangia")); // false
```

`nome` appartiene a `cane`, mentre `mangia` appartiene al suo prototipo. Se una proprietà propria ha lo stesso nome di una proprietà ereditata, la prima nasconde la seconda.

## La catena dei prototipi

```javascript
const base = { tipo: "base" };
const intermedio = Object.create(base);
const finale = Object.create(intermedio);

console.log(finale.tipo); // base
console.log(Object.getPrototypeOf(finale) === intermedio); // true
```

La ricerca termina quando trova la proprietà o arriva a `null`. `Object.getPrototypeOf()` legge il prototipo e `Object.setPrototypeOf()` lo modifica, ma quest'ultimo è generalmente da evitare dopo la creazione perché può peggiorare le prestazioni.

## Costruttori e `prototype`

```javascript
function Persona(nome) {
  this.nome = nome;
}

Persona.prototype.saluta = function () {
  return `Ciao, sono ${this.nome}`;
};

const ada = new Persona("Ada");
const grace = new Persona("Grace");

console.log(ada.saluta());
console.log(ada.saluta === grace.saluta); // true
```

Il metodo è sul prototipo e viene condiviso da tutte le istanze. L'operatore `new` crea l'oggetto, collega `Persona.prototype`, esegue il costruttore con `this` riferito all'oggetto e restituisce l'istanza.

## `instanceof`

```javascript
console.log(ada instanceof Persona); // true
console.log(ada instanceof Object);  // true
```

`instanceof` controlla se il prototipo del costruttore appare nella catena dell'oggetto. Non verifica semplicemente che l'oggetto abbia una certa forma.

## Ereditarietà

```javascript
function Animale(nome) {
  this.nome = nome;
}

Animale.prototype.mangia = function () {
  return `${this.nome} sta mangiando`;
};

function Cane(nome, razza) {
  Animale.call(this, nome);
  this.razza = razza;
}

Cane.prototype = Object.create(Animale.prototype);
Cane.prototype.constructor = Cane;

Cane.prototype.abbaia = function () {
  return `${this.nome} abbaia`;
};
```

`Animale.call(this, nome)` inizializza le proprietà dell'istanza. `Object.create` collega i metodi ereditati e il ripristino di `constructor` mantiene corretta l'informazione sul costruttore.

## Prototipi e oggetti nativi

`for...in` può includere proprietà ereditate. Per leggere solo quelle proprie usare `Object.keys`, `Object.values`, `Object.entries` o `Object.hasOwn`:

```javascript
const utente = { nome: "Ada", attivo: true };

for (const [chiave, valore] of Object.entries(utente)) {
  console.log(chiave, valore);
}
```

Aggiungere proprietà a `Array.prototype`, `Object.prototype` o ad altri oggetti nativi è sconsigliato: può creare conflitti con librerie e codice futuro.

## Riepilogo

- La ricerca delle proprietà segue la catena dei prototipi.
- `Object.create` crea un oggetto con un prototipo scelto.
- I metodi sul prototipo sono condivisi tra le istanze.
- `new` collega l'istanza al `prototype` del costruttore.
- `instanceof` controlla la catena dei prototipi.
- Le classi sono una sintassi moderna basata sugli stessi meccanismi.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione18) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione20)
