# Aspetti avanzati del browser

Il browser esegue JavaScript sul thread principale insieme a rendering e gestione degli eventi. Codice troppo costoso può bloccare input e animazioni.

## `requestAnimationFrame`

```javascript
function anima() {
  elemento.style.transform = `translateX(${posizione++}px)`;
  requestAnimationFrame(anima);
}
```

Usarlo per aggiornamenti visivi. Per lavoro non visivo usare task brevi o Web Worker.

## Observer API

`IntersectionObserver` osserva la visibilità senza calcolare continuamente coordinate; `MutationObserver` rileva cambiamenti nel DOM; `ResizeObserver` reagisce alle dimensioni di un elemento.

```javascript
const observer = new IntersectionObserver(entries => {
  for (const entry of entries) {
    if (entry.isIntersecting) entry.target.classList.add("visibile");
  }
});
observer.observe(document.querySelector("section"));
```

## Prestazioni e sicurezza

Ridurre letture e scritture alternate del layout, delegare eventi quando possibile e pulire listener e observer. Evitare `eval`, HTML non sanificato e dati sensibili negli URL.

## Riepilogo

Interfacce fluide richiedono lavoro breve sul main thread, osservatori adatti al problema e attenzione a sicurezza e risorse.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione39) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione41)
