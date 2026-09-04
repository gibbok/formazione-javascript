# I form

Un form raccoglie dati tramite `input`, `select`, `textarea`, `button` e altri controlli. Gli attributi semantici permettono al browser di validare e compilare i dati.

```html
<form id="registrazione">
  <label for="email">Email</label>
  <input id="email" name="email" type="email" required>
  <button type="submit">Invia</button>
</form>
```

## Validazione nativa

`required`, `minlength`, `maxlength`, `min`, `max`, `pattern` e i tipi dell'input definiscono vincoli leggibili dal browser.

```javascript
const form = document.querySelector("form");

form.addEventListener("submit", evento => {
  if (!form.checkValidity()) {
    evento.preventDefault();
    form.reportValidity();
  }
});
```

## FormData

```javascript
const dati = new FormData(form);
const oggetto = Object.fromEntries(dati.entries());
```

Checkbox e campi multipli possono avere più valori: usare `getAll` quando necessario.

## Accessibilità

Ogni controllo deve avere un `label`, messaggi associati con `aria-describedby` e focus visibile. Non usare placeholder come unica etichetta.

## Riepilogo

Il browser offre una base solida per i form. Validare anche lato server e non fidarsi mai dei dati ricevuti dal client.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione37) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione39)
