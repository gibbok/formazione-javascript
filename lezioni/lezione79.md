# Componenti

Un componente è una funzione che restituisce JSX. I nomi dei componenti iniziano con maiuscola, mentre i tag minuscoli rappresentano elementi HTML.

```jsx
function Scheda({ titolo, children }) {
  return (
    <article>
      <h2>{titolo}</h2>
      {children}
    </article>
  );
}
```

## Composizione

```jsx
function App() {
  return (
    <Scheda titolo="Profilo">
      <p>Contenuto riutilizzabile</p>
    </Scheda>
  );
}
```

Preferire composizione e componenti piccoli a gerarchie profonde. Un componente dovrebbe avere una responsabilità leggibile e non conoscere dettagli inutili del genitore.

## Purezza e render

React può renderizzare più volte un componente, anche in Strict Mode durante lo sviluppo. Il render deve solo calcolare JSX: chiamate di rete, subscription e modifiche esterne appartengono a effetti o a funzioni di evento.

## Componenti specializzati

Estrarre un componente quando esiste una responsabilità, una semantica o un comportamento riusabile, non solo per ridurre il numero di righe. Passare contenuto con `children` evita props eccessivamente rigide.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione78) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione80)
