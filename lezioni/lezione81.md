# Stato e ciclo di vita

Lo stato contiene dati che cambiano nel tempo e la cui modifica deve produrre un nuovo render.

```jsx
import { useState } from "react";

function Contatore() {
  const [conteggio, setConteggio] = useState(0);
  return (
    <button onClick={() => setConteggio(valore => valore + 1)}>
      {conteggio}
    </button>
  );
}
```

Usare l'aggiornamento funzionale quando il nuovo valore dipende dal precedente. Non mutare oggetti o array:

```jsx
setUtente(precedente => ({ ...precedente, attivo: true }));
```

## Effetti e cleanup

```jsx
useEffect(() => {
  const id = setInterval(aggiorna, 1000);
  return () => clearInterval(id);
}, []);
```

`useEffect` sincronizza il componente con sistemi esterni dopo il commit. Non usarlo per calcoli derivabili o per sincronizzare inutilmente due stati. Le dipendenze devono contenere i valori letti dall'effetto.

## Strict Mode e ciclo di vita

React non espone più un ciclo di vita basato su classi per i componenti funzione. In sviluppo Strict Mode può eseguire setup e cleanup più volte per scoprire effetti non idempotenti. Il cleanup deve annullare subscription, timer e richieste.

## Stato derivato

Se un valore può essere calcolato da props e stato durante il render, non conservarlo in un secondo state. Ridurre la duplicazione evita incoerenze.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione80) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione82)
