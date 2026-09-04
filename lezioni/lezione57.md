# Il modulo Express

Express semplifica routing e middleware HTTP.

```javascript
import express from "express";

const app = express();
app.use(express.json());

app.get("/api/saluto", (req, res) => {
  res.json({ messaggio: "Ciao" });
});

app.listen(3000);
```

## Struttura di una richiesta

Express aggiunge metodi di routing sopra il server HTTP di Node. `req.params` contiene parametri del percorso, `req.query` i parametri della query string e `req.body` viene popolato solo dal middleware che analizza il formato:

```javascript
app.use(express.json({ limit: "100kb" }));
app.use(express.urlencoded({ extended: true, limit: "100kb" }));

app.get("/api/utenti/:id", (req, res) => {
  res.json({ id: req.params.id, filtro: req.query.filtro ?? null });
});
```

Limitare il body evita che una richiesta consumi memoria senza controllo. Non fidarsi mai dei tipi presenti in `req.body`: un client può inviare qualsiasi JSON.

## Middleware

Un middleware può terminare la risposta oppure chiamare `next()`:

```javascript
function logRichiesta(req, res, next) {
  const inizio = Date.now();
  res.on("finish", () => {
    console.log(req.method, req.originalUrl, res.statusCode, Date.now() - inizio);
  });
  next();
}

app.use(logRichiesta);
```

L'ordine è importante: un middleware registrato dopo una route non la precede. Un middleware che non chiama `next`, non invia una risposta e non lancia un errore lascia la richiesta bloccata.

## Router e separazione delle responsabilità

Per applicazioni più grandi usare `Router`:

```javascript
import { Router } from "express";

const router = Router();

router.get("/", async (req, res, next) => {
  try {
    const utenti = await servizioUtenti.elenca();
    res.json(utenti);
  } catch (errore) {
    next(errore);
  }
});

app.use("/api/utenti", router);
```

Separare route, servizi e accesso ai dati evita di concentrare tutta la logica nel callback HTTP.

## CRUD e status code

```javascript
router.post("/", async (req, res, next) => {
  try {
    const dati = validaUtente(req.body);
    const utente = await servizioUtenti.crea(dati);
    res.status(201).json(utente);
  } catch (errore) {
    next(errore);
  }
});

router.delete("/:id", async (req, res, next) => {
  try {
    await servizioUtenti.rimuovi(req.params.id);
    res.status(204).end();
  } catch (errore) {
    next(errore);
  }
});
```

Usare `200` per una risposta riuscita con contenuto, `201` per una risorsa creata, `204` senza contenuto, `400` per input invalido, `404` per risorsa assente e `500` per errori inattesi.

## Middleware di errore

Il middleware di errore ha quattro parametri e va registrato dopo le route:

```javascript
app.use((errore, req, res, next) => {
  console.error(errore);

  if (res.headersSent) return next(errore);

  const status = errore.statusCode ?? 500;
  res.status(status).json({
    errore: status >= 500 ? "Errore interno" : errore.message
  });
});
```

In produzione non restituire stack trace o dettagli di database. Gli handler asincroni devono inoltrare i rifiuti a `next` oppure usare una funzione wrapper compatibile con la versione di Express.

## Statici, CORS e sicurezza

```javascript
app.use(express.static("public", {
  dotfiles: "deny",
  index: false
}));
```

Configurare CORS con origini esplicite, non con `*` quando si usano credenziali. Impostare header di sicurezza, rate limiting, cookie `HttpOnly`/`Secure` e validazione schema. HTTPS e autenticazione vanno gestiti anche dal reverse proxy quando presente.

## Avvio e chiusura ordinata

```javascript
const server = app.listen(3000);

process.on("SIGTERM", () => {
  server.close(() => {
    console.log("Server chiuso");
  });
});
```

Chiudere pool database, connessioni e consumer prima di terminare il processo. Un server Express è un componente HTTP, non una sostituzione della progettazione dell'API.

I middleware ricevono `req`, `res` e `next`. Gestire gli errori con middleware finale, validare body e parametri, impostare CORS e protezioni HTTP appropriate. Non fidarsi dei dati del client.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione56) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione58)
