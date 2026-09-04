# Eventi del mouse

Gli eventi principali del mouse sono `click`, `dblclick`, `contextmenu`, `mousedown`, `mouseup`, `mousemove`, `mouseover` e `mouseout`.

```javascript
area.addEventListener("click", evento => {
  console.log(evento.clientX, evento.clientY);
});

area.addEventListener("contextmenu", evento => {
  evento.preventDefault();
  mostraMenu(evento.clientX, evento.clientY);
});
```

`clientX` e `clientY` sono coordinate nella viewport; `pageX` e `pageY` includono lo scrolling. `button` identifica il pulsante del mouse.

## Mouseover e mouseenter

`mouseover` e `mouseout` attraversano anche gli elementi figli e generano più notifiche. `mouseenter` e `mouseleave` non propagano questi passaggi e sono spesso più semplici per un effetto su un contenitore.

## Movimento e prestazioni

`mousemove` può produrre moltissimi eventi. Per animazioni usare `requestAnimationFrame` e aggiornare il DOM al massimo una volta per fotogramma.

## Riepilogo

Scegliere l'evento in base all'interazione e non affidarsi solo al mouse: i controlli importanti devono funzionare anche con tastiera e tecnologie assistive.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione34) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione36)
