# Hooks

Gli Hooks sono funzioni React che permettono ai componenti funzione di usare stato, contesto, effetti e altre capacità.

## Rules of Hooks

Chiamare Hooks solo al livello superiore di un componente o di un custom Hook, mai dentro condizioni, cicli o callback. Il nome di un custom Hook inizia con `use`.

```jsx
function useOnline() {
  const [online, setOnline] = useState(navigator.onLine);
  useEffect(() => {
    const aggiorna = () => setOnline(navigator.onLine);
    addEventListener("online", aggiorna);
    addEventListener("offline", aggiorna);
    return () => {
      removeEventListener("online", aggiorna);
      removeEventListener("offline", aggiorna);
    };
  }, []);
  return online;
}
```

Un custom Hook riusa logica, non markup: ogni componente che lo chiama riceve il proprio stato. Gli Hooks devono essere chiamati sempre nello stesso ordine a ogni render.

## Hook principali

- `useState`: stato locale;
- `useEffect`: sincronizzazione con sistemi esterni;
- `useContext`: lettura di contesto;
- `useReducer`: transizioni di stato complesse;
- `useRef`: valore mutabile che non provoca render;
- `useMemo` e `useCallback`: ottimizzazioni mirate, non predefinite;
- `useId`: id stabili per accessibilità;
- `useTransition` e `useDeferredValue`: aggiornamenti non urgenti.

React Compiler può automatizzare molte memoizzazioni; prima di aggiungere `memo`, `useMemo` o `useCallback` misurare il problema.

## `useState`

`useState` conserva un valore tra i render e restituisce una funzione per aggiornarlo:

```jsx
import { useState } from "react";

function Contatore() {
  const [conteggio, setConteggio] = useState(0);

  function incrementaDueVolte() {
    setConteggio(valore => valore + 1);
    setConteggio(valore => valore + 1);
  }

  return (
    <button onClick={incrementaDueVolte}>
      {conteggio}
    </button>
  );
}
```

Quando il nuovo valore dipende dal precedente usare la forma funzionale. Per oggetti e array creare un nuovo riferimento invece di mutare quello esistente:

```jsx
setProfilo(profilo => ({ ...profilo, attivo: true }));
setElementi(elementi => elementi.filter(elemento => elemento.id !== id));
```

Il lazy initializer viene eseguito per calcolare lo stato iniziale:

```jsx
const [impostazioni, setImpostazioni] = useState(() => caricaImpostazioni());
```

Non conservare nello stato valori derivabili da props o da altri stati: calcolarli durante il render evita duplicazioni.

## `useEffect`

`useEffect` sincronizza il componente con un sistema esterno, come timer, DOM, WebSocket o API del browser:

```jsx
import { useEffect, useState } from "react";

function Orologio() {
  const [ora, setOra] = useState(() => new Date());

  useEffect(() => {
    const id = setInterval(() => setOra(new Date()), 1000);
    return () => clearInterval(id);
  }, []);

  return <time>{ora.toLocaleTimeString()}</time>;
}
```

Il cleanup viene eseguito prima di un nuovo setup e quando il componente viene smontato. Le dipendenze devono includere ogni valore reattivo letto dall'effetto:

```jsx
useEffect(() => {
  const controller = new AbortController();

  fetch(`/api/utenti/${id}`, { signal: controller.signal })
    .then(risposta => risposta.json())
    .then(setUtente)
    .catch(errore => {
      if (errore.name !== "AbortError") setErrore(errore);
    });

  return () => controller.abort();
}, [id]);
```

Non usare un effetto per trasformare dati già disponibili o per rispondere a un click: in quei casi bastano un calcolo durante il render o un event handler.

## `useContext`

`useContext` legge il valore del provider più vicino senza passare props attraverso ogni componente:

```jsx
import { createContext, useContext } from "react";

const LinguaContext = createContext("it");

function App() {
  return (
    <LinguaContext value="en">
      <Titolo />
    </LinguaContext>
  );
}

function Titolo() {
  const lingua = useContext(LinguaContext);
  return <h1>{lingua === "it" ? "Benvenuto" : "Welcome"}</h1>;
}
```

