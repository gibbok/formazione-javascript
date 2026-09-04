# Promise e async/await

Una Promise rappresenta il risultato futuro di un'operazione asincrona, come una richiesta HTTP o un timer. Può essere `pending`, `fulfilled` oppure `rejected`; dopo la conclusione non cambia più stato.

## Creare e consumare una Promise

```javascript
const promessa = new Promise((resolve, reject) => {
  const riuscita = true;

  if (riuscita) resolve("Operazione completata");
  else reject(new Error("Operazione fallita"));
});

promessa
  .then(risultato => risultato.toUpperCase())
  .then(risultato => console.log(risultato))
  .catch(errore => console.error(errore.message))
  .finally(() => console.log("Terminata"));
```

Ogni `then` restituisce una nuova Promise. Se il callback restituisce una Promise, la catena aspetta che venga completata.

## `async` e `await`

Una funzione `async` restituisce sempre una Promise. `await` rende lineare la lettura del codice senza bloccare il thread:

```javascript
function aspetta(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function esempio() {
  await aspetta(500);
  return "Fatto";
}

esempio().then(console.log);
```

Gli errori di una Promise attesa con `await` possono essere gestiti con `try...catch`.

```javascript
async function caricaUtente(url) {
  try {
    const risposta = await fetch(url);
    if (!risposta.ok) throw new Error(`HTTP ${risposta.status}`);
    return await risposta.json();
  } catch (errore) {
    console.error("Impossibile caricare l'utente", errore);
    throw errore;
  }
}
```

`fetch` non rifiuta automaticamente la Promise per 404 o 500: controllare sempre `ok`.

## Sequenziale o parallelo

Se la seconda operazione dipende dalla prima, usare due `await` in sequenza:

```javascript
const utente = await caricaUtente("/api/utente");
const ordini = await caricaOrdini(utente.id);
```

Per operazioni indipendenti usare `Promise.all`:

```javascript
const [profilo, notifiche] = await Promise.all([
  caricaProfilo(),
  caricaNotifiche()
]);
```

`Promise.all` fallisce appena una Promise fallisce. `Promise.allSettled` aspetta invece tutti i risultati; `Promise.race` restituisce il primo risultato; `Promise.any` restituisce il primo successo.

## Cicli asincroni

`forEach` non aspetta una callback `async`:

```javascript
valori.forEach(async valore => {
  await salva(valore);
});
```

Per operazioni sequenziali usare `for...of`:

```javascript
for (const valore of valori) {
  await salva(valore);
}
```

Per operazioni indipendenti creare le Promise e usare `Promise.all`.

## Cancellare una richiesta

```javascript
const controller = new AbortController();
const timeout = setTimeout(() => controller.abort(), 5000);

try {
  const risposta = await fetch("/api/dati", {
    signal: controller.signal
  });
  console.log(await risposta.json());
} catch (errore) {
  console.error(errore.name === "AbortError" ? "Annullata" : errore);
} finally {
  clearTimeout(timeout);
}
```

## Riepilogo

Le Promise descrivono risultati futuri. `async/await` ne semplifica l'uso, `try...catch` gestisce gli errori e `Promise.all` coordina operazioni parallele. Distinguere sequenze dipendenti da operazioni indipendenti evita attese inutili.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione21) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione23)
