# Introduzione a JavaScript

## Che cos'è JavaScript?

JavaScript è un linguaggio di programmazione ad alto livello, orientato agli oggetti e multi-paradigma. È uno dei tre linguaggi di programmazione standard per il web, insieme a HTML e CSS. JavaScript è un linguaggio interpretato, il che significa che non richiede di essere compilato prima di essere eseguito.

JavaScript è un linguaggio di scripting, il che significa che è stato progettato per essere eseguito all'interno di un altro programma. In questo caso, il programma è il browser web. JavaScript è stato progettato per aggiungere interattività ai siti web. Ad esempio, JavaScript può essere utilizzato per aggiungere effetti di scorrimento, aggiornare parti di una pagina, visualizzare messaggi di avviso o eseguire calcoli.

È utile distinguere tre elementi che spesso vengono confusi:

- **ECMAScript** è la specifica che descrive sintassi e comportamento del linguaggio.
- **JavaScript** è un'implementazione di quella specifica, arricchita dalle API dell'ambiente in cui viene eseguita.
- **Il browser** mette a disposizione API come `document`, `fetch`, `localStorage` e `setTimeout`, che non fanno parte del nucleo ECMAScript.

Per esempio, `Array`, `Promise` e `Map` appartengono al linguaggio, mentre `document.querySelector()` appartiene alle API del browser. Questa distinzione spiega perché lo stesso JavaScript può essere eseguito anche in Node.js, dove `document` non esiste ma sono disponibili API diverse.

Il codice viene eseguito da un **motore JavaScript**. Il motore analizza il testo, lo compila in una forma efficiente e lo esegue. Nei browser moderni questo processo è dinamico: il motore può ottimizzare le parti del programma più utilizzate mentre l'applicazione è in esecuzione.

## Storia di JavaScript

JavaScript è stato creato da Brendan Eich nel 1995. Inizialmente, JavaScript era chiamato Mocha. Successivamente, il nome è stato cambiato in LiveScript e infine in JavaScript. JavaScript è stato progettato per essere un linguaggio di scripting per il web. JavaScript è stato progettato per essere simile a Java, ma con una sintassi più semplice e meno funzionalità.

JavaScript è stato standardizzato nel 1997 con la pubblicazione della prima versione di ECMAScript. ECMAScript è lo standard su cui si basa JavaScript. JavaScript è stato standardizzato per garantire che il linguaggio funzioni in modo coerente su tutti i browser web.

## Caratteristiche di JavaScript

JavaScript ha molte caratteristiche che lo rendono un linguaggio di programmazione popolare per il web. Alcune delle caratteristiche più importanti di JavaScript includono:

- **Facilità di apprendimento**: JavaScript è un linguaggio di programmazione relativamente semplice da imparare. JavaScript ha una sintassi semplice e molti costrutti di alto livello che semplificano la scrittura di codice.

- **Interattività**: JavaScript è un linguaggio di programmazione ad eventi, il che significa che è possibile eseguire codice JavaScript in risposta a determinati eventi. Ad esempio, è possibile eseguire codice JavaScript quando un utente fa clic su un pulsante.

- **Oggetti**: JavaScript è un linguaggio di programmazione orientato agli oggetti, il che significa che è possibile creare oggetti in JavaScript. Gli oggetti in JavaScript sono simili agli oggetti in altri linguaggi di programmazione orientati agli oggetti. Gli oggetti in JavaScript possono avere proprietà e metodi.

- **Multi-paradigma**: JavaScript è un linguaggio di programmazione multi-paradigma, il che significa che supporta più stili di programmazione. Ad esempio, JavaScript supporta la programmazione orientata agli oggetti, la programmazione funzionale e la programmazione imperativa.

- **Interoperabilità**: JavaScript è un linguaggio di programmazione che può essere utilizzato insieme ad altri linguaggi di programmazione. Ad esempio, è possibile utilizzare JavaScript insieme a HTML e CSS per creare siti web interattivi.

- **Portabilità**: JavaScript è un linguaggio di programmazione che può essere eseguito su qualsiasi piattaforma. JavaScript è supportato da tutti i principali browser web, tra cui Chrome, Firefox, Safari e Edge.

### Un primo programma

```javascript
const nome = "Ada";
const messaggio = `Ciao, ${nome}!`;

console.log(messaggio);
```

`const` dichiara un riferimento che non verrà riassegnato, mentre il template literal racchiuso dai backtick permette di inserire espressioni con `${...}`. `console.log()` scrive nella console degli strumenti per sviluppatori e non modifica direttamente la pagina.

### Esempio di codice JavaScript

```javascript
// Creare un oggetto in JavaScript
var persona = {
  nome: "Mario",
  cognome: "Rossi",
  eta: 30,
  saluta: function() {
    return "Ciao, mi chiamo " + this.nome + " " + this.cognome + "!";
  }
};

// Visualizzare un messaggio di saluto
console.log(persona.saluta());
```

Attualmente, JavaScript può essere eseguito non solo nei browser, ma anche nei server web e in altri ambienti che supportano il motore JavaScript (JavaScript engine).

Il browser ha un suo motore JavaScript integrato, chiamato alle volte “JavaScript Virtual Machine”.

Esistono altri motori JavaScript, tra cui:

- V8 – per Chrome e Opera.
- SpiderMonkey – per Firefox.

## Cosa può fare JavaScript a livello browser?

- **Manipolare l'HTML**: JavaScript può cambiare tutti gli elementi HTML di una pagina.
- **Manipolare il CSS**: JavaScript può cambiare lo stile di un elemento HTML.
- **Manipolare gli eventi**: JavaScript può creare azioni in risposta a eventi.
- **Validare i dati**: JavaScript può controllare i dati inseriti in un modulo.
- **Invio di richieste asincrone**: JavaScript può inviare richieste al server senza dover ricaricare la pagina.

