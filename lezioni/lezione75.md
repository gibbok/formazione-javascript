# Effetti

jQuery offre effetti pronti come `show`, `hide`, `fadeIn`, `fadeOut`, `slideDown` e `slideUp`.

```javascript
$(".messaggio").fadeIn(200).delay(1000).fadeOut(200);
```

Le animazioni restituiscono una coda. `stop(true, true)` interrompe la coda precedente quando un evento può essere attivato rapidamente:

```javascript
$(".menu").stop(true, true).slideToggle(200);
```

## `animate`

```javascript
$(".barra").animate({ width: "80%", opacity: 0.8 }, 400);
```

Animare soprattutto proprietà trasformabili e opacità. Per accessibilità rispettare `prefers-reduced-motion` e offrire una versione senza movimento.

## CSS moderno

Per transizioni complesse è spesso meglio aggiungere o rimuovere una classe e lasciare l'animazione a CSS. Evitare di animare continuamente proprietà che provocano layout costoso.

## Riepilogo

Gli effetti jQuery sono semplici per interazioni legacy; controllare le code, le prestazioni e la riduzione del movimento.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione74) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione76)
