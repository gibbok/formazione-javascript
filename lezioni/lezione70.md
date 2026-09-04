# Ambienti di esecuzione

TypeScript controlla il codice in base alle API dell'ambiente: browser, Node.js, Deno, worker e librerie possono avere globali differenti.

## Librerie di tipi

Per il DOM si usa normalmente `lib.dom.d.ts`; per Node.js si installano i tipi del runtime:

```bash
npm install --save-dev @types/node
```

`tsconfig.json` definisce `target`, `module`, `lib`, `moduleResolution`, `strict`, `rootDir` e `outDir`. Il target indica il JavaScript prodotto, non cambia le API disponibili a runtime.

## Dichiarazioni ambientali

Un file `.d.ts` descrive codice esistente senza implementarlo:

```typescript
declare const versioneApp: string;
```

Le dichiarazioni devono corrispondere alla realtà: TypeScript non inserisce automaticamente controlli runtime.

## Riepilogo

Configurare i tipi in base all'ambiente reale, mantenere `strict` attivo quando possibile e ricordare che la compilazione non sostituisce polyfill, validazione o test nel runtime.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione69) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione71)
