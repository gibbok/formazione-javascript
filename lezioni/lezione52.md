# Il modulo HTTP

Il modulo `node:http` permette di creare server HTTP senza framework.

```javascript
import http from "node:http";

const server = http.createServer((req, res) => {
  res.writeHead(200, { "Content-Type": "application/json" });
  res.end(JSON.stringify({ ok: true }));
});

server.listen(3000, "127.0.0.1");
```

## Richiesta e risposta

`req.method` contiene il metodo HTTP, `req.url` il percorso ricevuto e `req.headers` le intestazioni. La risposta deve essere chiusa con `res.end()`:

```javascript
const server = http.createServer((req, res) => {
  const url = new URL(req.url, `http://${req.headers.host}`);

  if (req.method === "GET" && url.pathname === "/api/saluto") {
    res.writeHead(200, { "Content-Type": "application/json; charset=utf-8" });
    res.end(JSON.stringify({ messaggio: "Ciao" }));
    return;
  }

  res.writeHead(404, { "Content-Type": "application/json" });
  res.end(JSON.stringify({ errore: "Risorsa non trovata" }));
});
```

Usare `URL` invece di manipolare `req.url` con `split`: gestisce correttamente path, query string ed encoding.

## Leggere il body

Il body è uno stream. Va raccolto a pezzi e limitato per evitare richieste eccessivamente grandi:

```javascript
function leggiBody(req, limite = 1_000_000) {
  return new Promise((resolve, reject) => {
    let corpo = "";

    req.setEncoding("utf8");
    req.on("data", pezzo => {
      corpo += pezzo;
      if (corpo.length > limite) {
        reject(new Error("Body troppo grande"));
        req.destroy();
      }
    });
    req.on("end", () => resolve(corpo));
    req.on("error", reject);
  });
}
```

Il server deve verificare `Content-Type` prima di chiamare `JSON.parse` e gestire il caso di JSON non valido con status `400`.

## Routing manuale

Un server senza framework deve associare metodo e percorso a un handler, impostare status code coerenti e distinguere almeno `200`, `201`, `204`, `400`, `404` e `500`. Per molti endpoint questa logica diventa difficile da mantenere: Express o un altro router riduce il codice ripetitivo.

## Server e lifecycle

```javascript
const server = http.createServer(handler);
server.on("error", console.error);
server.listen({ port: 3000, host: "127.0.0.1" }, () => {
  console.log("Server attivo");
});

process.on("SIGTERM", () => {
  server.close(() => process.exit(0));
});
```

In produzione usare un reverse proxy per TLS, timeout, compressione e limiti aggiuntivi. Non esporre messaggi di errore interni al client.

Controllare sempre metodo, URL e input. Impostare status code, content type e limiti del body. In produzione usare HTTPS tramite proxy o certificati configurati correttamente.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione51) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione53)
