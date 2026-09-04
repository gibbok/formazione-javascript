# Interfacce

Le interfacce descrivono la forma di oggetti e contratti tra componenti.

```typescript
interface Utente {
  readonly id: number;
  nome: string;
  email?: string;
}

function visualizza(utente: Utente): string {
  return utente.nome;
}
```

`readonly` impedisce l'assegnazione tramite quel tipo; `?` indica una proprietà opzionale. Le interfacce possono estendersi e dichiarare firme di funzioni o indicizzazioni.

```typescript
interface Admin extends Utente {
  permessi: string[];
}
```

Usare interfacce per contratti estendibili e `type` per unioni, tuple e combinazioni più espressive.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione62) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione64)
