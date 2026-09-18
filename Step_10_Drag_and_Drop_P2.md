# 🧲 Passo 10: Drag & Drop no React - Parte 2 (Drop Zone & Pouso no Tabuleiro)

Agora que as cartas voam com os dados anexados no `onDragStart`, precisamos preparar os 9 espaços do tabuleiro para receber essas cartas, validar se o slot está livre e atualizar o estado do React.

### 📌 O Conceito (Teoria Profunda)
1. **`onDragOver` e `e.preventDefault()`:** Por padrão, navegadores **proíbem** soltar coisas em elementos comuns. O `preventDefault()` cancela essa trava de segurança, liberando o slot como zona de soltura.
2. **`onDrop`:** Acionado quando o usuário solta o botão do mouse sobre um slot.
3. **Estado do Tabuleiro no React:** Representamos os 9 slots da mesa como um Array de 9 posições no estado: `Array(9).fill(null)`.
4. **Atualização Imutável do Estado:** Em vez de modificar o array existente, criamos uma cópia (`[...tabuleiro]`), alteramos o slot desejado e chamamos a função `setTabuleiro` para que o React atualize a interface.

### 📖 Sintaxe Básica (Exemplos Análogos)

**1. Manipuladores de Drop Zone e Gerenciamento de Estado no React:**
```jsx
// Estado inicial do tabuleiro de 9 casas vazias
const [tabuleiroSlots, setTabuleiroSlots] = useState(Array(9).fill(null));

const aoSobrevoarSlot = (evento) => {
  // OBRIGATÓRIO: Cancela o bloqueio padrão do navegador
  evento.preventDefault(); 
};

const aoSoltarNoSlot = (evento, indiceSlot) => {
  evento.preventDefault();
  
  // Regra de segurança: Se o slot já tem carta, ignora a jogada!
  if (tabuleiroSlots[indiceSlot] !== null) return;

  // Recupera os dados guardados na mochila de transferência
  const idDaCarta = evento.dataTransfer.getData('cartaId');

  // Atualização imutável do array do tabuleiro
  const novoTabuleiro = [...tabuleiroSlots];
  novoTabuleiro[indiceSlot] = idDaCarta;
  setTabuleiroSlots(novoTabuleiro);
};
```

---

### 💻 Mão na Massa (Desafio Ativo)

Sua missão é transformar os 9 slots do tabuleiro React em Drop Zones ativas que fixam as cartas e atualizam a mão do jogador.

**Sua Tarefa Prática:**
1. Abra `frontend/src/App.jsx`.
2. Crie o estado do tabuleiro:
   `const [tabuleiro, setTabuleiro] = useState(Array(9).fill(null));`
3. Crie a função `tratarDragOver`:
   ```javascript
   const tratarDragOver = (e) => e.preventDefault();
   ```
4. Crie a função `tratarDrop(e, indexSlot)`:
   * Evite a ação padrão com `e.preventDefault()`.
   * Verifique se `tabuleiro[indexSlot]` já possui uma carta. Se sim, cancele com `return`.
   * Obtenha o ID da carta da mochila de transferência (`e.dataTransfer.getData('cartaId')`).
   * Encontre o objeto da carta correspondente.
   * Crie uma cópia do array `tabuleiro`, coloque a carta na posição `indexSlot` e atualize com `setTabuleiro(...)`.
   * remova a carta jogada da mão do aliado usando `setCartasAliadas(prev => prev.filter(c => c.id !== cartaId))`.
5. No JSX do tabuleiro, substitua as divs estáticas por uma renderização via `.map()` do estado `tabuleiro`:
   * Aplique `onDragOver={tratarDragOver}` e `onDrop={(e) => tratarDrop(e, index)}` em cada `<div className="slot">`.
   * Se o slot tiver uma carta (`carta !== null`), renderize o componente/div da carta fixada no slot sem permissão de arraste (`draggable={false}`).

**Teste Final:**
Abra o navegador, arraste uma carta da sua mão aliada e solte em qualquer uma das 9 casas do tabuleiro. A carta deve pousar perfeitamente no slot escolhido, travar na mesa e sumir da sua mão!
