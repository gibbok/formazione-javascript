# Introduzione a React

React è una libreria per costruire interfacce tramite componenti. Un componente riceve dati, restituisce una descrizione dell'interfaccia e viene rivalutato quando cambiano le sue dipendenze.

## Creare un progetto

Per un progetto moderno usare un framework React o un build tool supportato, invece di aggiungere script casuali a una pagina:

```bash
npm create vite@latest mia-app -- --template react
cd mia-app
npm install
npm run dev
```

Installare versioni coerenti di `react` e `react-dom`. React 19 è stabile; API come Server Components e Server Functions dipendono però dall'integrazione del framework.

## Primo componente

```jsx
function App() {
  return <h1>Ciao React</h1>;
}

export default App;
```

Nel browser il punto d'ingresso usa `createRoot`:

```jsx
import { createRoot } from "react-dom/client";
import App from "./App.jsx";

createRoot(document.getElementById("root")).render(<App />);
```

React aggiorna il DOM solo dove la descrizione è cambiata. Il componente deve essere puro: niente modifiche a variabili esterne o DOM durante il render.

## Sviluppo moderno

Usare ESLint per Rules of React e Hooks, TypeScript per contratti più forti e React DevTools per ispezionare componenti, props e render. Non confondere React con un router, un client dati o un framework full-stack: questi sono strumenti separati.

### By [Maurizio Tolomeo](https://github.com/moris88)

[HOMEPAGE](https://moris88.github.io/formazione-javascript/) | [LEZIONE SUCCESSIVA](https://moris88.github.io/formazione-javascript/lezioni/lezione78)
