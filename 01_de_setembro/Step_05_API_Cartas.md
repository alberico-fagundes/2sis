# 🗄️ Passo 05: A API de Cartas no Backend

No Passo 04 colocamos nosso servidor Express no ar respondendo a um status simples. Agora, vamos transformar nosso backend na "fonte da verdade" dos dados do jogo, criando uma rota que entrega o Banco de Dados de Cartas para o jogo.

### 📌 O Conceito (Teoria Profunda)
Em aplicações modernas (SaaS/Microsserviços), o Frontend **nunca** guarda dados fixos no seu próprio código. As informações (como cartas, pontuações, usuários) ficam guardadas no Backend.
* **Arrays de Objetos (JSON):** É a estrutura padrão para representar listas de entidades. Cada carta tem atributos como `id`, `nome`, `forca` e `img`.
* **Endpoints da API:** São as rotas do backend que expõem esses dados para que qualquer cliente (React, app mobile, etc.) possa consumi-los em formato JSON através de requisições HTTP (`GET`).

### 📖 Sintaxe Básica (Exemplos Análogos)

**1. Estrutura de Lista de Objetos:**
```javascript
const listaDeExemplo = [
  { id: 1, item: "Item A", valor: 10 },
  { id: 2, item: "Item B", valor: 25 }
];
```

**2. Retornando Estruturas Complexas no Express:**
Podemos responder a uma requisição enviando um objeto que contém listas dentro:
```javascript
app.get('/meu-endpoint', (req, res) => {
  res.json({
    categoriaA: listaDeExemplo,
    mensagem: "Dados carregados com sucesso"
  });
});
```

---

### 💻 Mão na Massa (Desafio Ativo)

Sua missão é estender o arquivo `server.js` do seu backend para que ele sirva o deck de cartas do Faunadex.

**Sua Tarefa Prática:**
1. Abra o arquivo `backend/server.js`.
2. Acima das rotas, crie duas constantes: `cartasAliadas` e `cartasInimigas`. Cada uma deve conter um Array com 5 objetos de cartas. Cada carta deve possuir:
   * `id` (número único)
   * `nome` (string, ex: "Urso Alpha")
   * `forca` (número de 1 a 10)
   * `img` (URL de imagem, ex: `"https://placebear.com/200/300"`)
3. Crie uma nova rota `GET` apontando para `'/api/cartas'`.
4. Faça essa rota responder enviando um JSON com as duas listas (ex: `{ aliadas: cartasAliadas, inimigas: cartasInimigas }`).
5. Garanta que o servidor continua ouvindo na porta `3000`.

**Teste:** 
Abra o terminal na pasta `backend`, rode `node server.js` e acesse `http://localhost:3000/api/cartas` no seu navegador. Você deve ver a estrutura JSON completa das cartas aliadas e inimigas exibida na tela!
