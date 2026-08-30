# ⚛️ Projeto: Mega Navbar Reutilizável
## Passo 2: Escrevendo JSX e className

Agora que você já criou o esqueleto do seu Componente Funcional `Navbar` no passo anterior, é hora de dar vida a ele construindo o seu interior usando **JSX**.

### 📌 O que é JSX? (Revisão)
JSX é uma extensão de sintaxe para JavaScript. Em termos simples: ele permite que você **escreva código muito parecido com HTML dentro do seu arquivo JavaScript**. Isso torna a criação e o gerenciamento de telas no React muito mais fáceis.

*Exemplo de JSX na prática:*
```javascript
export function App() {
  return (
    <div>
      <h1>Currículo de React</h1>
      <p>Eu amo aprender React!</p>
    </div>
  );
}
```

---

### 💻 Mão na Massa

A sua tarefa agora é preencher o interior do componente `Navbar` que você criou.

Dentro do componente, você deve **retornar** (usando a palavra `return`) uma tag HTML `<nav>`. Essa tag servirá de contêiner principal para a nossa barra de navegação.

**Regra importante (className):**
A tag `<nav>` precisa ter uma classe CSS chamada `navbar`. 
No HTML comum, nós escreveríamos `<nav class="navbar">`. Porém, no JSX (que no fundo é JavaScript), a palavra `class` é uma "palavra reservada" usada para criar Classes em programação Orientada a Objetos. 
Para resolver esse conflito, no React nós usamos **`className`** em vez de `class`.

*Exemplo:*
```javascript
<div className="minha-classe">...</div>
```

**Sua Tarefa:** 
Dentro do seu arquivo do componente, faça a função `Navbar` retornar a tag `<nav>` com o `className` correto. Lembre-se de colocar os parênteses `()` logo após o `return`!
