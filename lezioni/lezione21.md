# Gestione degli errori

Gli errori possono dipendere dalla sintassi, dai dati ricevuti o dall'ambiente: un file può mancare, una risposta può essere invalida o un input può non rispettare le regole attese. Gestirli significa prevedere il caso, mantenere un messaggio utile e decidere se recuperare o propagare l'errore.

## Tipi di errore

- `SyntaxError`: sintassi non valida;
- `ReferenceError`: variabile non disponibile;
- `TypeError`: operazione incompatibile con il valore;
- `RangeError`: valore fuori dall'intervallo valido.

```javascript
// const = 1;                // SyntaxError
// console.log(inesistente); // ReferenceError
// null.toString();          // TypeError
```

## `throw`

`throw` interrompe il flusso e trasferisce il controllo al primo `catch` disponibile:

```javascript
function dividi(a, b) {
  if (b === 0) {
    throw new Error("Il divisore non può essere zero");
  }

  return a / b;
}
```

È preferibile lanciare `Error` o una sua sottoclasse, non stringhe, perché gli oggetti errore conservano `name`, `message` e lo stack.

## `try...catch...finally`

```javascript
try {
  const dati = JSON.parse('{"nome":"Ada"}');
  console.log(dati.nome);
} catch (errore) {
  console.error("JSON non valido:", errore.message);
} finally {
  console.log("Operazione terminata");
}
```

`finally` viene eseguito in ogni caso ed è utile per chiudere risorse o nascondere un indicatore di caricamento. Un `return` dentro `finally` può nascondere un errore e va evitato.

## Rilanciare un errore

Un livello può aggiungere contesto e rilanciare l'errore:

```javascript
function leggiConfigurazione(testo) {
  try {
    return JSON.parse(testo);
  } catch (errore) {
    throw new Error("Configurazione non leggibile", { cause: errore });
  }
}
```

`cause` conserva la causa originale senza perdere il dettaglio tecnico.

## Errori personalizzati

```javascript
class ValidazioneError extends Error {
  constructor(messaggio, campo) {
    super(messaggio);
    this.name = "ValidazioneError";
    this.campo = campo;
  }
}

function validaNome(nome) {
  if (typeof nome !== "string" || !nome.trim()) {
    throw new ValidazioneError("Il nome è obbligatorio", "nome");
  }
}
```

Il chiamante può distinguere gli errori con `instanceof`, ma dovrebbe prevedere anche un fallback per errori sconosciuti.

## Validare prima di usare

La validazione è diversa dalla gestione di un'eccezione: controllare un input atteso prima di usarlo evita di usare `try...catch` come normale condizione.

```javascript
function creaUtente(dati) {
  if (!dati || typeof dati.nome !== "string") {
    throw new TypeError("dati.nome deve essere una stringa");
  }

  return { nome: dati.nome.trim() };
}
```

## Errori asincroni

Un `try...catch` cattura un errore asincrono quando la Promise viene attesa con `await` nello stesso blocco:

```javascript
async function carica(url) {
  try {
    const risposta = await fetch(url);
    if (!risposta.ok) throw new Error(`HTTP ${risposta.status}`);
    return await risposta.json();
  } catch (errore) {
    console.error("Richiesta fallita", errore);
    throw errore;
  }
}
```

`fetch` rifiuta la Promise per errori di rete, ma non automaticamente per status HTTP come 404 o 500: bisogna controllare `response.ok`.

## Buone pratiche

- Gestire solo gli errori che si sanno trattare.
- Non mostrare all'utente stack trace o dati sensibili.
- Registrare contesto sufficiente per il debugging.
- Liberare risorse in `finally`.
- Validare i dati ai confini dell'applicazione.
- Non usare eccezioni per sostituire condizioni normali.

## Riepilogo

`throw` produce un errore, `try` contiene l'operazione rischiosa, `catch` la gestisce e `finally` esegue la pulizia. Errori personalizzati, validazione e propagazione con contesto rendono il programma più affidabile.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione20) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione22)
