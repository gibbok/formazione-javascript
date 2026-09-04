# Moduli TypeScript

TypeScript usa la sintassi dei moduli ECMAScript e controlla i tipi tra file.

```typescript
// matematica.ts
export function somma(a: number, b: number): number {
  return a + b;
}
```

```typescript
import { somma } from "./matematica.js";
```

Con alcuni bundler l'import sorgente può usare `.ts`, mentre i browser eseguono il `.js` compilato: seguire la configurazione del progetto. `tsconfig.json` definisce target, moduli, strictness, output e alias.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione64) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione66)
