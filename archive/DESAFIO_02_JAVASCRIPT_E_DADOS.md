# 🚀 DESAFIO 02 - A ARENA FAUNADEX (A MAGIA DAS CARTAS E O MOTOR DE DADOS)
## Engenharia de Software ULTRA DIDÁTICA | Terça-Feira, 11 de Agosto (2 Aulas)

> 🎓 **PROJETO INTEGRADOR (PBL):** O Faunadex não é apenas programação, é o elo prático entre 3 disciplinas do 2º SIS:
> - 🖥️ **ITE:** Base estrutural (HTML/CSS), layout em Grid e pensamento computacional via JavaScript.
> - 🧩 **Análise e Método de Sistemas:** Metodologia Ágil (Sprints/Baby Steps), e entregas contínuas (Git).
> - 🗄️ **Introdução a Banco de Dados:** Modelagem de entidades e atributos das cartas preparando terreno para os dados persistentes.

> **🎯 OBJETIVO EXTRAORDINÁRIO PARA HOJE:** Na aula passada montamos o "esqueleto" do nosso jogo. Como hoje temos duas aulas, vamos dar vida a ele! Primeiro, vamos colocar imagens reais e ensinar o jogo a ouvir nossos cliques (JavaScript básico). Depois, vamos apagar as cartas fixas do HTML e criar um Banco de Dados de Cartas em JSON para que o computador as desenhe sozinho!

---

## 🎨 PASSO 2.1: VESTINDO AS CARTAS (BACKGROUND IMAGE)

Vamos trocar aquele fundo azul sem graça por imagens reais de cartas.

**1. Preparando o Terreno:**
Para não perdermos tempo baixando imagens (e evitarmos bugs), vamos usar links diretos da internet (URLs) para vestir nossas cartas. No futuro, vocês poderão trocar por imagens baixadas na pasta `img`.

**2. A Mágica no CSS:**
Abra o seu `index.html` e vá até a tag `<style>`. Vamos alterar o código da classe `.carta`:
```css
        /* Desenhando a Carta - ATUALIZADO */
        .carta {
            /* Tira o background azul e coloca a imagem via URL! */
            background-image: url('https://placebear.com/150/200'); 
            background-size: cover; /* Faz a foto preencher a carta toda */
            background-position: center;
            
            border: 2px solid #4CAF50;
            border-radius: 8px;
            display: flex;
            justify-content: center;
            align-items: center;
            color: transparent; /* Esconde o texto provisório */
            cursor: pointer;
            transition: transform 0.2s; /* Animação suave */
        }
        
        /* Efeito de Hover (passar o mouse) */
        .carta:hover {
            transform: scale(1.1); /* A carta cresce um pouquinho! */
            border-color: yellow;
        }

        /* Cartas do Inimigo puxam outra imagem */
        .inimigo {
            background-image: url('https://placebear.com/150/201');
            border-color: #e94560;
        }
```

💾 **O SAVE GAME OBRIGATÓRIO:**
1. Vá no menu **Source Control** do VSCode.
2. Digite a mensagem: `Passo 2.1: Imagens e efeito hover adicionados nas cartas`.
3. Clique em **Commit**.

---

## 🧠 PASSO 2.2: O PRIMEIRO NEURÔNIO DO JOGO (JAVASCRIPT)

O jogo está bonito, mas ele é burro. Vamos usar o **JavaScript** para criar o "sistema nervoso".

Vá até o **final** do seu arquivo `index.html`, logo **ACIMA** da tag `</body>`, e crie a área do cérebro:
```html
    </div> <!-- Fim da Arena -->

    <!-- CÉREBRO DO JOGO -->
    <script>
        // 1. O Computador precisa enxergar as cartas. Vamos selecioná-las!
        const todasAsCartas = document.querySelectorAll('.carta');

        // 2. Vamos colocar um "Ouvido" em cada carta da mesa.
        todasAsCartas.forEach(carta => {
            carta.addEventListener('click', () => {
                alert("Você clicou em uma carta para o Duelo!");
            });
        });
    </script>
</body>
```
Atualize e clique em qualquer carta. O alerta significa que o JavaScript acordou!

💾 **SAVE GAME:** `Passo 2.2: Adicionado Listener de clique via JavaScript`. Commit & Push!

---

## 🗄️ PASSO 2.3: O BANCO DE DADOS DAS CARTAS (ENTIDADES E ATRIBUTOS)

Escrever HTML na mão para cada carta dá muito trabalho. Vamos apagar o HTML manual e usar JSON!

**1. A Modelagem:**
Ainda dentro do `<script>`, APAGUE o código do alerta que fizemos acima e vamos criar a nossa "Tabela" de Cartas usando JSON. 
```javascript
// Nosso Banco de Dados de Animais Aliados (Usando links web para não falhar imagens)
const bancoDeCartasAliadas = [
    { id: 1, nome: "Urso Alpha", forca: 8, img: "https://placebear.com/200/300" },
    { id: 2, nome: "Urso Beta", forca: 9, img: "https://placebear.com/200/301" },
    { id: 3, nome: "Urso Charlie", forca: 5, img: "https://placebear.com/200/302" },
    { id: 4, nome: "Urso Delta", forca: 6, img: "https://placebear.com/200/303" },
    { id: 5, nome: "Urso Echo", forca: 7, img: "https://placebear.com/200/304" }
];
```

**2. A Renderização Inteligente:**
Apague todas as `<div class="carta">` de dentro da `<div class="mao-aliado">` no seu HTML. Deixe a div da mão vazia!
Depois, logo abaixo do JSON no JavaScript adicione:
```javascript
const maoAliado = document.querySelector('.mao-aliado');

// O JavaScript vai ler o Banco de Dados e criar as cartas
bancoDeCartasAliadas.forEach(cartaDado => {
    let cartaElemento = document.createElement('div');
    cartaElemento.classList.add('carta');
    cartaElemento.style.backgroundImage = `url(${cartaDado.img})`;
    
    // Adiciona o alerta de volta
    cartaElemento.addEventListener('click', () => {
        alert("Você clicou na carta: " + cartaDado.nome + " com força " + cartaDado.forca);
    });

    maoAliado.appendChild(cartaElemento);
});
```
Atualize a tela. As cartas agora nascem diretamente do Banco de Dados!

**🚨 MISSÃO BOSS (Desafio Final da Aula):**
Você reparou que a nossa mão do inimigo não usa o banco de dados? O HTML dela continua ocioso (ou você apagou).
**A sua missão final:**
1. ANTES DE TUDO: Vá no seu HTML e APAGUE as 5 divs da carta que estão dentro da `<div class="mao-inimigo">`. Deixe ela vazia igual você fez com o aliado, senão o inimigo vai ficar com 10 cartas na mão e bugar a tela!
2. Crie um novo array JSON chamado `bancoDeCartasInimigas` com 5 animais diferentes (troque os URLs das imagens no final para `/305`, `/306`, etc).
3. Repita a lógica do `.forEach` para injetar essas cartas dentro da classe `.mao-inimigo`.
4. Atenção: Para elas ficarem vermelhas, você precisará adicionar a classe `inimigo` nelas! (Dica: `cartaElemento.classList.add('inimigo')`).

**O primeiro grupo que conseguir rodar as 5 cartas inimigas dinâmicas, chame o professor para avaliar!**

💾 **SAVE GAME FINAL:** `Passo 2.3: Missão Boss concluída - Cartas inimigas dinâmicas`. Commit & Push!
