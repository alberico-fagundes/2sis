# 🔌 Passo 07: Integração Frontend-Backend (Fetch & State no React)

Nas aulas anteriores:
* **No Backend (`server.js`):** Criamos a API Express rodando na **porta 3333** com o endpoint `/api/cartas` que devolve o objeto `{ cartasAliadas, cartasInimigas }`.
* **No Frontend (`App.jsx`):** Criamos o estado `cartas` com `useState` e buscamos a API com `useEffect` e `fetch('http://localhost:3333/api/cartas')`.

Neste **Passo 07**, o desafio é **renderizar dinamicamente os dados** recebidos do backend dentro do tabuleiro.

---

### 📌 Análise do Estado Atual do Código

No seu `App.jsx`, os dados do servidor já chegam e são guardados no estado `cartas`:

```javascript
// O estado armazena um objeto com duas listas:
// cartas = { cartasAliadas: [...], cartasInimigas: [...] }
```

**O problema atual:** As divs `<div className="mao-aliado"></div>` e `<div className="mao-inimigo"></div>` continuam **vazias** no JSX. Precisamos transformar esse array de objetos em elementos visuais.

---

### 📖 Sintaxe Básica (Exemplo Análogo)

No React, nunca criamos HTML repetido manualmente para listas. Usamos o método `.map()` do JavaScript.

**Como mapear um Array contido dentro de um Objeto no JSX:**

```jsx
{/* Suponha um objeto estado: const [dados, setDados] = useState({ usuarios: [] }); */}

<div className="lista-container">
  {/* 1. Acessamos a lista através da propriedade do objeto (dados.usuarios) */}
  {dados.usuarios.map((item) => (
    // 2. A prop 'key' deve receber o ID único de cada item
    // 3. Acessamos o atributo desejado com a notação de ponto (item.name)
    <div key={item.id} className="card-item">
      {item.name}
    </div>
  ))}
</div>
```

* **`map((item) => ...)`:** Transforma cada objeto do array em uma tag JSX.
* **`key={item.id}`:** Obrigatório no React para manter a performance e renderização corretas ao alterar elementos.
* **`{item.name}`:** As chaves `{}` permitem inserir código/variáveis JavaScript dentro do JSX.

---

### 💻 Mão na Massa (Desafio Ativo)

Sua missão é aplicar o padrão `.map()` no retorno JSX do seu `App.jsx`.

**Sua Tarefa Prática:**
1. Abra `frontend/src/App.jsx`.
2. Localize a `<div className="mao-aliado"></div>`.
3. Insira dentro dela o mapeamento de `cartas.cartasAliadas`:
   * Use `.map((carta) => ...)`
   * Crie uma `<div className="carta" key={carta.id}>`
   * Exiba o nome da carta usando `{carta.name}`
4. Localize a `<div className="mao-inimigo"></div>`.
5. Insira dentro dela o mapeamento de `cartas.cartasInimigas`:
   * Use `.map((carta) => ...)`
   * Crie uma `<div className="carta inimigo" key={carta.id}>`
   * Exiba o nome da carta usando `{carta.name}`

---

### 🧪 Teste de Aceite:
1. Certifique-se de que o backend está rodando no terminal (`node server.js` na porta 3333).
2. Deixe o frontend React rodando (`npm run dev`).
3. Abra a aplicação no navegador.
4. Se as cartas **"Carta Aliada 1"**, **"Carta Aliada 2"**, **"Carta Aliada 3"** e as cartas inimigas aparecerem renderizadas nas laterais, a integração foi concluída com sucesso!
