# Props

Le props sono dati passati dal genitore al componente figlio. Sono di sola lettura: il figlio non deve modificarle.

```jsx
function Pulsante({ testo, disabilitato = false, onClick }) {
  return (
    <button disabled={disabilitato} onClick={onClick}>
      {testo}
    </button>
  );
}
```

## Tipi e default

Con TypeScript descrivere le props:

```tsx
interface ListaProps {
  elementi: { id: number; nome: string }[];
  titolo?: string;
}
```

Usare default parameter o `??` per valori mancanti. Non duplicare una prop nello stato senza una ragione: la copia può diventare obsoleta.

## Callback e lifting state

```jsx
function Filtro({ valore, onChange }) {
  return <input value={valore} onChange={e => onChange(e.target.value)} />;
}
```

Il genitore mantiene lo stato condiviso e passa callback per aggiornarlo. Questo pattern si chiama lifting state up.

## Children e render prop

`children` permette di comporre layout. Una prop funzione può personalizzare la resa, ma va usata quando la composizione normale non basta.

Le props devono contenere dati serializzabili quando attraversano confini server/client; funzioni e oggetti complessi richiedono supporto specifico del framework.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione79) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione81)
