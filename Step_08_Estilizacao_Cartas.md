# 🎨 Passo 08: Estilização do Card Único (React + CSS)

Nossas cartas já são buscadas da API, mas atualmente aparecem como caixas genéricas de texto. No nosso modelo de design (inspirado nas cartas colecionáveis clássicas como Triple Triad / Bandai), **cada carta é uma imagem completa gerada por IA** que já possui a ilustração do animal, a moldura e os números de força (N, S, L, O) integrados na própria arte da imagem.

---

### 📌 O Conceito (Teoria Profunda)

Quando o visual da carta vem pronto em uma única imagem:
1. **Renderização Limpa no React:** O componente exibe a imagem completa (`<img src={carta.img} />`) sem a necessidade de sobrepor fontes ou criar grids complexos em HTML/CSS para os números.
2. **Propriedades do CSS:** Definimos a proporção clássica de Card Game (proporção `3:4`), cantos arredondados (`border-radius`), sombra projetada (`box-shadow`), transição suave (`transition`) e indicação de arraste (`cursor: grab`).
3. **Identificação do Time/Dono:** A borda da div externa (`.carta`) ganha destaque de cor para identificar se a carta pertence ao jogador (azul) ou ao oponente (vermelho).

---

### 📖 Sintaxe Básica (Exemplo Análogo)

#### 1. Exibindo a Imagem do Card no JSX
```jsx
// Renderizando uma carta com imagem única
<div className={`carta ${carta.dono === 'jogador' ? 'aliado' : 'inimigo'}`}>
  <img src={carta.img} alt={carta.name} className="imagem-card" />
</div>
```

#### 2. Regras CSS de um Card Game (Proporção 3:4)
```css
/* Container da carta */
.carta {
  width: 120px;
  height: 160px;
  border-radius: 8px;
  border: 3px solid #00d2ff; /* Azul para jogador */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
  overflow: hidden;
  cursor: grab;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

/* Moldura do inimigo */
.carta.inimigo {
  border-color: #ff2a5f; /* Vermelho para o oponente */
}

/* Imagem inteira preenchendo a carta */
.imagem-card {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* Efeito ao passar o mouse */
.carta:hover {
  transform: scale(1.08);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.6);
}
```

---

### 💻 Mão na Massa (Desafio Ativo)

Sua missão é dar o acabamento visual às cartas no React.

**Sua Tarefa Prática:**
1. Abra `frontend/src/App.jsx`.
2. No `.map()` que renderiza as cartas aliadas e inimigas, substitua o texto simples por uma tag `<img src={carta.img} alt={carta.name} className="imagem-card" />`.
3. Abra `frontend/src/App.css` e adicione os estilos:
   * **`.carta`**: Defina largura (`120px`) e altura (`160px`), `border-radius: 8px`, `overflow: hidden`, `cursor: grab` e `transition: transform 0.2s`.
   * **`.imagem-card`**: Ajuste `width: 100%`, `height: 100%` e `object-fit: cover`.
   * **`.carta:hover`**: Adicione `transform: scale(1.08)` para criar o efeito tátil ao passar o mouse.

---

### 🧪 Teste de Aceite:
Abra a aplicação no navegador (`http://localhost:5173`). As cartas devem surgir com a arte completa do animal e os números integrados na imagem, elevando-se suavemente com o efeito de hover ao passar o mouse!