## Cosa può fare JavaScript a livello server?

- **Creare server web**: JavaScript può essere utilizzato per creare server web. Ad esempio, Node.js è un ambiente di runtime JavaScript che consente di eseguire JavaScript lato server.
- **Gestire file**: JavaScript può essere utilizzato per leggere e scrivere file su un server.
- **Gestire database**: JavaScript può essere utilizzato per connettersi a un database e gestire i dati.

## Cosa NON può fare JavaScript a livello browser?

Per la sicurezza dell’utente, le possibilità di JavaScript nel browser sono limitate. L’intento è di prevenire che una pagina “maligna” tenti di accedere alle informazioni personali o di danneggiare i dati degli utenti.

Esempi di queste restrizioni possono essere:

JavaScript, in una pagina web, non può leggere o scrivere in qualsiasi file nell’hard disk, né copiare o eseguire programmi. Non ha accesso diretto alle funzioni del sistema operativo.

I moderni browser gli consentono di lavorare con i file, sempre con un accesso limitato e comunque solo se il comando proviene da utente, come il “dropping” di un file nella finestra del browser, o con la selezione tramite il tag `<input>`.

Ci sono anche funzionalità che consentono di interagire con la camera/microfono e altri dispositivi, ma in ogni caso richiedono il permesso esplicito dell’utente. Quindi una pagina con JavaScript abilitato non può attivare la web-cam di nascosto, osservare i nostri comportamenti e inviare informazioni alla CIA.

Pagine o schede diverse generalmente non sono a conoscenza dell’esistenza delle altre. In certi casi, tuttavia, può capitare; ad esempio quando una finestra ne apre un’altra tramite JavaScript. Ma anche in questo caso, il codice JavaScript non può accedere all’altra pagina se non appartiene allo stesso sito (stesso dominio, protocollo o porta).

Questa viene definita la “Same Origin Policy” (“Politica di Appartenenza alla Stessa Origine”). Per poter aggirare questo limite, entrambe le pagine devono contenere uno speciale codice JavaScript che consente di gestire lo scambio di dati.

Questa limitazione è sempre dovuta alla sicurezza dell’utente. Una pagina proveniente da `http://anysite.com` che è stata aperta da un utente, ad esempio, non deve essere in grado di accedere ad un’altra scheda del browser con l’URL `http://gmail.com` e rubarne le informazioni.

JavaScript può facilmente comunicare con il server da cui la pagina proviene. Ma la sua abilità di ricevere dati da altri siti/domini è limitata. Sebbene sia possibile, sono richieste esplicite autorizzazioni (passate tramite HTTP headers) dall’indirizzo remoto. Ancora una volta, una limitazione dovuta alla sicurezza.

## Linguaggi “oltre” JavaScript

La sintassi di JavaScript non soddisfa le necessità di tutti. Alcune persone necessitano di caratteristiche differenti.

Questo è prevedibile, poiché i progetti e i requisiti sono diversi da persona a persona.

Recentemente, per questo motivo, sono nati molti nuovi linguaggi che vengono convertiti in JavaScript prima di essere eseguiti nel browser.

Gli strumenti moderni rendono la conversione molto veloce e pulita, consentendo agli sviluppatori di programmare in un altro linguaggio e di auto-convertirlo under the hood.

Esempi di alcuni linguaggi:

- `CoffeeScript` è un linguaggio che introduce una sintassi semplificata che consente di scrivere codice più leggibile. Amato dagli sviluppatori provenienti da Ruby.
- `TypeScript` si occupa di aggiungere la “tipizzazione”, per semplificare lo sviluppo e supportare sistemi più complessi. E’ stato sviluppato da Microsoft.
- `Flow` anche’esso aggiunge la tipizzazione dei dati, ma in un modo differente. Sviluppato da Facebook.
- `Dart` è un linguaggio autonomo che possiede il suo motore, che esegue in ambienti esterni al browser (come mobile apps). E’ stato introdotto da Google come alternativa a JavaScript, ma attualmente i browser richiedono la conversione in JavaScript, proprio come i precedenti.
- `Brython` è un transpiler, scritto in Python, che consente di scrivere applicazioni in quest’ultimo senza utilizzare JavaScript.
- `Kotlin` è un moderno, conciso e sicuro linguaggio di programmazione mirato ai browsers o a Node.

### Come studiare JavaScript

Un programma JavaScript può essere osservato su tre livelli: i dati che riceve, le trasformazioni che applica e gli effetti che produce. Separare questi livelli rende più semplice individuare gli errori. Conviene inoltre provare gli esempi nella console del browser, modificare un valore alla volta e leggere il risultato con `console.log()`.

### Conclusione

JavaScript è un linguaggio di programmazione ad alto livello, orientato agli oggetti e multi-paradigma. JavaScript è stato progettato per essere eseguito all'interno di un browser web e per aggiungere interattività ai siti web. JavaScript è un linguaggio di scripting, il che significa che è stato progettato per essere eseguito all'interno di un altro programma. JavaScript è stato standardizzato nel 1997 con la pubblicazione della prima versione di ECMAScript. JavaScript ha molte caratteristiche che lo rendono un linguaggio di programmazione popolare per il web, tra cui facilità di apprendimento, interattività, oggetti, multi-paradigma, interoperabilità e portabilità. JavaScript può essere utilizzato per manipolare l'HTML, il CSS e gli eventi di una pagina web. JavaScript può anche essere utilizzato per creare server web, gestire file e gestire database. JavaScript ha alcune limitazioni a livello browser per garantire la sicurezza dell'utente, ma può essere esteso con linguaggi come CoffeeScript, TypeScript, Flow, Dart, Brython e Kotlin.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione2)
