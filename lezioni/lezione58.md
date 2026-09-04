# MongoDB

MongoDB è un database documentale. I dati sono documenti BSON organizzati in collezioni.

```javascript
import { MongoClient } from "mongodb";

const client = new MongoClient(process.env.MONGODB_URI);
await client.connect();
const utenti = client.db("app").collection("utenti");
await utenti.insertOne({ nome: "Ada" });
const risultato = await utenti.find({ nome: "Ada" }).toArray();
```

Creare indici per query frequenti, validare i dati e usare variabili d'ambiente per la connessione. Chiudere il client durante lo shutdown del processo.

## Connessione e pool

Il client va creato e riusato, non aperto per ogni richiesta:

```javascript
const client = new MongoClient(process.env.MONGODB_URI);
await client.connect();

const database = client.db("app");
const utenti = database.collection("utenti");
```

In un server il driver gestisce un pool di connessioni. Gestire `SIGTERM` per chiudere il client quando il processo termina.

## CRUD

```javascript
const creato = await utenti.insertOne({ nome: "Ada", attivo: true });
const utente = await utenti.findOne({ _id: creato.insertedId });

await utenti.updateOne(
 { _id: creato.insertedId },
 { $set: { attivo: false } }
);

await utenti.deleteOne({ _id: creato.insertedId });
```

Non costruire query direttamente da input senza validare tipi e campi consentiti. Un endpoint dovrebbe permettere solo filtri e aggiornamenti esplicitamente definiti.

## Indici e aggregazioni

```javascript
await utenti.createIndex({ email: 1 }, { unique: true });
const attivi = await utenti.find({ attivo: true })
 .sort({ nome: 1 })
 .limit(20)
 .toArray();
```

Gli indici accelerano le letture ma aumentano spazio e costo delle scritture. Analizzare le query con `explain`. Le aggregation pipeline trasformano dati in più fasi, come `$match`, `$group` e `$sort`.

## Modello dei dati e transazioni

MongoDB permette documenti flessibili, ma uno schema esplicito evita dati incoerenti. Embedding è adatto a dati letti insieme e limitati; riferimenti sono preferibili per entità grandi o condivise.

Le transazioni multi-documento richiedono un deployment compatibile e vanno usate quando l'operazione non può essere divisa. Non sostituiscono la progettazione degli indici e dei vincoli.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione57) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione59)
