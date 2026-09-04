# Includere JavaScript in un documento HTML

In questo articolo esamineremo come includere JavaScript in un documento HTML utilizzando il tag `<script>`. Il tag `<script>` è utilizzato per includere codice JavaScript in un documento HTML e può essere utilizzato per creare siti web interattivi e dinamici.

## Il tag “script”

Il tag `<script>` è utilizzato per includere codice JavaScript in un documento HTML. Il tag `<script>` può essere utilizzato all'interno dell'elemento `<head>` o dell'elemento `<body>` di un documento HTML.

Ecco un esempio di utilizzo del tag `<script>`:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Document</title>
  <script>
    // Codice JavaScript
    console.log("Ciao mondo!");
  </script>
</head>
<body>
  <h1>Benvenuto!</h1>
  <script>
    // Codice JavaScript
    console.log("Ciao mondo!");
  </script>
</body>
</html>
```

In questo esempio, il tag `<script>` è utilizzato per includere codice JavaScript all'interno dell'elemento `<head>` e dell'elemento `<body>` di un documento HTML.

## Attributi del tag “script”

Il tag `<script>` supporta diversi attributi che possono essere utilizzati per specificare il comportamento del codice JavaScript incluso. Alcuni degli attributi più comuni del tag `<script>` includono:

- `src`: specifica l'URL di un file esterno contenente codice JavaScript.
- `type`: specifica il tipo di contenuto del codice JavaScript. Il valore predefinito è "text/javascript".
- `defer`: specifica che il codice JavaScript deve essere eseguito dopo il caricamento del documento HTML.
- `async`: specifica che il codice JavaScript può essere eseguito in modo asincrono rispetto al caricamento del documento HTML.

Ecco un esempio di utilizzo degli attributi del tag `<script>`:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Document</title>
  <script src="script.js" type="text/javascript" defer></script>
</head>
<body>
  <h1>Benvenuto!</h1>
  <script src="script.js" type="text/javascript" async></script>
</body>
</html>
```

In questo esempio, il tag `<script>` è utilizzato per includere codice JavaScript da un file esterno utilizzando l'attributo `src`. Gli attributi `type`, `defer` e `async` sono utilizzati per specificare il tipo di contenuto del codice JavaScript e il comportamento di esecuzione.

### `defer` e `async` a confronto

La posizione dello script e i suoi attributi determinano quando il codice può essere eseguito:

- uno script normale nel `<head>` blocca il parsing dell'HTML mentre viene scaricato ed eseguito;
- `defer` scarica lo script in parallelo, lo esegue dopo il parsing e mantiene l'ordine tra più script differiti;
- `async` scarica in parallelo ed esegue appena il download termina, quindi l'ordine tra più script non è garantito;
- gli script `type="module"` sono differiti automaticamente e supportano `import` ed `export`.

```html
<script src="config.js" defer></script>
<script src="app.js" defer></script>
```

In questo esempio `app.js` può usare ciò che `config.js` ha inizializzato, perché gli script `defer` vengono eseguiti nell'ordine in cui compaiono.

## Supporto del tag “script” nei browser

Il tag `<script>` è supportato da tutti i principali browser web, tra cui Chrome, Firefox, Safari e Edge. Il tag `<script>` è utilizzato per includere codice JavaScript in un documento HTML e può essere utilizzato per creare siti web interattivi e dinamici.

## Script esterni

I file JavaScript possono essere inclusi in un documento HTML utilizzando il tag `<script>` con l'attributo `src`. Ad esempio:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Document</title>
  <script src="script.js" type="text/javascript"></script>
</head>
<body>
  <h1>Benvenuto!</h1>
</body>
</html>
```

In questo esempio, il file `script.js` contiene il codice JavaScript che verrà eseguito quando il documento HTML viene caricato nel browser.

Nota:

Se src è impostato, il contenuto all’interno di script verrà ignorato!

Esempio:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Document</title>
  <script src="script.js" type="text/javascript">
    console.log("Questo codice verrà ignorato!"); // il contenuto viene ignorato, perché src è impostato
  </script>
</head>
<body>
  <h1>Benvenuto!</h1>
</body>
</html>
```

In questo esempio, il codice all'interno del tag `<script>` viene ignorato perché l'attributo `src` è impostato su "script.js".

## Percorsi e sicurezza

Il valore di `src` è un URL relativo o assoluto e viene risolto rispetto all'URL del documento HTML. Un file `js/app.js` non è lo stesso file di `./app.js` se la struttura delle cartelle è diversa. In produzione è inoltre buona pratica servire gli script tramite HTTPS e usare una Content Security Policy adeguata.

Quando il codice deve accedere al DOM, `defer` o `type="module"` evitano di dover aspettare manualmente l'evento `DOMContentLoaded` nella maggior parte dei casi. Se invece lo script viene inserito alla fine del `<body>`, gli elementi precedenti sono già stati analizzati, ma le dipendenze tra script vanno comunque gestite esplicitamente.

### Conclusione

In questo articolo abbiamo esaminato il tag `<script>` e come può essere utilizzato per includere codice JavaScript in un documento HTML. Abbiamo esaminato anche gli attributi del tag `<script>` e come possono essere utilizzati per specificare il comportamento del codice JavaScript incluso. Infine, abbiamo esaminato come includere file JavaScript esterni in un documento HTML utilizzando il tag `<script>`. Il tag `<script>` è uno strumento potente che consente di aggiungere interattività e dinamicità ai siti web e di creare esperienze utente coinvolgenti.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione4)
