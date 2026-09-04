# Classi in TypeScript

TypeScript aggiunge tipi a proprietà, costruttori e metodi delle classi.

```typescript
class Conto {
  private saldo: number;

  constructor(saldoIniziale: number) {
    this.saldo = saldoIniziale;
  }

  deposita(importo: number): void {
    this.saldo += importo;
  }

  get totale(): number {
    return this.saldo;
  }
}
```

`public`, `private` e `protected` controllano l'accesso durante la compilazione. I modificatori `readonly`, `abstract`, `implements` ed `extends` descrivono invarianti e contratti. La privacy TypeScript non è automaticamente una protezione runtime; per quella usare campi JavaScript `#`.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione63) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione65)
