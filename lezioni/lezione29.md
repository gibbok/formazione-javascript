# Attributi e proprietà

Gli attributi appartengono al markup HTML; le proprietà sono valori esposti dagli oggetti DOM. Spesso sono collegati, ma non sono sempre la stessa cosa.

```html
<input id="email" type="email" value="iniziale@example.com">
```

```javascript
const input = document.querySelector("#email");
console.log(input.getAttribute("value"));
console.log(input.value);
```

L'attributo rappresenta il valore iniziale, mentre la proprietà `value` rappresenta il valore corrente digitato dall'utente.

## API degli attributi

```javascript
input.setAttribute("aria-label", "Email");
console.log(input.hasAttribute("required"));
input.removeAttribute("disabled");
```

Per attributi booleani, la presenza spesso equivale a `true`:

```javascript
input.setAttribute("required", "");
console.log(input.hasAttribute("required")); // true
```

## `data-*`

Gli attributi personalizzati `data-*` sono accessibili con `dataset`:

```html
<button data-id-utente="42">Apri</button>
```

```javascript
const button = document.querySelector("button");
console.log(button.dataset.idUtente); // "42"
```

I valori del dataset sono sempre stringhe.

## Riepilogo

Usare proprietà per lo stato corrente del controllo e attributi per configurazione e markup. `dataset` è utile per metadati semplici, non per conservare dati sensibili.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione28) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione30)
