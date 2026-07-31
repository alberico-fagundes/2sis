# 🐍 Instalação do Miniconda no Linux

> **O que é o Miniconda?** É uma versão enxuta do Conda — um gerenciador de ambientes e pacotes Python. Com ele você instala o Git, Python e qualquer biblioteca de forma organizada e sem conflitos.

---

## 📥 Passo 1 — Baixar o instalador

Abra o terminal e execute:

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

---

## ▶️ Passo 2 — Executar o instalador

```bash
bash Miniconda3-latest-Linux-x86_64.sh
```

---

## 🖱️ Passo 3 — Seguir as instruções na tela

| Etapa | O que fazer |
|---|---|
| Termos de licença | Pressione **Enter** e segure até chegar ao final |
| Aceitar licença | Digite **`yes`** e pressione Enter |
| Local de instalação | Apenas pressione **Enter** para aceitar o padrão |
| Inicializar o Conda | Digite **`yes`** quando aparecer `Do you wish the installer to initialize Miniconda3?` |

---

## 🔄 Passo 4 — Ativar as alterações

**Opção A:** Feche e abra o terminal novamente.

**Opção B:** Atualize a sessão atual sem fechar:

```bash
source ~/.bashrc
```

---

## ✅ Verificando a instalação

Se tudo correu bem, o início da linha do terminal exibirá:

```
(base) seu-usuario@maquina:~$
```

Confirme a instalação listando os pacotes instalados:

```bash
conda list
```

Se aparecer uma lista de pacotes, o Miniconda está instalado e funcionando! 🎉

---

## 🚀 Próximo passo — Instalar o Git via Conda

Com o Miniconda instalado, instale o Git com um único comando:

```bash
conda install -c conda-forge git
```

Verifique se o Git foi instalado:

```bash
git --version
```
