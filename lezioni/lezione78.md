# JSX e TSX

JSX è una sintassi che permette di descrivere elementi UI dentro JavaScript. TSX è la stessa sintassi in file TypeScript.

```jsx
const nome = "Ada";
const elemento = <h1>Ciao, {nome}</h1>;
```

JSX viene trasformato in chiamate React. Le espressioni tra `{}` sono JavaScript; non inserire istruzioni `if` direttamente nel markup, ma usare espressioni, variabili o componenti.

## Regole principali

Un componente restituisce un solo nodo radice, eventualmente un Fragment:

```jsx
return (
  <>
    <h1>Titolo</h1>
    <p>Testo</p>
  </>
);
```

Gli attributi HTML usano spesso nomi camelCase: `className`, `htmlFor`, `tabIndex`. Gli elementi devono essere chiusi e gli array renderizzati devono avere una `key` stabile.

## Condizioni e liste

```jsx
{utente ? <Profilo utente={utente} /> : <Login />}
{prodotti.map(prodotto => (
  <li key={prodotto.id}>{prodotto.nome}</li>
))}
```

Non usare l'indice come key quando l'ordine può cambiare. `0`, `false`, `null` e `undefined` hanno comportamenti diversi nelle espressioni JSX: rendere esplicita la condizione.

## Sicurezza

Il testo interpolato viene escapato. `dangerouslySetInnerHTML` deve ricevere soltanto HTML sanificato e fidato.

## TypeScript

```tsx
interface Props { nome: string }
function Saluto({ nome }: Props) {
  return <p>Ciao, {nome}</p>;
}
```

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione77) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione79)
