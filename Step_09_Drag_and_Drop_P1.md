# 🖐️ Passo 09: Drag & Drop no React - Parte 1 (Drag Start)

Com as cartas vestidas e dinâmicas, entramos na mecânica principal de interatividade do jogo: **Drag & Drop (Arrastar e Soltar)**. Nesta primeira parte, ensinaremos o React a liberar as cartas para serem seguradas e a "carregar" os dados da carta na mochila do navegador durante o voo.

### 📌 O Conceito (Teoria Profunda)
Nativamente, os navegadores não deixam elementos HTML serem arrastados livremente. Para ativar essa capacidade no React, usamos:
1. **`draggable={true}`:** Atributo que sinaliza ao navegador que a `div` da carta pode ser destacada da tela.
2. **`onDragStart`:** Evento sintético do React acionado no milissegundo em que o usuário clica e começa a mover o mouse.
3. **`e.dataTransfer.setData()`:** A "bolsinha invisível" do navegador. Usamos este método para guardar o ID (ou o objeto JSON completo) da carta que está voando.
4. **Feedback Visual:** Mudar a opacidade da carta enquanto ela é arrastada dá a sensação tátil de que a carta saiu da mão do jogador.

### 📖 Sintaxe Básica (Exemplos Análogos)

**1. Habilitando Arraste e Anexando Dados em Eventos Sintéticos do React:**
```jsx
function CardItem({ item }) {
  const aoComecarArrastar = (evento, itemObjeto) => {
    // Armazena a informação como String JSON na mochila de transferência
    evento.dataTransfer.setData('itemDados', JSON.stringify(itemObjeto));
  };

  return (
    <div
      draggable={true}
      onDragStart={(e) => aoComecarArrastar(e, item)}
      className="card-elemento"
    >
      {item.nome}
    </div>
  );
}
```

---

### 💻 Mão na Massa (Desafio Ativo)

Sua missão é permitir que as cartas aliadas na mão do jogador sejam arrastáveis e carreguem seus dados durante o movimento.

**Sua Tarefa Prática:**
1. Abra `frontend/src/App.jsx`.
2. Crie uma função chamada `tratarDragStart` (ou `handleDragStart`) que recebe o evento `e` e o objeto `carta`.
3. Dentro dessa função, use `e.dataTransfer.setData('cartaId', carta.id.toString())` (ou converta a carta para JSON com `JSON.stringify(carta)`).
4. Na renderização das cartas aliadas (`cartasAliadas.map(...)`), adicione:
   * `draggable={true}`
   * `onDragStart={(e) => tratarDragStart(e, carta)}`
5. *(Opcional)* Crie um estado `cartaArrastadaId` com `useState(null)` para guardar qual carta está voando, adicionando uma classe CSS temporária (ex: `opacity: 0.5`) para dar feedback visual de transparência.

**Teste:**
Abra o navegador no frontend, clique em uma carta aliada e arraste o mouse. Você deve ver o "fantasma" da imagem da carta acompanhando o ponteiro do mouse!
