# ⚛️ Projeto: Mega Navbar Reutilizável
## Passo 1: Componentes Funcionais no React

Neste workshop, vamos praticar o trabalho com Componentes Funcionais do React criando uma barra de navegação (Navbar). 

### 📌 O que você vai aprender?
* O que são Componentes Funcionais.
* Regras essenciais de sintaxe do React.

---

### 💻 Mão na Massa

A primeira etapa é definir um componente funcional chamado `Navbar`.

* **Se você está no Plano A (Vite):** Crie um arquivo chamado `Navbar.jsx` na sua pasta `src/`.
* **Se você está no Plano B (CDN/HTML):** Vá até a tag `<script type="text/babel">` do seu `index.html`.

**Regras importantes para o desafio:**

1. **Letra Maiúscula Obrigatória:** 
   Todo componente funcional no React **precisa** começar com a letra maiúscula (Ex: `Navbar` e não `navbar`). É assim que o React sabe que isso é um componente customizado e não uma tag HTML normal como `<div>`.

2. **Exportação Nomeada (Named Export) - *Apenas para o Plano A*:** 
   Se você estiver usando arquivos separados (Plano A), certifique-se de colocar a palavra `export` antes da sua função. Isso permite que outros arquivos leiam o seu componente.
   *Exemplo:*
   ```javascript
   export function MinhaFuncao() {
     return <h2>Olá</h2>;
   }
   ```
   *(No Plano B, você não precisa colocar 'export' pois tudo fica no mesmo arquivo).*

---

### ⚠️ Erro Comum (Fique Atento!)
Se você esquecer de exportar o componente no arquivo `.jsx`, o React vai quebrar a sua página e mostrar este erro no Console do navegador:

> *Warning: React.createElement: type is invalid... You likely forgot to export your component from the file it's defined in.*

**Sua Tarefa:** Crie a função vazia do componente `Navbar`.
