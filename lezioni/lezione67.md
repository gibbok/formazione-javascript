# Generici

I generici permettono di mantenere il legame tra tipi senza ricorrere ad `any`.

```typescript
function primo<T>(valori: T[]): T | undefined {
  return valori[0];
}

const numero = primo([1, 2, 3]);
const testo = primo(["a", "b"]);
```

I vincoli limitano le operazioni disponibili:

```typescript
function lunghezza<T extends { length: number }>(valore: T): number {
  return valore.length;
}
```

I generici possono essere usati con interfacce, classi e alias. Dare nomi descrittivi ai parametri quando il codice non è banale.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione66) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione68)
