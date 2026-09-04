# Tipi di base

TypeScript offre `string`, `number`, `boolean`, array, tuple, `null`, `undefined`, `unknown`, `any`, `void` e `never`.

```typescript
const nome: string = "Ada";
let eta: number = 36;
const attivo: boolean = true;
const numeri: number[] = [1, 2, 3];
const coppia: [string, number] = ["Ada", 36];
```

Usare `unknown` per dati non verificati e restringerli prima dell'uso. Limitare `any`, perché disattiva i controlli. TypeScript spesso inferisce il tipo senza annotazione esplicita.

```typescript
function lunghezza(valore: string | string[]): number {
  return typeof valore === "string" ? valore.length : valore.length;
}
```

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione60) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione62)
