# Il modulo URL

La classe `URL` analizza e costruisce indirizzi in modo sicuro.

```javascript
const indirizzo = new URL("https://example.com/cerca?q=js&page=2");
console.log(indirizzo.hostname);
console.log(indirizzo.searchParams.get("q"));
indirizzo.searchParams.set("page", "3");
console.log(indirizzo.href);
```

Usare `URL` e `URLSearchParams` invece di manipolare stringhe a mano. Validare protocollo, dominio e parametri quando l'URL proviene dall'esterno.

## Parti di un URL

```javascript
const url = new URL("https://utente:password@example.com:8443/api/utenti?id=42#profilo");

console.log(url.protocol); // https:
console.log(url.hostname); // example.com
console.log(url.port); // 8443
console.log(url.pathname); // /api/utenti
console.log(url.hash); // #profilo
```

`origin` combina protocollo, host e porta. Evitare di loggare URL completi quando possono contenere token, password o dati personali.

## URL relativi

Il costruttore accetta una base per risolvere percorsi relativi:

```javascript
const base = new URL("https://example.com/api/");
const endpoint = new URL("utenti/42", base);
console.log(endpoint.href); // https://example.com/api/utenti/42
```

In Node.js, per costruire un URL a partire da una richiesta HTTP, usare `new URL(req.url, "http://host")` invece di concatenare stringhe.

## Query string

```javascript
const parametri = new URLSearchParams({ ricerca: "node js", pagina: "2" });
parametri.append("tag", "backend");

for (const [chiave, valore] of parametri) {
 console.log(chiave, valore);
}
```

`get` restituisce il primo valore, `getAll` tutti i valori ripetuti. `set` sostituisce, `append` aggiunge e `delete` rimuove. I parametri sono sempre stringhe e devono essere convertiti e validati.

## Validazione degli URL

```javascript
function urlHttpsValido(testo) {
 try {
  const url = new URL(testo);
  return url.protocol === "https:" && url.hostname.endsWith("example.com");
 } catch {
  return false;
 }
}
```

Non usare un controllo testuale come `url.startsWith("https://example.com")`: potrebbe accettare domini come `example.com.attacker.test`.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione53) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione55)
