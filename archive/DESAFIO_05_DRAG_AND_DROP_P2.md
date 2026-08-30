# 🚀 DESAFIO 05 - A ARENA FAUNADEX (O POUSO NA MESA)
## Engenharia de Software ULTRA DIDÁTICA | Fase 5 (Terça - 2 Aulas)

> 🎓 **PROJETO INTEGRADOR (PBL):** O Faunadex avança conectando as disciplinas:
> - 🖥️ **ITE:** Eventos Avançados de Interface Web (Drag Over e Drop). Entendendo como o DOM lida com sobreposições e transferências de nós (Nodes).
> - 🧩 **Análise e Método de Sistemas:** A integração de Módulos. Hoje nós conectamos a "Mão do Jogador" (Módulo A, feito na Sexta) com o "Tabuleiro" (Módulo B). A mágica acontece quando dois sistemas independentes começam a conversar.

> **🎯 OBJETIVO EXTRAORDINÁRIO:** Nós já sabemos segurar a carta e ela até se transforma num "fantasma" que segue o mouse. O problema? A mesa de batalha ainda é sólida como uma parede de concreto e recusa a nossa jogada, devolvendo a carta pra mão. Hoje vamos transformar os 9 espaços (slots) da mesa em "zonas magnéticas" (Drop Zones) que aceitam a carta, grudam ela no lugar e atualizam as regras do jogo. O ciclo de Gameplay principal começa a nascer!

---

## 🧲 PASSO 10: AS ZONAS MAGNÉTICAS DO TABULEIRO (DROP)

Por medida de segurança, o seu navegador de internet bloqueia que você saia soltando coisas pela tela (imagine o caos se você arrastasse uma imagem sem querer e ela destruísse o site). Para a mesa aceitar a carta, precisamos explicitamente mandar o navegador abaixar os escudos.

Vamos colocar um "ouvidor" em cada buraco (slot) da mesa. 

**1. O Código Magnético Completo:**
Copie o bloco de código abaixo e cole no final do seu arquivo JavaScript. Ele vai varrer a mesa inteira e adicionar 3 ouvidos especiais (`dragover`, `dragleave` e `drop`) para cada espaço de uma só vez! Leia atentamente os comentários, eles são a explicação da mágica.

```javascript
// Primeiro, capturamos todos os 9 buracos da mesa (tudo que tem a classe .slot)
const slotsMesa = document.querySelectorAll('.slot');

// Agora usamos o forEach para aplicar as mesmas regras magnéticas em todos os 9 buracos:
slotsMesa.forEach(slot => {
    
    // 1. O VOO RASANTE (dragover)
    // O que acontece quando a carta está SOBREVOANDO o buraco?
    slot.addEventListener('dragover', (evento) => {
        // MÁGICA DE HACKER: O preventDefault() cancela o bloqueio natural do navegador.
        // Sem essa linha, o navegador diz "Não!" e a carta quica de volta pra mão.
        evento.preventDefault(); 
        
        // Efeito visual de ímã: Acendemos o buraco de verde avisando o jogador: "PODE SOLTAR!"
        slot.style.backgroundColor = '#4CAF50'; 
    });

    // 2. A DESISTÊNCIA (dragleave)
    // O que acontece quando o jogador passa a carta por cima, mas desiste e tira o mouse?
    slot.addEventListener('dragleave', () => {
        // Se a carta saiu de cima, apagamos a luz verde e devolvemos a cor original do buraco.
        slot.style.backgroundColor = '#1b263b'; 
    });

    // 3. A TRANSFERÊNCIA DE MATÉRIA (O Pouso / drop)
    // O que acontece no exato milissegundo em que o botão do mouse é solto?
    slot.addEventListener('drop', (evento) => {
        // Novamente, impedimos o navegador de tentar abrir a carta como se fosse um link.
        evento.preventDefault();
        
        // A carta pousou. Desligamos a luz verde do buraco.
        slot.style.backgroundColor = '#1b263b';
        
        // COMO ACHAMOS A CARTA CERTA?
        // Simples: o JavaScript procura no HTML quem é a ÚNICA carta que está voando 
        // (a que ganhou a classe .segurando no Passo 9)
        const cartaSegurada = document.querySelector('.segurando');
        
        // REGRA DE OURO DA ENGENHARIA DE JOGOS: 
        // Não podemos colocar duas cartas no mesmo buraco. 
        // O "if" abaixo verifica: "Este buraco tem zero filhos (está vazio)?"
        if(slot.children.length === 0) {
            // Se estiver vazio, usamos o appendChild para MOVER a carta da mão para o tabuleiro.
            // O appendChild não clona a carta, ele literalmente teleporta o elemento HTML.
            slot.appendChild(cartaSegurada);
            
            // TRAVA DE SEGURANÇA: Uma vez jogada, a carta está fixada.
            // Tiramos a permissão de arraste para o jogador não roubar e puxar a carta de volta!
            cartaSegurada.setAttribute('draggable', 'false');
        }
    });
});
```

**Resumo da Ópera (Como tudo se conecta):**
O `dragover` desliga a parede invisível do navegador. O `dragleave` é pura perfumaria para deixar o jogo polido (feedback visual). E o rei da festa é o `drop`: ele puxa a carta pela classe `.segurando` (que nós criamos na aula de sexta) e teleporta ela da div "mão" para a div do "tabuleiro", travando-a no chão de cimento fresco. Atualize e jogue. Você agora consegue arrastar cartas para a mesa! O núcleo de gameplay do Faunadex nasceu!

---

## 🧠 MICRO-DESAFIO ANTI-ÓCIO (Para provar que você não é um robô)

Não confie apenas nos meus textos, quebre o seu próprio jogo!
1. Tente arrastar a carta e soltá-la fora da mesa (tipo, num espaço em branco da tela). O que acontece? Ela volta para a sua mão! Isso ocorre porque a tela inteira está bloqueada, nós só abrimos exceção (o `preventDefault()`) dentro dos "slots".
2. Tente jogar uma carta por cima de outra carta que já está na mesa. Ela não vai! Por quê? Por causa da nossa trava inteligente de engenharia `if(slot.children.length === 0)`. Se quiser ver o universo quebrar, apague esse `if` inteiro e teste novamente!

---

## 💾 O SAVE GAME OBRIGATÓRIO (Git)

Não feche o VSCode sem salvar o seu progresso no Git! Integrar dois módulos separados é o ponto de maior risco de qualquer sistema. Salvar aqui significa que o pilar central do seu jogo está garantido e perfeitamente versionado contra bugs futuros.

1. Vá no menu **Source Control** do VSCode (o ícone das três bolinhas conectadas).
2. Na caixinha de texto, digite a mensagem (o seu log) com muita clareza: 
   `Passo 10: Sistema de Drop implementado, zonas magneticas e transferencia de modulos funcional`
3. Clique no botão azul gigantesco **Commit** (e faça o Push se necessário).

Pronto! Você evoluiu de um "montador de páginas" para um verdadeiro Arquiteto de Sistemas Interativos. Parabéns!
