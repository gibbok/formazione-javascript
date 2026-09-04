# Eventi dei form

I form generano eventi `submit`, `input`, `change`, `focus` e `blur`.

## Submit

```javascript
form.addEventListener("submit", evento => {
  evento.preventDefault();
  const dati = new FormData(form);
  console.log(dati.get("email"));
});
```

Gestire `submit` sul form funziona anche quando l'utente invia con Enter. `FormData` legge i controlli che hanno un attributo `name`.

## Input e change

`input` scatta a ogni modifica, mentre `change` normalmente scatta quando il valore viene confermato o il controllo perde il focus. Per validazione in tempo reale usare input con messaggi non invasivi.

```javascript
email.addEventListener("input", () => {
  email.setCustomValidity(email.validity.typeMismatch ? "Email non valida" : "");
});
```

## Focus

`focus` e `blur` non propagano come gli eventi comuni; `focusin` e `focusout` sì. Non rimuovere l'indicatore di focus senza sostituirlo con uno visibile.

## Riepilogo

Lasciare che il browser esegua la validazione nativa quando possibile e aggiungere messaggi chiari. Non affidarsi solo alla validazione client: il server deve sempre verificare i dati.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione35) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione37)
