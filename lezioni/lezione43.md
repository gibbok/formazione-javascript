# Network requests

`fetch` invia richieste HTTP e restituisce una Promise.

```javascript
const risposta = await fetch("/api/utenti");
if (!risposta.ok) throw new Error(`HTTP ${risposta.status}`);
const utenti = await risposta.json();
```

## Metodo e body

```javascript
await fetch("/api/utenti", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ nome: "Ada" })
});
```

`fetch` non rifiuta la Promise per status HTTP. Gestire timeout con `AbortController`, errori di rete e dati inattesi.

## CORS e credenziali

Le richieste cross-origin richiedono autorizzazione del server tramite CORS. Cookie e credenziali richiedono opzioni esplicite e configurazione server coerente.

## Riepilogo

Controllare sempre status, formato e validità della risposta. Il client non sostituisce l'autorizzazione e la validazione del server.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione42) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione44)
