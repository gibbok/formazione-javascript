# Ricerca degli elementi

Il DOM offre metodi diversi per trovare gli elementi. La scelta dipende dal selettore e dal numero di nodi attesi.

## Selettori comuni

```javascript
const titolo = document.getElementById("titolo");
const paragrafi = document.getElementsByTagName("p");
const elementi = document.getElementsByClassName("scheda");
```

I metodi `getElementsBy*` restituiscono collezioni spesso live, che si aggiornano quando cambia il DOM.

## `querySelector` e `querySelectorAll`

```javascript
const primo = document.querySelector("main .scheda");
const tutte = document.querySelectorAll("main .scheda");
```

`querySelector` restituisce il primo elemento o `null`; `querySelectorAll` restituisce una NodeList statica.

```javascript
document.querySelectorAll("button").forEach(button => {
  button.disabled = false;
});
```

Usare selettori specifici e controllare `null` prima di accedere alle proprietà.

## Selettori sicuri

Per un id ricevuto dall'esterno, `CSS.escape()` può evitare che caratteri speciali alterino il selettore. Non concatenare input non fidato in selettori o HTML senza validazione.

## Riepilogo

`getElementById` è semplice per un id, mentre i selettori CSS offrono maggiore flessibilità. Distinguere collezioni live e statiche evita risultati inattesi.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione26) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione28)
