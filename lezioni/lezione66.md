# Decoratori

I decoratori sono funzioni applicate a classi o membri per aggiungere metadati o comportamento. La sintassi e il supporto dipendono dalla versione TypeScript e dal framework.

```typescript
function logClasse<T extends new (...args: any[]) => object>(classe: T): T {
  console.log(classe.name);
  return classe;
}

@logClasse
class Servizio {}
```

Verificare se il progetto usa decoratori legacy o la proposta ECMAScript standard: le semantiche non sono identiche. Evitare decoratori che nascondono troppo comportamento e documentare gli effetti.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione65) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione67)
