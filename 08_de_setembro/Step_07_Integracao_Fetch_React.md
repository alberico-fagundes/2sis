# 🔌 Passo 07: Integração Frontend-Backend (Fetch & State no React)

Agora que o layout está pronto e a API Express está rodando no backend, precisamos fazer o React "conversar" com o servidor via rede usando **Hooks** (`useState` e `useEffect`) e a função `fetch`.

### 📌 O Conceito (Teoria Profunda)
Em aplicações reativas:
1. **`useState`:** É a memória do componente React. Qualquer mudança na variável de estado faz a tela re-renderizar automaticamente para refletir a novidade.
2. **`useEffect` com `[]` (Array de Dependências Vazio):** Executa o código interno apenas **uma vez**, no exato instante em que o componente nasce na tela (montagem). Sem ele, o `fetch` seria executado em um loop infinito travando o navegador!
3. **`fetch()`:** É a API nativa do JavaScript para disparar requisições HTTP assíncronas para servidores.
4. **`.map()`:** Método JavaScript usado para transformar cada item de um Array em um elemento visual JSX.

### 📖 Sintaxe Básica (Exemplos Análogos)

**1. Padrão de Busca de Dados Assíncronos no React:**
```jsx
import { useState, useEffect } from 'react';

function ExemploIntegracao() {
  const [itens, setItens] = useState([]);

  useEffect(() => {
    fetch('http://localhost:3000/sua-rota')
      .then(resposta => resposta.json())
      .then(dados => {
        setItens(dados.minhaLista);
      })
      .catch(erro => console.error("Erro na integração:", erro));
  }, []); // Array vazio = executa só na montagem!

  return (
    <div>
      {itens.map(item => (
        <p key={item.id}>{item.nome}</p>
      ))}
    </div>
  );
}
```

---

### 💻 Mão na Massa (Desafio Ativo)

Sua tarefa é conectar o React ao endpoint `/api/cartas` do backend Express e desenhar as cartas dinamicamente na tela.

**Sua Tarefa Prática:**
1. Abra `frontend/src/App.jsx`.
2. Importe `useState` e `useEffect` do pacote `'react'`.
3. Crie dois estados no topo do componente `App`:
   * `cartasAliadas` (iniciado com `[]`)
   * `cartasInimigas` (iniciado com `[]`)
4. Crie um `useEffect` que faça a requisição `fetch('http://localhost:3000/api/cartas')`.
5. Ao receber a resposta em JSON, atualize os estados usando as funções `set` correspondentes aos dados que vieram do backend.
6. Dentro da `<div className="mao-aliado">`, use `.map()` sobre `cartasAliadas` para renderizar uma `<div className="carta" key={carta.id}>`.
7. Dentro da `<div className="mao-inimigo">`, use `.map()` sobre `cartasInimigas` para renderizar uma `<div className="carta inimigo" key={carta.id}>`.
8. Por enquanto, coloque o nome da carta (`carta.nome`) dentro da div para testar a renderização do texto.

**Teste:**
1. Certifique-se de que o backend está rodando (`node server.js` na pasta `backend`).
2. Abra o frontend (`npm run dev`) e acesse o navegador.
3. Se os nomes das cartas aliadas e inimigas nascerem automaticamente nas laterais da tela, a integração foi concluída com sucesso!
