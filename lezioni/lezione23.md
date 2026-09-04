# Generators e iteratori

Un iteratore produce valori uno alla volta tramite `next()`. Un oggetto iterabile espone `Symbol.iterator` e può essere consumato da `for...of`, spread e destructuring. Array, stringhe, `Map` e `Set` sono iterabili.

## Il protocollo degli iteratori

```javascript
const iteratore = ["a", "b"][Symbol.iterator]();

console.log(iteratore.next()); // { value: "a", done: false }
console.log(iteratore.next()); // { value: "b", done: false }
console.log(iteratore.next()); // { value: undefined, done: true }
```

`done: true` indica che la sequenza è terminata. `for...of` legge i valori, mentre `for...in` percorre i nomi delle proprietà.

## Un iteratore personalizzato

```javascript
function creaContatore(limite) {
  let corrente = 0;

  return {
    [Symbol.iterator]() {
      return this;
    },
    next() {
      if (corrente < limite) {
        return { value: corrente++, done: false };
      }
      return { done: true };
    }
  };
}

for (const numero of creaContatore(3)) {
  console.log(numero); // 0, 1, 2
}
```

## Generator function

Una generator function si dichiara con `function*` e usa `yield` per sospendere l'esecuzione:

```javascript
function* numeriFinoA(limite) {
  for (let numero = 0; numero < limite; numero++) {
    yield numero;
  }
}

const numeri = numeriFinoA(3);
console.log(numeri.next()); // { value: 0, done: false }
console.log(numeri.next()); // { value: 1, done: false }
```

La chiamata al generator non esegue subito il corpo. Ogni `next()` riprende dal punto dopo l'ultimo `yield`.

```javascript
console.log([...numeriFinoA(4)]); // [0, 1, 2, 3]
```

## Valori inviati al generator

Il valore passato a `next()` diventa il risultato del `yield` sospeso:

```javascript
function* dialogo() {
  const nome = yield "Come ti chiami?";
  return `Ciao, ${nome}`;
}

const conversazione = dialogo();
console.log(conversazione.next().value);
console.log(conversazione.next("Ada").value);
```

L'argomento del primo `next()` viene ignorato perché il generator non è ancora sospeso su un `yield`.

## `yield*`

`yield*` delega a un altro iterabile:

```javascript
function* numeri() {
  yield 1;
  yield 2;
}

function* completa() {
  yield 0;
  yield* numeri();
  yield 3;
}

console.log([...completa()]); // [0, 1, 2, 3]
```

## Generator asincroni

Un generator asincrono usa `async function*` e si consuma con `for await...of`:

```javascript
async function* pagine() {
  yield await caricaPagina(1);
  yield await caricaPagina(2);
}

for await (const pagina of pagine()) {
  console.log(pagina);
}
```

È utile per stream, paginazione e sorgenti che producono dati nel tempo.

## Lazy evaluation

I generatori calcolano il valore solo quando viene richiesto. Possono quindi rappresentare sequenze grandi o infinite:

```javascript
function* naturali() {
  let numero = 0;
  while (true) yield numero++;
}
```

Una sequenza infinita deve sempre essere consumata con un limite. I generatori non sono automaticamente più veloci: sono utili quando la produzione progressiva semplifica il problema o riduce la memoria necessaria.

## Riepilogo

- Un iterable espone `Symbol.iterator`.
- Un iterator restituisce `{ value, done }` da `next()`.
- `for...of` consuma gli iterable.
- `function*` crea generatori sospendibili con `yield`.
- `yield*` delega a un altro iterabile.
- `async function*` si consuma con `for await...of`.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione22) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione24)
