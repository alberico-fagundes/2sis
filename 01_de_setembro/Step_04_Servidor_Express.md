# 🚀 Passo 04: O Servidor e a Rota de Status

Nosso ambiente Backend existe, mas ainda não tem código. Vamos escrever a base do Express para ele escutar requisições.

### 📌 O Conceito (Teoria Profunda)
Um servidor Express funciona como um telefonista. Ele fica com o "telefone no ouvido" (ouvindo uma porta física, ex: 3000) esperando alguém ligar.
Quando o React liga para o "ramal" `/api/status`, o Express atende e devolve uma resposta no formato universal JSON.

### 📖 Sintaxe Básica (Exemplos Análogos)
Antes de construir o seu servidor, veja como os comandos do Node.js e do Express se parecem:

**1. Como importar pacotes (O require):**
No Node.js, nós puxamos bibliotecas para dentro de variáveis usando o `require`:
`const nomeDaVariavel = require('nome-do-pacote');`

**2. Como criar uma Rota (O ramal):**
Uma rota do tipo `GET` exige o caminho e uma função que recebe uma requisição (`req`) e dispara uma resposta (`res`):
```javascript
app.get('/meu-caminho-falso', (req, res) => {
  res.json({ aviso: "Atendido com sucesso!" });
});
```

**3. Como mandar o app escutar uma porta (O Listen):**
```javascript
app.listen(8080, () => {
  console.log("Servidor ligado na porta 8080!");
});
```

---

### 💻 Mão na Massa (Desafio Ativo)
Use os bloquinhos de exemplo acima como base para deduzir e escrever a lógica oficial do nosso servidor.

**Sua Tarefa Prática:**
Abra o arquivo `server.js` que você criou e siga a receita abaixo:
1. Importe o pacote `express` para dentro de uma variável chamada `express`.
2. Importe o pacote `cors` para dentro de uma variável chamada `cors`.
3. Crie o seu app iniciando o Express: `const app = express();`
4. Habilite a segurança: digite `app.use(cors());` e `app.use(express.json());`.
5. Crie uma rota do tipo `GET` apontando para o caminho exato `'/api/status'`. Quando acessada, ela deve responder enviando um JSON com a mensagem: `"Backend Node 3SIS Operante!"`.
6. Mande o seu `app` ouvir (`listen`) a porta `3000` e imprima um `console.log` avisando que ligou.

**Teste Final:** No terminal do backend, rode `node server.js`. Depois, abra o seu navegador e acesse `http://localhost:3000/api/status`. Você deve ver o seu JSON na tela!

*(Se tudo rodar, o seu Template Base está completo. Basta subir pro Github!)*
