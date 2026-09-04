# Le tecniche moderne, "use strict"

JavaScript è un linguaggio di programmazione flessibile e potente, ma può anche essere propenso a errori e comportamenti imprevisti. Per mitigare alcuni di questi problemi, è possibile utilizzare la direttiva `"use strict"` per dichiarare che il codice deve essere eseguito in modalità rigorosa.

La modalità rigorosa abilita un sottoinsieme più sicuro e più restrittivo di JavaScript, che aiuta a prevenire errori comuni e comportamenti imprevisti. Ad esempio, la modalità rigorosa richiede che le variabili vengano dichiarate prima di essere utilizzate, impedisce l'uso di parole chiave riservate come identificatori e impone altre restrizioni che possono aiutare a scrivere codice più affidabile.

La modalità rigorosa non è una versione diversa del linguaggio e non sostituisce l'uso di `const` e `let`: modifica alcune regole durante l'esecuzione e trasforma diversi comportamenti silenziosi in errori espliciti.

Per utilizzare la modalità rigorosa, è possibile inserire la direttiva `"use strict"` all'inizio di un file JavaScript o all'inizio di una funzione. Ad esempio:

```javascript
"use strict";

// Codice JavaScript in modalità rigorosa
```

La direttiva è supportata dai browser moderni e fa parte di ECMAScript da molti anni. Nei moduli JavaScript è già attiva, quindi non serve ripeterla.

## Esempio di utilizzo di "use strict"

```javascript
"use strict";

// Dichiarare una variabile senza utilizzare la parola chiave "var"
nome = "Mario"; // Errore in modalità rigorosa
```

Altri casi importanti sono l'assegnazione a una proprietà non scrivibile e l'uso di `this` in una funzione chiamata senza oggetto: in strict mode `this` vale `undefined`, invece dell'oggetto globale. La modalità rigorosa vieta inoltre alcune sintassi legacy come `with` e impedisce di duplicare nomi di parametri in una funzione.

In questo esempio, la direttiva `"use strict"` viene utilizzata per dichiarare che il codice deve essere eseguito in modalità rigorosa. Quando si tenta di assegnare un valore a una variabile senza dichiararla con la parola chiave "var", viene generato un errore in modalità rigorosa.

## Vantaggi di "use strict"

L'utilizzo della direttiva `"use strict"` offre diversi vantaggi, tra cui:

- **Prevenzione di errori comuni**: La modalità rigorosa impone restrizioni che possono prevenire errori comuni e comportamenti imprevisti.
- **Miglioramento delle prestazioni**: Alcune ottimizzazioni del motore JavaScript possono essere abilitate in modalità rigorosa, migliorando le prestazioni del codice.
- **Miglior leggibilità del codice**: La modalità rigorosa richiede una sintassi più rigorosa, che può migliorare la leggibilità del codice e facilitare la manutenzione.
- **Compatibilità futura**: La modalità rigorosa è parte dello standard ECMAScript e può aiutare a garantire la compatibilità con le future versioni di JavaScript.

## Dovremmo utilizzare “use strict”?

La direttiva `"use strict"`, abbiamo detto, serve per scrivere codice JavaScript più affidabile e prevenire errori comuni. Tuttavia, è importante tenere presente che la direttiva `"use strict"` potrebbe non essere supportata in tutti i contesti e potrebbe richiedere attenzione aggiuntiva durante lo sviluppo e il test del codice.

JavaScript moderno supporta, comunque, le “classi” e i “moduli” – delle strutture avanzate del linguaggio (a cui arriveremo più avanti), che abilitano use strict in automatico. Quindi non è necessario inserire la direttiva "use strict" se utilizziamo queste funzionalità.

Per il codice moderno la raccomandazione pratica è usare `const` per i riferimenti che non cambiano, `let` quando devono essere riassegnati e moduli per organizzare il programma. In un file non modulare, la direttiva può ancora essere utile, soprattutto quando si mantiene codice precedente.

### Conclusione

Abbiamo visto come utilizzare la direttiva `"use strict"` per dichiarare che il codice JavaScript deve essere eseguito in modalità rigorosa. La modalità rigorosa abilita un sottoinsieme più sicuro e più restrittivo di JavaScript, che aiuta a prevenire errori comuni e comportamenti imprevisti.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione5)
