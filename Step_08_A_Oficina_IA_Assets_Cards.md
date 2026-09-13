# 🎮 Missão 08-A: Forja de Cartas com IA & Coleção FaunaDex

> **🏆 MISSÃO DA SUA GUILDA:**  
> O protótipo do jogo está funcional, mas as cartas ainda estão sem arte e sem vida! Sua missão é usar **Inteligência Artificial Generativa** para forjar as cartas lendárias do folclore e fauna brasileira no estilo clássico retrô (Triple Triad / Final Fantasy 1999) e colocá-las para brilhar na tela do seu jogo.

---

## 🎖️ Sistema de Conquistas (XP da Aula)
* 🥉 **[+100 XP] Invocador de IA:** Gerou sua 1ª carta lendária no gerador de imagens.
* 🥈 **[+200 XP] Mestre dos Assets:** Salvou o arquivo `.png` no local correto do projeto.
* 🥇 **[+300 XP] Full-Stack Game Dev:** A carta apareceu linda e renderizada no seu React!

---

## ⚡ Passo 1: Escolha seu Monstro & Copie o Prompt

Abra uma das ferramentas gratuitas de IA no navegador:
👉 **[Bing Image Creator (DALL-E 3)](https://www.bing.com/create)** ou **[Ideogram.ai](https://ideogram.ai)**

Escolha uma das cartas abaixo, dê **Ctrl+C** no prompt e dê **Ctrl+V** na IA:

### 🔥 Opção A: Curupira (O Guardião de Fogo)
```text
Full physical trading card of Brazilian mythical creature Curupira, 1999 Bandai Final Fantasy VIII Triple Triad card style. Gold metallic frame border. In the top-left corner, display four large bold numbers arranged in a cross layout: 8 on top, 2 on the left, 9 on the right, 6 on the bottom. Center illustration of a fiery Curupira with backward feet in a vibrant Amazon rainforest. Dark magenta gradient background. White name banner at bottom reading 'CURUPIRA'. Retro 90s Japanese card game aesthetic, vibrant colors.
```

### 🐺 Opção B: Lobo-Guará (A Fera do Cerrado)
```text
Full physical trading card of Brazilian animal Maned Wolf Lobo Guara, 1999 Bandai Final Fantasy VIII Triple Triad card style. Gold metallic frame border. In the top-left corner, display four large bold numbers arranged in a cross layout: 7 on top, 5 on the left, 8 on the right, 6 on the bottom. Center illustration of an imposing Maned Wolf in a golden sunset savanna. Deep orange and purple background. White name banner at bottom reading 'LOBO GUARA'. Retro 90s Japanese card game aesthetic, vibrant colors.
```

### 🐍 Opção C: Boitatá (A Serpente de Chamas)
```text
Full physical trading card of Brazilian mythical fire serpent Boitata, 1999 Bandai Final Fantasy VIII Triple Triad card style. Gold metallic frame border. In the top-left corner, display four large bold numbers arranged in a cross layout: 9 on top, 7 on the left, 9 on the right, 4 on the bottom. Center illustration of a glowing giant fire snake with fiery eyes. Dark night jungle background. White name banner at bottom reading 'BOITATA'. Retro 90s Japanese card game aesthetic, vibrant colors.
```

*(💡 **Dica Pro:** Quer criar outro? É só trocar o nome e a descrição do meio do prompt!)*

---

## 💾 Passo 2: Baixar e Guardar no Inventário

1. Escolha a melhor imagem gerada e clique em **Baixar / Download**.
2. **Renomeie o arquivo** baixado para um nome simples em minúsculo:
   * Exemplo: `curupira.png` (ou `lobo_guara.png`, `boitata.png`).
3. Arraste e solte o arquivo na pasta pública do seu frontend:
   📂 `frontend/public/cartas/curupira.png`

> ⚠️ **Atenção:** Se a pasta `cartas` ainda não existir dentro de `frontend/public/`, clique com botão direito e crie a pasta `cartas`!

---

## 💻 Passo 3: Registrar a Carta no Backend (`server.js`)

Abra o arquivo `backend/server.js` e aponte o atributo `img` da sua carta:

```javascript
// Localize a lista cartasAliadas ou cartasInimigas e atualize:
{
  id: 1,
  nome: 'Curupira',
  forca: 8, // ou objeto de força { norte: 8, leste: 9, sul: 6, oeste: 2 }
  img: '/cartas/curupira.png' // 👈 Caminho direto da sua carta!
}
```

---

## 🚀 Passo 4: O Grande Teste (Recompensa Visual)

1. No terminal do Backend: `node server.js`
2. No terminal do Frontend: `npm run dev`
3. Abra seu jogo em `http://localhost:5173` no navegador.

✨ **Resultado Esperado:** A carta com a arte épica gerada por você e sua IA vai aparecer no tabuleiro do seu jogo pronta para o duelo!

---

## ✅ Checklist de Conclusão da Missão
- [ ] Consegui gerar pelo menos 1 carta com moldura e números de força no gerador de IA.
- [ ] Salvei a imagem renomeada em `frontend/public/cartas/`.
- [ ] Atualizei o `backend/server.js` com o caminho `/cartas/nome_da_imagem.png`.
- [ ] A carta carregou sem erros no navegador.
