# NPM

NPM è il registry e il client per pacchetti JavaScript. `package.json` descrive progetto, script e dipendenze.

```bash
npm init -y
npm install express
npm install --save-dev eslint
npm run test
```

`dependencies` servono a runtime, `devDependencies` allo sviluppo. Il lockfile fissa l'albero installato e va versionato. Non installare pacchetti senza valutarne manutenzione, licenza e sicurezza.

## `package.json` in dettaglio

Un progetto reale descrive nome, versione, entry point, script e dipendenze:

```json
{
  "name": "server-esempio",
  "version": "1.0.0",
  "type": "module",
  "main": "src/server.js",
  "scripts": {
    "start": "node src/server.js",
    "dev": "node --watch src/server.js",
    "test": "node --test"
  },
  "engines": {
    "node": ">=20"
  }
}
```

`main` indica l'entry point di un pacchetto; negli strumenti moderni possono esistere anche `exports`, `bin`, `files` e condizioni per browser o Node.

## Versioni e lockfile

Una versione come `^1.4.2` consente aggiornamenti compatibili secondo semver, mentre `~1.4.2` limita gli aggiornamenti alla versione patch. `package-lock.json` registra le versioni concrete e gli hash: in CI usare `npm ci`, che installa esattamente dal lockfile e fallisce se è incoerente.

Comandi utili:

```bash
npm list --depth=0
npm outdated
npm audit
npm uninstall express
```

Non usare `npm audit fix --force` alla cieca: può introdurre breaking change. Leggere l'avviso e aggiornare con test.

## Pacchetti locali e `npx`

`npm link` collega un pacchetto locale durante lo sviluppo. `npx` esegue un binario del progetto senza installarlo globalmente:

```bash
npx tsc --noEmit
```

Preferire binari locali e script versionati rispetto a installazioni globali non riproducibili.

## Pubblicazione e sicurezza

Prima di pubblicare controllare `files`, licenza, segreti e file inclusi. Eseguire installazioni con una versione Node dichiarata e non eseguire automaticamente script di pacchetti non fidati.

## Pacchetti e Express

Express è una dipendenza di produzione quando il server la importa durante l'esecuzione:

```bash
npm install express
npm install --save-dev nodemon
```

Il comando aggiorna `package.json` e il lockfile. Non modificare manualmente versioni isolate senza poi rigenerare il lockfile con NPM.

Una configurazione tipica può definire script distinti:

```json
{
  "scripts": {
    "start": "node src/server.js",
    "dev": "nodemon src/server.js",
    "test": "node --test",
    "lint": "eslint ."
  }
}
```

`npm run` mostra gli script disponibili. Gli script ricevono le variabili d'ambiente del processo; per valori sensibili usare il sistema di configurazione dell'ambiente, non il file JSON.

## Installazione riproducibile

In sviluppo `npm install` può aggiornare il lockfile secondo i vincoli semver. In CI e produzione usare `npm ci`: rimuove `node_modules`, installa esattamente quanto indicato dal lockfile e fallisce se `package.json` e lockfile non coincidono.

## Dipendenze transitive

Installare Express porta con sé altre dipendenze. `npm ls` mostra l'albero, mentre `npm audit` confronta le versioni con vulnerabilità note. Un audit non dimostra che il codice sia sicuro: valutare anche configurazione, input, autorizzazione e aggiornamenti.

## Pacchetto e applicazione

Una libreria dovrebbe dichiarare un'API pubblica con `exports`, includere solo i file necessari con `files` e indicare `engines` supportate. Un'applicazione privata può avere un entry point e script, ma non ha bisogno di pubblicare il pacchetto nel registry.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione54) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione56)
