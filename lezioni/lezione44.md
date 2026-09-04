# WebSocket

WebSocket mantiene una connessione bidirezionale tra browser e server, utile per chat, notifiche e dati in tempo reale.

```javascript
const socket = new WebSocket("wss://example.com/socket");

socket.addEventListener("open", () => socket.send(JSON.stringify({ tipo: "ping" })));
socket.addEventListener("message", evento => console.log(JSON.parse(evento.data)));
socket.addEventListener("error", console.error);
socket.addEventListener("close", () => console.log("Connessione chiusa"));
```

Usare `wss` in produzione. Gestire riconnessione, backoff, autenticazione, messaggi non validi e chiusura della pagina. Validare sempre i dati ricevuti: WebSocket non garantisce che il peer sia affidabile.

## Riepilogo

WebSocket è persistente e bidirezionale, ma richiede un protocollo applicativo per formato, versioni, errori e riconnessioni.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione43) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione45)