In React 19 si può usare direttamente `<LinguaContext value={...}>`; `<LinguaContext.Provider>` resta valido nei progetti esistenti. Il valore del Context deve essere stabile quando possibile: ogni consumatore viene aggiornato quando cambia il riferimento del valore.

## `useReducer`

`useReducer` è utile quando lo stato ha transizioni numerose o correlate:

```jsx
import { useReducer } from "react";

function reducer(stato, azione) {
  switch (azione.type) {
    case "aggiungi":
      return { ...stato, totale: stato.totale + azione.valore };
    case "azzera":
      return { ...stato, totale: 0 };
    default:
      throw new Error(`Azione sconosciuta: ${azione.type}`);
  }
}

function Totale() {
  const [stato, dispatch] = useReducer(reducer, { totale: 0 });
  return (
    <>
      <strong>{stato.totale}</strong>
      <button onClick={() => dispatch({ type: "aggiungi", valore: 5 })}>+</button>
      <button onClick={() => dispatch({ type: "azzera" })}>Azzera</button>
    </>
  );
}
```

Il reducer deve essere puro: non eseguire richieste, timer o modifiche esterne al suo interno. L'azione descrive cosa è successo; il reducer decide il nuovo stato.

## `useRef`

`useRef` conserva un valore mutabile tra i render senza provocare un nuovo render quando cambia. È adatto a riferimenti DOM e valori tecnici:

```jsx
import { useRef } from "react";

function Ricerca() {
  const inputRef = useRef(null);

  return (
    <>
      <input ref={inputRef} />
      <button onClick={() => inputRef.current?.focus()}>Cerca</button>
    </>
  );
}
```

Può anche conservare il valore precedente:

```jsx
const precedente = useRef(valore);
useEffect(() => {
  precedente.current = valore;
}, [valore]);
```

Non usare ref per dati che devono comparire nell'interfaccia: in quel caso serve state.

## `useMemo`

`useMemo` riutilizza il risultato di un calcolo tra render finché cambiano le dipendenze:

```jsx
const filtrati = useMemo(
  () => prodotti.filter(prodotto => prodotto.nome.includes(query)),
  [prodotti, query]
);
```

È un'ottimizzazione, non una garanzia semantica. Prima misurare il costo; un memo inutile aumenta complessità e può diventare errato se le dipendenze sono incomplete.

## `useCallback`

`useCallback` conserva il riferimento a una funzione:

```jsx
const salva = useCallback(() => {
  onSave(id);
}, [id, onSave]);
```

Serve soprattutto quando una callback viene passata a un componente memoizzato o usata come dipendenza di un Hook. Non rende automaticamente più veloce ogni funzione e non deve servire a nascondere un problema di dipendenze.

## `useId`

`useId` genera un id stabile tra render e compatibile con il rendering server/client:

```jsx
function CampoEmail() {
  const id = useId();
  return (
    <>
      <label htmlFor={id}>Email</label>
      <input id={id} type="email" />
    </>
  );
}
```

Non usarlo come `key` per liste o come identificativo di dati: serve a collegare controlli e messaggi accessibili.

## `useTransition`

Una transition marca un aggiornamento come non urgente:

```jsx
const [isPending, startTransition] = useTransition();

function cambiaFiltro(nuovoFiltro) {
  startTransition(() => setFiltro(nuovoFiltro));
}

return (
  <>
    <input onChange={evento => setQuery(evento.target.value)} />
    <button onClick={() => cambiaFiltro("recenti")}>Recenti</button>
    {isPending && <p>Aggiornamento in corso...</p>}
  </>
);
```

Non mettere in una transition aggiornamenti che devono essere immediati, come il testo digitato o lo stato di un controllo.

## `useDeferredValue`

`useDeferredValue` produce una versione ritardata di un valore costoso da usare:

```jsx
const queryDifferita = useDeferredValue(query);
const risultati = useMemo(
  () => cercaNelCatalogo(queryDifferita),
  [queryDifferita]
);
```

