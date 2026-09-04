# AJAX

In jQuery AJAX indica richieste asincrone senza ricaricare la pagina. `$.ajax` restituisce una jqXHR, compatibile con Promise.

```javascript
$.ajax({
  url: "/api/utenti",
  method: "GET",
  dataType: "json",
  timeout: 5000
})
  .done(utenti => console.log(utenti))
  .fail((xhr, stato, errore) => console.error(stato, errore))
  .always(() => $(".loading").hide());
```

## POST e dati

```javascript
$.ajax({
  url: "/api/utenti",
  method: "POST",
  contentType: "application/json",
  data: JSON.stringify({ nome: "Ada" })
});
```

Controllare status, formato e messaggi del server. `$.ajaxSetup` può impostare opzioni comuni, ma configurazioni globali nascoste rendono difficile il debugging.

## CORS e sicurezza

Le richieste cross-origin richiedono autorizzazione CORS. Non inserire token o dati sensibili nei parametri URL senza motivo. Il server deve autenticare, autorizzare e validare ogni richiesta.

Per nuovo codice valutare `fetch` e `async/await`; jQuery resta utile quando il progetto esistente dipende dalla sua API.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione75) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione77)
