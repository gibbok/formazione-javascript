# Manipolazione degli elementi

jQuery offre metodi per contenuto, attributi, proprietà, classi e struttura.

```javascript
const titolo = $("h1");
titolo.text("Nuovo titolo");
titolo.attr("aria-label", "Titolo principale");
titolo.addClass("evidenziato");
```

`text` tratta il contenuto come testo; `html` interpreta markup e non deve ricevere dati non fidati.

## Attributi e proprietà

```javascript
const checkbox = $("#accetto");
checkbox.prop("checked", true);
checkbox.data("id", 42);
```

Usare `prop` per lo stato corrente dei controlli e `attr` per gli attributi HTML. `data` mantiene valori associati all'elemento, ma i dati restano lato client.

## Creare e rimuovere

```javascript
const voce = $("<li>").text("Nuova voce");
$("ul").append(voce);
voce.remove();
```

`append`, `prepend`, `before`, `after`, `wrap` e `empty` modificano la struttura. Per liste grandi costruire il contenuto con attenzione e non inserire HTML non sanificato.

## Riepilogo

Separare contenuto e stile con `text` e `addClass`, usare `prop` per proprietà dinamiche e manipolare il DOM in gruppi quando possibile.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione72) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione74)