L'input può aggiornarsi subito mentre i risultati si aggiornano in background. Non è un debounce: non imposta un tempo fisso e non riduce necessariamente il numero di render.

## `useLayoutEffect`

`useLayoutEffect` esegue il setup dopo il commit ma prima che il browser dipinga. È adatto a misurare un elemento e correggere immediatamente la posizione:

```jsx
const tooltipRef = useRef(null);

useLayoutEffect(() => {
  const altezza = tooltipRef.current?.getBoundingClientRect().height ?? 0;
  setAltezza(altezza);
}, []);
```

Usarlo il meno possibile: può bloccare il paint. Nei componenti renderizzati sul server preferire `useEffect` o una strategia isomorfica.

## `useImperativeHandle`

Permette di esporre un'API imperativa limitata attraverso un ref:

```jsx
function Campo({ ref }) {
  const inputRef = useRef(null);

  useImperativeHandle(ref, () => ({
    focus() {
      inputRef.current?.focus();
    }
  }), []);

  return <input ref={inputRef} />;
}
```

In React 19 `ref` può essere una prop dei componenti funzione; nei progetti precedenti si usa spesso `forwardRef`. Preferire props dichiarative quando bastano.

## `useSyncExternalStore`

È l'Hook per sottoscriversi correttamente a uno store esterno, anche con rendering concorrente:

```jsx
const online = useSyncExternalStore(
  callback => {
    addEventListener("online", callback);
    addEventListener("offline", callback);
    return () => {
      removeEventListener("online", callback);
      removeEventListener("offline", callback);
    };
  },
  () => navigator.onLine,
  () => true
);
```

Il terzo argomento è lo snapshot server, importante per evitare mismatch durante hydration.

## `useDebugValue`

Un custom Hook può mostrare un'etichetta utile in React DevTools:

```jsx
function useOnline() {
  const online = useSyncExternalStore(...);
  useDebugValue(online ? "online" : "offline");
  return online;
}
```

`useDebugValue` serve solo al debugging e non modifica il comportamento dell'interfaccia.

## Hooks React 19

### `useActionState`

`useActionState` collega un'Action allo stato restituito e al flag pending:

```jsx
const [errore, submit, isPending] = useActionState(
  async (_statoPrecedente, formData) => {
    const risposta = await salvaProfilo(formData);
    return risposta.ok ? null : risposta.errore;
  },
  null
);

return (
  <form action={submit}>
    <input name="nome" />
    <button disabled={isPending}>{isPending ? "Salvo..." : "Salva"}</button>
    {errore && <p role="alert">{errore}</p>}
  </form>
);
```

L'Action deve restituire lo stato successivo. La validazione server resta necessaria, anche quando il form è tipizzato.

### `useOptimistic`

Mostra un risultato provvisorio mentre l'operazione reale è in corso:

```jsx
const [messaggiOttimistici, aggiungiOttimistico] = useOptimistic(
  messaggi,
  (correnti, testo) => [...correnti, { testo, invio: true }]
);

async function invia(formData) {
  aggiungiOttimistico(formData.get("testo"));
  await salvaMessaggio(formData);
}
```

Se l'operazione fallisce, React torna ai dati reali. Mostrare uno stato “in invio” e gestire esplicitamente il retry.

### `use`

`use` può leggere una Promise gestita da Suspense o un Context durante il render:

```jsx
function Commenti({ commentiPromise }) {
  const commenti = use(commentiPromise);
  return commenti.map(commento => <p key={commento.id}>{commento.testo}</p>);
}
```

Non creare la Promise nel render del componente: deve provenire da un livello che la conserva o da un framework compatibile con Suspense. A differenza degli Hooks tradizionali, `use` può essere chiamato dopo un controllo condizionale, ma deve comunque essere usato durante il render.

## Regole pratiche

- Usare state per dati visualizzati e ref per valori imperativi.
- Usare effect solo per sincronizzare sistemi esterni.
- Mantenere completi gli array delle dipendenze.
- Non aggiungere memoizzazione senza una misurazione.
- Pulire sempre timer, listener, observer e subscription.
- Testare loading, errori, cancellazione e Strict Mode.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione81) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione83)
