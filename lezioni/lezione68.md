# Namespace

I namespace raggruppano dichiarazioni sotto un nome e appartengono soprattutto a codice TypeScript legacy o a librerie globali.

```typescript
namespace Geometria {
  export function areaQuadrato(lato: number): number {
    return lato * lato;
  }
}

console.log(Geometria.areaQuadrato(4));
```

Nei progetti moderni i moduli sono generalmente preferibili: supportano dipendenze esplicite, tree shaking e isolamento migliore. I namespace possono essere utili per dichiarazioni ambientali o compatibilità con codice esistente.

## By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE PRECEDENTE](https://moris88.github.io/formazione-javascript/lezioni/lezione67) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione69)
