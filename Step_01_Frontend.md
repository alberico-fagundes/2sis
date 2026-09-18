# 🏗️ Passo 01: A Fundação do Frontend (Vite)

Em uma arquitetura de microsserviços, separamos visualmente e estruturalmente o "Rosto" (Frontend) do "Maestro" (Backend). Para o nosso Rosto, usaremos a ferramenta de scaffolding chamada Vite.

### 📌 O Conceito (Teoria Profunda)
O Vite não é o React em si; ele é um **Empacotador (Bundler)**. No passado, configurávamos dezenas de arquivos complexos (Webpack) só para o React ligar. O Vite faz isso em 2 segundos e já deixa o projeto pronto para rodar.

### 💻 Mão na Massa (Desafio Ativo)
Como você já está dentro da pasta raiz (`template_3sis`), sua tarefa é apenas gerar a subpasta do frontend.

**Sua Tarefa Prática:**
1. Abra o terminal raiz do seu projeto.
2. Invoque o Vite pedindo para ele criar um projeto chamado `frontend` utilizando o template do react:
   `npm create vite@latest frontend -- --template react`
3. Entre na pasta recém-criada (`cd frontend`).
4. Mande o npm ler o `package.json` e baixar todas as dependências ocultas (`npm install`).

**Teste:** A pasta pesada `node_modules` apareceu? Então você está pronto para o Passo 2!
