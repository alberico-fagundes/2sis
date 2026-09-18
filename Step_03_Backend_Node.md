# ⚙️ Passo 03: O Maestro (Backend Node)

Agora que temos o Frontend pronto, precisamos da outra metade do Microsserviço: o servidor Node.js que vai receber os cliques da tela e (futuramente) conversar com a UTI de Dados em Python.

### 📌 O Conceito (Teoria Profunda)
Enquanto o Vite gerou o Frontend todinho sozinho, no Backend nós começamos do Absoluto Zero. 
* O comando `npm init -y` cria a "certidão de nascimento" do seu projeto (`package.json`).
* **Express:** É a biblioteca que transforma o Node em um Servidor Web capaz de ouvir portas (ex: porta 3000).
* **CORS:** É o "Segurança da Boate". Por padrão, navegadores proíbem que um site na porta 5173 puxe dados da porta 3000. O CORS é quem "libera a entrada" para que o React possa conversar com o Node.

### 💻 Mão na Massa (Desafio Ativo)
Volte o seu terminal para a pasta mestre (`template_3sis`).

**Sua Tarefa Prática:**
1. Crie uma pasta chamada `backend` e entre nela.
2. Gere o arquivo `package.json` rodando `npm init -y`.
3. Instale as duas bibliotecas vitais usando o npm: `express` e `cors`.
4. Crie um arquivo em branco chamado `server.js` na raiz da pasta `backend`.

**Teste:** Olhe dentro do arquivo `package.json` gerado na pasta backend. Na aba de "dependencies", você deve ver o express e o cors instalados lá.
