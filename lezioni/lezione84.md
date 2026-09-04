# Form in React

Un form può essere controllato dallo stato oppure letto al submit come form HTML nativo.

## Input controllato

```jsx
function Login() {
  const [email, setEmail] = useState("");
  return (
    <form>
      <input value={email} onChange={e => setEmail(e.target.value)} />
      <button>Accedi</button>
    </form>
  );
}
```

Lo stato è la fonte di verità, utile per validazione immediata e UI condizionale. Per form grandi, campi non controllati e `FormData` possono ridurre render e codice.

## Actions React 19

React 19 permette di passare una funzione ad `action`:

```jsx
async function cerca(formData) {
  const query = formData.get("query");
  await inviaRicerca(query);
}

function Ricerca() {
  return (
    <form action={cerca}>
      <input name="query" />
      <button type="submit">Cerca</button>
    </form>
  );
}
```

L'Action riceve `FormData`, usa una Transition e resetta i controlli non controllati dopo il successo. `useActionState` espone risultato e pending:

```jsx
const [errore, action, pending] = useActionState(async (_stato, dati) => {
  try {
    await salva(dati);
    return null;
  } catch (e) {
    return e.message;
  }
}, null);
```

`useFormStatus` va usato in un componente figlio del form per leggere `pending`. `useOptimistic` permette di mostrare subito il risultato previsto, con ritorno allo stato reale se l'operazione fallisce.

La validazione deve esistere anche sul server. Per accessibilità usare label, messaggi associati e stato di errore leggibile.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione83) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione85)
