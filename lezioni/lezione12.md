# L'istruzione "switch"

In JavaScript, l'istruzione `switch` viene utilizzata per eseguire un blocco di codice diverso in base al valore di una variabile. L'istruzione `switch` è simile a una serie di istruzioni `if...else if...else`, ma è più leggibile e concisa quando si devono gestire più casi.

## Sintassi

La sintassi dell'istruzione `switch` è la seguente:

```javascript
switch (espressione) {
  case valore1:
    // blocco di codice
    break;
  case valore2:
    // blocco di codice
    break;
  case valore3:
    // blocco di codice
    break;
  default:
    // blocco di codice
}
```

- Il valore di `epressione` viene controllato utilizzando l’uguaglianza stretta con i valori dei blocchi case (`valore1` e `valole2` nell’esempio sopra).
- Se l’uguaglianza viene trovata, `switch` inizia ad eseguire il codice partendo dal corrispondente blocco `case`, fino al `break` più vicino (oppure fino alla fine dello `switch`).
- Se non viene trovata nessuna uguaglianza allora viene eseguito il codice del blocco `default` (se presente).

### Esempio

```javascript
let a = 2 + 2;

switch (a) {
  case 3:
    alert( 'Too small' );
    break;
  case 4:
    alert( 'Exactly!' );
    break;
  case 5:
    alert( 'Too big' );
    break;
  default:
    alert( "I don't know such values" );
}
```

Qui lo `switch` inizia confrontando a con il primo `case`, il cui valore è 3. Non vi è corrispondenza.
Poi valuta 4. C’è una corrispondenza, quindi l’esecuzione inizia da `case` 4 fino al `break` più vicino.
Se non c’è nessun `break` l’esecuzione procede al prossimo `case`.

## Raggruppare i casi

Spesso è necessario eseguire lo stesso blocco di codice per più casi. In questo caso, è possibile raggruppare i casi e omettere i `break` tra di essi. Ecco un esempio:

```javascript
let a = 2 + 2;

switch (a) {
  case 4:
    alert('Right!');
    break;

  case 3: // (*) raggruppamento dei casi
  case 5:
    alert('Wrong!');
    alert("Why don't you take a math class?");
    break;

  default:
    alert('The result is strange. Really.');
}
```

In questo esempio, se `a` è 3 o 5, verrà visualizzato un messaggio "Wrong!" e "Why don't you take a math class?". Se `a` è 4, verrà visualizzato un messaggio "Right!". In tutti gli altri casi, verrà visualizzato un messaggio "The result is strange. Really.".

Il confronto di `switch` è stretto: `switch ("1")` non entra in `case 1`. Il `break` impedisce il fall-through, cioè l'esecuzione dei casi successivi. Il fall-through intenzionale è leggibile quando i casi sono raggruppati, ma va terminato con un `break` o con un `return`.

Quando i casi dipendono da intervalli, più condizioni o condizioni composte, `if...else` può comunicare meglio l'intento. `switch` è particolarmente adatto a un insieme finito di valori, come stati o comandi.

## Valori con espressioni

Gli `case` possono contenere espressioni arbitrarie di JavaScript. Ad esempio:

```javascript
let a = 2 + 2;

switch (a) {
  case 1 + 3:
    alert("This works too!");
    break;
  case 2 * 2:
    alert("Also this!");
    break;
  default:
    alert("Not matched.");
}
```

In questo esempio, l'espressione `2 + 2` viene valutata e assegnata a `a`, quindi a vale `4`.

Lo switch confronta a con ogni valore nei case:

- `1 + 3` viene valutato come `4`, quindi il codice di quel `case` viene eseguito e viene mostrato l'alert "This works too!".
- Il secondo `case` (`2 * 2`) avrebbe anch'esso il valore `4`, ma l'esecuzione si ferma al primo `break`.
- Se `a` fosse stato un altro numero, sarebbe stato eseguito il blocco `default`.

Questo dimostra che nei case è possibile usare espressioni, non solo valori statici.

### Conclusioni

L'istruzione `switch` è utile quando si devono gestire più casi in modo più leggibile e conciso rispetto a una serie di istruzioni `if...else if...else`. È possibile utilizzare `case` per confrontare valori o espressioni e `default` per gestire i casi non corrispondenti.

#### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione13)
