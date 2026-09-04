# Introduzione a TypeScript

TypeScript è un superset di JavaScript che aggiunge tipizzazione statica e strumenti di analisi. Il compilatore controlla il codice e produce JavaScript eseguibile dal browser o da Node.js.

```typescript
function saluta(nome: string): string {
  return `Ciao, ${nome}`;
}
```

I tipi aiutano a trovare errori prima dell'esecuzione, ma vengono rimossi durante la compilazione: non sostituiscono la validazione dei dati ricevuti a runtime.

```bash
npm install --save-dev typescript
npx tsc --init
```

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione61)
