# Eventi in React

Gli eventi JSX usano nomi camelCase e ricevono funzioni, non stringhe:

```jsx
function Pulsante() {
  function gestisciClick(evento) {
    console.log(evento.currentTarget);
  }
  return <button onClick={gestisciClick}>Apri</button>;
}
```

React usa un sistema di eventi coerente tra browser. `preventDefault` impedisce il comportamento nativo; `stopPropagation` ferma il bubbling e va usato solo quando necessario.

## Eventi e stato

```jsx
function Campo() {
  const [valore, setValore] = useState("");
  return <input value={valore} onChange={e => setValore(e.target.value)} />;
}
```

Non leggere un evento sintetico in un callback asincrono aspettandosi che rappresenti ancora lo stesso stato: estrarre il valore necessario subito. Gli aggiornamenti di stato sono batchati, quindi usare updater funzionali per più aggiornamenti dipendenti.

## Event delegation

React delega gli eventi nel root in modo trasparente. Per liste dinamiche mettere un handler sul contenitore e risalire con `closest` o usare il dato passato al componente, mantenendo però controlli semantici e accessibili.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione82) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione84)
