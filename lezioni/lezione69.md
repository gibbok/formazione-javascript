# Utility Types

Gli utility types trasformano tipi esistenti senza duplicarne la definizione.

```typescript
interface Utente {
  id: number;
  nome: string;
  email: string;
}

type Aggiornamento = Partial<Utente>;
type UtenteCompleto = Required<Utente>;
type Pubblico = Pick<Utente, "id" | "nome">;
type SenzaEmail = Omit<Utente, "email">;
```

Altri utility comuni sono `Readonly`, `Record`, `ReturnType`, `Parameters`, `Awaited`, `Exclude` ed `Extract`. Usarli per rappresentare input, output e trasformazioni, senza creare tipi inutilmente complessi.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione68) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione70)
