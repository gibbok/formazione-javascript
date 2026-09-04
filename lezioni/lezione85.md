# React avanzato

React moderno separa rendering, effetti, dati e aggiornamenti urgenti. Le API concorrenti aiutano a mantenere reattiva l'interfaccia, ma non rendono automaticamente asincrono ogni codice.

## Context

```jsx
const TemaContext = createContext("chiaro");

function App() {
  return <TemaContext value="scuro"><Pagina /></TemaContext>;
}

function Titolo() {
  const tema = use(TemaContext);
  return <h1 data-tema={tema}>Titolo</h1>;
}
```

In React 19 un Context può essere usato direttamente come provider; `<TemaContext.Provider>` resta comune nei progetti esistenti. Il Context è adatto a tema, lingua e servizi condivisi, non a ogni stato locale: aggiornamenti frequenti possono rendere molte parti dipendenti.

## Suspense e `use`

```jsx
function Commenti({ promise }) {
  const commenti = use(promise);
  return commenti.map(commento => <p key={commento.id}>{commento.testo}</p>);
}

function Pagina({ promise }) {
  return (
    <Suspense fallback={<p>Caricamento...</p>}>
      <Commenti promise={promise} />
    </Suspense>
  );
}
```

`use` può leggere Promise gestite da un framework o da una libreria compatibile con Suspense; non creare una nuova Promise a ogni render. Error Boundary gestiscono errori di render e Actions, mentre Suspense gestisce attesa e fallback: sono problemi diversi.

## Transizioni

```jsx
const [isPending, startTransition] = useTransition();

function cambiaFiltro(filtro) {
  startTransition(() => setFiltro(filtro));
}
```

Gli aggiornamenti urgenti, come digitazione e focus, devono restare immediati. Filtri costosi, navigazione e risultati possono essere non urgenti. `useDeferredValue` offre una versione ritardata di un valore senza bloccare l'input.

## Refs in React 19

I componenti funzione possono ricevere `ref` come prop senza `forwardRef` nei nuovi pattern React 19:

```jsx
function Campo({ ref, ...props }) {
  return <input ref={ref} {...props} />;
}
```

Usare ref per focus, misure o integrazioni imperative, non per sostituire lo stato visualizzato. Un callback ref può restituire una funzione di cleanup nelle API moderne.

## Server Components e Client Components

I Server Components vengono eseguiti in un ambiente server/build e non includono JavaScript nel client per la loro logica. Non possono usare Hooks client o browser API. I Client Components, indicati dal framework con `"use client"`, gestiscono interazione e stato.

Le Server Functions, indicate dal framework con `"use server"`, permettono di chiamare codice server dal client attraverso un protocollo gestito dal framework: autenticare e autorizzare sempre dentro la funzione. React da solo non fornisce un server completo o un router.

## SSR, hydration e metadata

`hydrateRoot` collega React a HTML generato sul server. Il primo render client deve produrre lo stesso markup: evitare durante il render `Date.now()`, `Math.random()` o accessi condizionali a `window`. React 19 supporta metadata come `title`, `meta` e `link` nei componenti e migliora i messaggi di hydration.

## React Compiler

React Compiler è uno strumento di build che può automatizzare memoizzazione e ottimizzazioni in progetti configurati. Non corregge componenti impuri e non sostituisce le Rules of React. Usare ESLint e DevTools per individuare effetti, mutazioni e render inutili prima di ottimizzare manualmente.

## Architettura e test

Separare componenti presentazionali, stato, accesso dati e side effect. Testare comportamenti osservabili, navigazione da tastiera, loading, errore e aggiornamenti ottimistici. Misurare con Profiler prima di aggiungere memoizzazione.

## Riepilogo

React avanzato significa progettare confini tra server e client, mantenere puri i render, usare Suspense e transizioni per l'esperienza utente e gestire Actions con errori e pending state. Le API più nuove richiedono sempre un ambiente compatibile e una strategia di validazione server.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione84)
