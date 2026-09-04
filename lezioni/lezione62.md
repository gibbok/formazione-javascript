# Tipi avanzati

I tipi unione descrivono più possibilità, mentre gli intersection type combinano strutture.

```typescript
type Identificativo = string | number;
type Timestampato = { creato: Date };
type Utente = { nome: string } & Timestampato;
```

I literal type restringono i valori possibili:

```typescript
type Stato = "attivo" | "sospeso" | "eliminato";
```

Type guard, `in`, `typeof` e `instanceof` restringono un'unione. Le discriminated union con una proprietà comune rendono sicuri gli switch.

```typescript
type Risultato = { ok: true; valore: string } | { ok: false; errore: string };
```

Usare `never` per rami impossibili e `unknown` invece di `any` quando il tipo non è ancora noto.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione61) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione63)
