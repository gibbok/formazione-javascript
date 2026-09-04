# MySQL

MySQL è un database relazionale basato su tabelle, relazioni e SQL.

```javascript
import mysql from "mysql2/promise";

const connessione = await mysql.createConnection({
  uri: process.env.DATABASE_URL
});

const [righe] = await connessione.execute(
  "SELECT * FROM utenti WHERE id = ?",
  [1]
);
```

Usare query parametrizzate per prevenire SQL injection, pool di connessioni per server concorrenti e transazioni quando più modifiche devono essere atomiche. Chiudere il pool durante lo shutdown.

## Pool di connessioni

Un pool riusa connessioni e limita il numero di accessi simultanei al database:

```javascript
const pool = mysql.createPool({
  uri: process.env.DATABASE_URL,
  connectionLimit: 10
});

const [righe] = await pool.execute(
  "SELECT id, nome FROM utenti WHERE attivo = ? LIMIT ?",
  [true, 20]
);
```

I valori vanno passati come parametri, mai concatenati nella stringa SQL. Per nomi di colonne o ordinamenti dinamici usare una whitelist, perché i parametri non sostituiscono identificatori SQL.

## CRUD e transazioni

```javascript
const [risultato] = await pool.execute(
  "INSERT INTO utenti (nome, email) VALUES (?, ?)",
  ["Ada", "ada@example.com"]
);
```

Quando più query devono riuscire insieme usare una connessione dedicata:

```javascript
const connessione = await pool.getConnection();
try {
  await connessione.beginTransaction();
  await connessione.execute("UPDATE conti SET saldo = saldo - ? WHERE id = ?", [10, 1]);
  await connessione.execute("UPDATE conti SET saldo = saldo + ? WHERE id = ?", [10, 2]);
  await connessione.commit();
} catch (errore) {
  await connessione.rollback();
  throw errore;
} finally {
  connessione.release();
}
```

## Schema e relazioni

Le tabelle definiscono colonne, tipi, vincoli e relazioni. `PRIMARY KEY` identifica una riga; `FOREIGN KEY` collega tabelle; `UNIQUE`, `NOT NULL` e `CHECK` proteggono l'integrità anche se l'applicazione contiene bug.

Usare migration versionate per modificare lo schema in modo riproducibile. Evitare di affidare la consistenza solo alla validazione JavaScript.

## Prestazioni ed errori

Creare indici per le query reali, ma non indicizzare ogni colonna. Selezionare solo i campi necessari, paginare risultati grandi e controllare i piani con `EXPLAIN`. Gestire timeout, perdita di connessione, deadlock e violazioni di vincoli senza restituire dettagli interni al client.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione58) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione60)
