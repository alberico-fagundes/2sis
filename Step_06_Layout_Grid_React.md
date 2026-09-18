# 📐 Passo 06: O Layout do Tabuleiro em CSS Grid (React)

Com o backend fornecendo os dados, voltamos ao nosso frontend React (`src/App.jsx`). Vamos construir o esqueleto visual da Arena Faunadex utilizando o poder do **CSS Grid**.

### 📌 O Conceito (Teoria Profunda)
Em aplicações React, a estrutura do HTML fica dentro do arquivo JSX retornado pelos componentes. O **CSS Grid** nos permite criar sistemas de coordenadas bi-dimensionais (linhas e colunas) sem depender de posicionamentos manuais arcaicos ou desalinhamentos.
* **Layout Principal:** Dividido em 3 colunas principais (Mão Aliada na esquerda, Tabuleiro central, Mão Inimiga na direita).
* **Matriz 3x3:** O tabuleiro no centro exige exatamente 9 espaços dispostos em 3 colunas por 3 linhas iguais (`repeat(3, 1fr)`).

### 📖 Sintaxe Básica (Exemplos Análogos)

**1. Estrutura JSX (Retorno do Componente):**
```jsx
function MeuComponente() {
  return (
    <div className="conteiner-pai">
      <div className="coluna-esquerda">...</div>
      <div className="centro-grid">...</div>
      <div className="coluna-direita">...</div>
    </div>
  );
}
```

**2. Regras CSS de Grid bi-dimensional:**
```css
/* Cria 3 colunas com larguras personalizadas */
.conteiner-pai {
  display: grid;
  grid-template-columns: 150px 1fr 150px;
  gap: 20px;
}

/* Cria uma matriz de 3x3 usando a função repeat */
.centro-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  gap: 10px;
}
```

---

### 💻 Mão na Massa (Desafio Ativo)

Sua missão é criar o layout estrutural da arena dentro do projeto React.

**Sua Tarefa Prática:**
1. Abra o arquivo `frontend/src/App.jsx`.
2. Dentro da `div` principal (`dashboard-container` ou `arena`), monte 3 áreas filhas:
   * Uma `div` com a classe `mao-aliado`
   * Uma `div` com a classe `tabuleiro`
   * Uma `div` com a classe `mao-inimigo`
3. Dentro da `div.tabuleiro`, crie **9 elementos** `<div className="slot"></div>` para representar os espaços da mesa.
4. Abra o arquivo `frontend/src/App.css` (ou crie o CSS equivalente) e defina os estilos:
   * Faça a `div` principal ter `display: grid` com 3 colunas (`150px 450px 150px`) e um `gap` para afastar os lados.
   * Faça a `.tabuleiro` usar `display: grid` com `repeat(3, 1fr)` para colunas e linhas, além de um fundo escuro e borda destacada.
   * Defina estilos básicos para `.slot` (fundo escuro, borda suave e altura mínima para ser visível).

**Teste:** 
Rode `npm run dev` na pasta `frontend` e abra no navegador. Você deve ver o tabuleiro perfeitamente alinhado em 3 colunas com os 9 slots no centro!
