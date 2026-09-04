# Classi

Le classi offrono una sintassi ordinata per creare oggetti con stato e comportamenti comuni. In JavaScript sono costruite sopra i prototipi: semplificano la scrittura dell'ereditarietà senza eliminare il modello prototipale.

## Dichiarare una classe

```javascript
class Persona {
  constructor(nome, eta) {
    this.nome = nome;
    this.eta = eta;
  }

  saluta() {
    return `Ciao, sono ${this.nome}`;
  }
}

const persona = new Persona("Ada", 36);
console.log(persona.saluta());
```

`constructor` viene eseguito da `new`. I metodi sono condivisi tramite il prototipo e una classe non può essere usata prima della sua dichiarazione.

## Proprietà e metodi statici

```javascript
class Contatore {
  valore = 0;

  incrementa() {
    this.valore += 1;
    return this.valore;
  }

  static crea() {
    return new Contatore();
  }
}

const contatore = Contatore.crea();
console.log(contatore.incrementa());
```

Un metodo `static` si chiama sulla classe, non sull'istanza. È utile per factory e funzioni che non dipendono da un oggetto specifico.

## Getter e setter

```javascript
class Rettangolo {
  constructor(base, altezza) {
    this.base = base;
    this.altezza = altezza;
  }

  get area() {
    return this.base * this.altezza;
  }

  set dimensione(valore) {
    this.base = valore;
    this.altezza = valore;
  }
}
```

Il getter si usa come una proprietà (`rettangolo.area`). Un setter può validare o normalizzare un valore prima di salvarlo.

## Ereditarietà con `extends`

```javascript
class Animale {
  constructor(nome) {
    this.nome = nome;
  }

  verso() {
    return "Verso generico";
  }
}

class Cane extends Animale {
  constructor(nome, razza) {
    super(nome);
    this.razza = razza;
  }

  verso() {
    return "Bau";
  }
}
```

`extends` collega i prototipi. `super(...)` chiama il costruttore della classe padre e deve essere eseguito prima di usare `this` nella classe figlia. `super.metodo()` richiama invece un metodo ereditato.

## Campi privati

```javascript
class Account {
  #saldo = 0;

  deposita(importo) {
    if (importo > 0) this.#saldo += importo;
  }

  get saldo() {
    return this.#saldo;
  }
}
```

I campi con `#` sono accessibili solo dentro la classe. Il prefisso `_` è soltanto una convenzione e non protegge realmente la proprietà.

## `this` nei metodi

Il valore di `this` dipende da come il metodo viene chiamato. Estrarlo può far perdere il riferimento all'istanza:

```javascript
const saluta = persona.saluta;
// saluta(); // non equivale a persona.saluta()

const salutaPersona = persona.saluta.bind(persona);
console.log(salutaPersona());
```

Le arrow function catturano il `this` esterno e non sono automaticamente equivalenti ai metodi tradizionali.

## Quando usare le classi

Le classi sono adatte quando più istanze condividono stato e comportamento. Per dati semplici bastano oggetti letterali e funzioni. Una composizione di oggetti spesso è più flessibile di una gerarchia molto profonda.

## Riepilogo

- `class` definisce un modello per creare istanze.
- `constructor` inizializza lo stato.
- `static` definisce metodi della classe.
- `extends` e `super` gestiscono l'ereditarietà.
- Getter e setter espongono proprietà calcolate o validate.
- I campi `#` sono privati.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione19) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione21)
