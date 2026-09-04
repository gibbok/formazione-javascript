# Caricamento delle risorse

Il browser emette eventi quando documento, immagini, fogli di stile e script vengono caricati o falliscono.

## `DOMContentLoaded` e `load`

```javascript
document.addEventListener("DOMContentLoaded", () => {
  inizializzaInterfaccia();
});

window.addEventListener("load", () => {
  console.log("Tutte le risorse sono disponibili");
});
```

Con `defer` e script modulo il DOM è normalmente pronto prima dell'esecuzione dello script.

## Immagini

```javascript
const immagine = new Image();
immagine.onload = () => console.log("Caricata");
immagine.onerror = () => console.error("Errore");
immagine.src = "/assets/foto.jpg";
```

Usare `loading="lazy"` per immagini non visibili immediatamente e fornire sempre un testo `alt` significativo.

## Risorse fallite

Un listener `error` segnala problemi, ma non permette di recuperare una risorsa senza una strategia alternativa. Gestire timeout, fallback e messaggi comprensibili.

## Riepilogo

Scegliere l'evento in base alla risorsa: `DOMContentLoaded` per il DOM, `load` per la pagina completa e `error` per fallback specifici.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione38) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione40)
