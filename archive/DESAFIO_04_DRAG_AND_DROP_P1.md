# 🚀 DESAFIO 04 - A ARENA FAUNADEX (A MAGIA DO ARRASTE)
## Engenharia de Software ULTRA DIDÁTICA | Fase 4 (Sexta - 1 Aula)

> 🎓 **PROJETO INTEGRADOR (PBL):** O Faunadex avança conectando as disciplinas:
> - 🖥️ **ITE:** Eventos Avançados de Interface Web. Vamos usar a API nativa do HTML5 (Drag and Drop) para interagir com o DOM de forma dinâmica.
> - 🧩 **Análise e Método de Sistemas:** Construção de uma *feature* de alto risco e complexidade, quebrada em uma Sprint curta e gerenciável (Baby Steps).

> **🎯 OBJETIVO EXTRAORDINÁRIO:** Um jogo de cartas de verdade não é feito só de cliques. Você precisa pegar a carta, sentir o "peso" dela e arrastá-la para a mesa! Hoje vamos ativar a "gravidade" do jogo. Vamos transformar nossos pedaços estáticos de HTML em objetos reais que podemos segurar e mover com o mouse.

---

## 🖐️ PASSO 9: O PODER DE SEGURAR A CARTA (DRAG START)

Até agora, nossas cartas são como pinturas na parede: bonitas, mas presas. Para soltá-las, não precisamos de magia negra, precisamos de **Eventos** no JavaScript. Um "Evento" é basicamente ensinar o navegador a ficar de "ouvidos abertos" esperando o jogador fazer alguma coisa.

**1. Permitindo o Arraste (A permissão secreta):**
Por padrão, o navegador não deixa você arrastar qualquer coisa pela tela (imagine que bagunça seria se o usuário saísse arrastando todos os textos do site). Precisamos dar uma "permissão especial" e explícita para as nossas cartas.

Na hora em que o JavaScript cria as cartas uma por uma (lembra do nosso `.forEach` da aula passada?), nós vamos adicionar as regras de *Drag* **EXATAMENTE LOGO ANTES** da linha onde colocamos a carta na mão do aliado (`maoAliado.appendChild(cartaElemento);`).

Vá no seu arquivo de JavaScript (ou dentro da tag `<script>` no final do HTML) e localize o miolo do seu `forEach`. Ele deve ser atualizado para ficar como o bloco abaixo. **Atenção:** leia os comentários verdes do código com calma, eles são a verdadeira aula:

```javascript
    // ... seu código antigo que extrai os dados (cartaDado) e cria a div (cartaElemento) está aqui em cima ...
    
    // 1. A PERMISSÃO DE ARRASTE
    // Dizemos ao HTML: "Ei, esta div não é estática, ela pode ser segurada e puxada pelo mouse!"
    cartaElemento.setAttribute('draggable', 'true');

    // 2. O QUE ACONTECE NO EXATO MILISSEGUNDO EM QUE EU COMEÇO A PUXAR? (dragstart)
    cartaElemento.addEventListener('dragstart', (evento) => {
        // Colocamos uma classe CSS para mudar o visual da carta que ficou na mão enquanto o "fantasma" dela voa.
        cartaElemento.classList.add('segurando');
        
        // A Mochila do Navegador: O 'dataTransfer' é uma bolsinha invisível.
        // Guardamos nela a "forca" da carta para que o tabuleiro saiba quem está caindo nele mais tarde.
        evento.dataTransfer.setData('text/plain', cartaDado.forca);
    });

    // 3. O QUE ACONTECE QUANDO EU SOLTO O BOTÃO DO MOUSE? (dragend)
    cartaElemento.addEventListener('dragend', () => {
        // A carta caiu. Tiramos a classe CSS para ela voltar a ficar com a cor normal.
        cartaElemento.classList.remove('segurando');
    });

    // 4. COLOCANDO NA MESA
    // O seu appendChild antigo já estava aqui no final, não apague ele!
    maoAliado.appendChild(cartaElemento);
```

**2. O Efeito Visual Fantasma (CSS):**
Se você salvar e rodar o jogo agora, a carta já arrasta! Mas visualmente, parece que a carta principal continua imóvel na sua mão e você está arrastando apenas um "clone". O jogador precisa sentir que a carta *saiu* da mão dele.

Vá no topo do seu arquivo, dentro da tag `<style>`, e crie a classe `.segurando` que nós acabamos de inventar ali em cima no JavaScript:

```css
        /* Efeito de Carta Sendo Arrastada (Feedback Visual) */
        .segurando {
            opacity: 0.5; /* A carta original na mão fica 50% transparente */
            transform: scale(1.1); /* Dá um zoomzinho pra dar sensação de profundidade */
            border-color: #00ffff; /* Acende uma borda de neon pra ficar claro qual está selecionada */
        }
```

Atualize o navegador e tente puxar a carta. Percebeu a mágica? A carta na sua mão fica transparente e ganha brilho, indicando que a energia dela viajou com o seu mouse! O cérebro do jogador entende instantaneamente que ele tem o controle daquele objeto.

---

## 🧠 MICRO-DESAFIO ANTI-ÓCIO (Para provar que você não é um copiador de código)

Não acredite cegamente no professor. Quebre o código e teste você mesmo! 
1. Vá no CSS que acabamos de colar e mude a propriedade `opacity: 0.5;` para `opacity: 0.1;`.
2. Salve o arquivo (`Ctrl + S`) e arraste a carta de novo no navegador. 
3. Ela quase desapareceu completamente, não é? Isso prova o seu domínio sobre o visual. O CSS é o mestre da aparência.
4. *Devolva o valor para `0.5` antes de continuar para não estragar seu jogo e atrapalhar os próximos passos.*

---

## 💾 O SAVE GAME OBRIGATÓRIO (Git)

Não ouse fechar o VSCode sem salvar o seu progresso no Git! Você acabou de dar o primeiro e mais importante passo para criar uma mecânica de arrasto complexa. Se o computador travar agora, você perde o que entendeu.

1. Vá no menu **Source Control** do VSCode (o ícone das três bolinhas conectadas).
2. Na caixinha de texto, digite a mensagem (o seu log) exatamente assim: 
   `Passo 9: Sistema de DragStart ativado, cartas arrastáveis com efeito fantasma via CSS`
3. Clique no botão azul gigantesco **Commit** (e se pedir para sincronizar/Push, confirme).

Parabéns, Guerreiro(a)! Na próxima etapa (Parte 2), vamos ensinar o tabuleiro (os buracos vazios da mesa) a perderem o medo de receber cartas e a aceitarem que as cartas caiam sobre eles. Até lá!
