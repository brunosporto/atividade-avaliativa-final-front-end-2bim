
# 👗 StyleWave Moda

<div align="center">

![StyleWave Banner](https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?w=800&q=80)

**Aplicação web de loja de moda desenvolvida com React, Tailwind CSS e React Router**

[![React](https://img.shields.io/badge/React-18-61DAFB?style=flat&logo=react)](https://react.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?style=flat&logo=tailwindcss)](https://tailwindcss.com/)
[![React Router](https://img.shields.io/badge/React_Router-6-CA4245?style=flat&logo=reactrouter)](https://reactrouter.com/)
[![HTML5](https://img.shields.io/badge/HTML5-Semântico-E34F26?style=flat&logo=html5)](https://developer.mozilla.org/pt-BR/docs/Web/HTML)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

[🚀 Demo ao Vivo](#-deploy) · [📖 Funcionalidades](#-funcionalidades) · [⚙️ Instalação](#️-instalação-e-execução)

</div>

---

## 📋 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades](#-funcionalidades)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Pré-requisitos](#-pré-requisitos)
- [Instalação e Execução](#️-instalação-e-execução)
- [Deploy](#-deploy)
- [Como Usar a Aplicação](#-como-usar-a-aplicação)
- [Componentes React](#-componentes-react)
- [API Utilizada](#-api-utilizada)
- [Boas Práticas Aplicadas](#-boas-práticas-aplicadas)
- [Contribuindo](#-contribuindo)
- [Licença](#-licença)

---

## 📌 Sobre o Projeto

O **StyleWave Moda** é uma aplicação web SPA (Single Page Application) de uma loja de moda fictícia, desenvolvida como projeto educacional para demonstrar na prática o uso de tecnologias modernas de desenvolvimento front-end.

O projeto cobre desde a estruturação semântica com HTML5, passando por estilização responsiva com Tailwind CSS, até a componentização e gerenciamento de estado com React 18 e navegação com React Router v6 — tudo em um único arquivo HTML autocontido, sem necessidade de bundler ou instalação de dependências locais.

### 🎯 Objetivos do Projeto

- Demonstrar o uso de **React** com hooks (`useState`, `useEffect`, `useCallback`)
- Aplicar **componentização** com passagem de **Props**
- Implementar **roteamento** entre páginas com React Router
- Realizar **validação de formulários** em JavaScript puro
- Persistir dados no **LocalStorage** e usar **SessionStorage** para comunicação entre rotas
- Consumir uma **API externa** (ViaCEP) via Fetch API
- Aplicar **Tailwind CSS** com design responsivo (Flexbox, Grid, Media Queries)

---

## ✨ Funcionalidades

### 🏠 Página Inicial
- Vitrine de produtos com imagens responsivas em Grid Layout
- Tabela de produtos com nome, tamanho e preço
- Animação de entrada suave nas páginas (fade-in)

### 📝 Cadastro de Usuários
- Formulário com **6 campos** validados em tempo real
- Feedback visual imediato: borda **verde** (válido) e **vermelha** (inválido)
- Validações: nome completo, e-mail, CPF (11 dígitos), idade (18–120), senha (mín. 6 chars), confirmação de senha
- Botão de submit desabilitado enquanto o formulário for inválido
- Redirecionamento automático para a lista após o cadastro
- Suporte à **edição** de usuários existentes

### 👥 Lista de Usuários
- Tabela completa com todos os usuários cadastrados
- **Campo de busca** por nome ou e-mail em tempo real
- Ações de **Editar** (via SessionStorage) e **Excluir** (com confirmação)
- Contador de usuários cadastrados
- Dados persistidos no **LocalStorage**

### 📍 Consulta de CEP
- Busca via Fetch API na API pública **ViaCEP**
- Preenchimento automático de: rua, bairro, cidade e estado
- Ativação por botão ou tecla **Enter**
- Indicador de loading durante a requisição
- Mensagens de erro para CEP inválido ou falha de conexão

### 🧭 Navegação
- Menu lateral (desktop) / barra superior (mobile)
- Link ativo destacado com cor diferente via NavLink
- Rota `404` para URLs não encontradas
- Título da aba do navegador atualizado por página

---

## 🛠 Tecnologias Utilizadas

| Tecnologia | Versão | Finalidade |
|---|---|---|
| **HTML5** | — | Estrutura semântica (`<nav>`, `<header>`, `<main>`, `<footer>`) |
| **CSS3** | — | Animações, scrollbar, reset de Box Model |
| **Tailwind CSS** | 3.x (CDN) | Estilização responsiva, Flexbox, Grid, Media Queries |
| **React** | 18 (CDN) | Componentização, estado, ciclo de vida |
| **ReactDOM** | 18 (CDN) | Renderização no DOM Virtual |
| **React Router DOM** | 6 (CDN) | Roteamento entre páginas (HashRouter) |
| **Babel Standalone** | — | Transpilação de JSX no navegador |
| **ViaCEP API** | — | Consulta de endereços por CEP |
| **LocalStorage** | — | Persistência de usuários cadastrados |
| **SessionStorage** | — | Comunicação de estado entre rotas |

---

## 📁 Estrutura do Projeto

```
stylewave-moda/
│
├── index.html          # Arquivo principal — toda a aplicação
├── README.md           # Documentação do projeto
└── LICENSE             # Licença MIT (opcional)
```

> ℹ️ Por ser um projeto autocontido em um único arquivo HTML, todas as dependências são carregadas via CDN. Não há `package.json`, `node_modules` ou processo de build.

### Estrutura Interna dos Componentes React

```
App
├── HashRouter
│   ├── Navbar                    # Menu de navegação
│   ├── Header                    # Cabeçalho da loja
│   └── Routes
│       ├── / → HomePage
│       │   ├── ProductCard[]     # Card de produto (props: produto, tamanho, preco)
│       ├── /cadastro → CadastroPage
│       │   └── FormInput[]       # Input validado (props: id, type, value, error, touched...)
│       ├── /usuarios → UsuariosPage
│       │   └── UserRow[]         # Linha da tabela (props: usuario, index, onEdit, onDelete)
│       ├── /cep → CepPage
│       │   └── CepField[]        # Campo somente-leitura (props: label, value)
│       └── * → Página 404
```

---

## ✅ Pré-requisitos

Por ser um arquivo HTML puro com dependências via CDN, os requisitos são mínimos:

- **Navegador moderno** atualizado (Chrome 90+, Firefox 88+, Edge 90+, Safari 14+)
- **Conexão com a internet** para carregar as bibliotecas via CDN e consultar a API de CEP
- *(Opcional)* Um servidor HTTP local para desenvolvimento (ver seção abaixo)

> ⚠️ **Não** é necessário instalar Node.js, npm, ou qualquer dependência local para executar o projeto.

---

## ⚙️ Instalação e Execução

### Opção 1 — Abrir diretamente no navegador (mais simples)

```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/stylewave-moda.git

# 2. Acesse a pasta
cd stylewave-moda

# 3. Abra o arquivo no navegador
# No Linux/Mac:
open index.html

# No Windows:
start index.html
```

> ✅ Pronto! A aplicação abrirá no seu navegador padrão.

---

### Opção 2 — Servidor local com VS Code (recomendado para desenvolvimento)

1. Instale a extensão **Live Server** no VS Code
2. Abra a pasta do projeto no VS Code
3. Clique com o botão direito em `index.html`
4. Selecione **"Open with Live Server"**
5. Acesse `http://127.0.0.1:5500`

---

### Opção 3 — Servidor HTTP via Python

```bash
# Python 3
python3 -m http.server 8080

# Acesse no navegador:
# http://localhost:8080
```

---

### Opção 4 — Servidor HTTP via Node.js

```bash
# Instale o servidor global (apenas uma vez)
npm install -g http-server

# Na pasta do projeto:
http-server -p 8080

# Acesse no navegador:
# http://localhost:8080
```

---

### Opção 5 — Servidor HTTP via npx (sem instalação global)

```bash
npx serve .

# Acesse no navegador:
# http://localhost:3000
```

---

## 🚀 Deploy

Por ser um projeto estático (apenas HTML), pode ser publicado gratuitamente em diversas plataformas:

### GitHub Pages (recomendado)

```bash
# 1. Crie um repositório no GitHub chamado stylewave-moda

# 2. Inicialize o Git na pasta do projeto
git init
git add .
git commit -m "feat: projeto StyleWave Moda"

# 3. Conecte ao repositório remoto
git remote add origin https://github.com/seu-usuario/stylewave-moda.git

# 4. Envie o código
git push -u origin main

# 5. No GitHub, vá em:
#    Settings → Pages → Source → Deploy from branch → main → / (root)
#    Salve e aguarde alguns minutos.

# 6. Sua aplicação estará disponível em:
#    https://seu-usuario.github.io/stylewave-moda/
```

---

### Netlify (arrastar e soltar)

1. Acesse [netlify.com](https://netlify.com) e crie uma conta gratuita
2. No painel, clique em **"Add new site" → "Deploy manually"**
3. Arraste a **pasta do projeto** para a área indicada
4. Aguarde o deploy — URL gerada automaticamente (ex: `https://stylewave-abc123.netlify.app`)

**Via Netlify CLI:**
```bash
npm install -g netlify-cli
netlify login
netlify deploy --prod --dir .
```

---

### Vercel

```bash
npm install -g vercel
vercel login
vercel --prod
```

---

### Surge.sh

```bash
npm install -g surge
surge

# Siga as instruções no terminal.
# URL gerada: https://stylewave-moda.surge.sh (ou personalizada)
```

---

## 📖 Como Usar a Aplicação

### 🏠 Página Inicial

Ao abrir a aplicação, você verá a vitrine com imagens dos produtos e a tabela de catálogo. Use o menu lateral (desktop) ou a barra superior (mobile) para navegar entre as seções.

---

### 📝 Cadastrando um Usuário

1. Clique em **"Cadastro"** no menu
2. Preencha todos os campos do formulário:

   | Campo | Regra de validação |
   |---|---|
   | Nome completo | Deve conter nome e sobrenome |
   | E-mail | Formato válido (ex: nome@email.com) |
   | CPF | Exatamente 11 dígitos numéricos |
   | Idade | Entre 18 e 120 anos |
   | Senha | Mínimo de 6 caracteres |
   | Confirmar senha | Deve ser idêntica à senha |

3. Cada campo exibe feedback visual enquanto você digita:
   - 🟢 **Borda verde** + "✓ Válido" — campo correto
   - 🔴 **Borda vermelha** + mensagem de erro — campo inválido
4. Clique em **"✅ Cadastrar"** — você será redirecionado para a lista de usuários

---

### 👥 Gerenciando Usuários

1. Clique em **"Usuários"** no menu para ver todos os cadastrados
2. Use o **campo de busca** para filtrar por nome ou e-mail
3. Para **editar**: clique em **"✏️ Editar"** — o formulário abrirá preenchido com os dados
4. Para **excluir**: clique em **"🗑️ Excluir"** e confirme na caixa de diálogo
5. Os dados são salvos automaticamente no **LocalStorage** do navegador

> ⚠️ Limpar os dados do navegador apagará os usuários cadastrados.

---

### 📍 Consultando um CEP

1. Clique em **"CEP"** no menu
2. Digite um CEP com 8 dígitos (ex: `01310100`)
3. Pressione **Enter** ou clique em **"Buscar"**
4. Os campos de endereço serão preenchidos automaticamente:
   - CEP formatado, Rua, Bairro, Cidade e Estado

---

## 🧩 Componentes React

| Componente | Props | Descrição |
|---|---|---|
| `App` | — | Raiz da aplicação; gerencia estado global de usuários |
| `Navbar` | — | Menu de navegação com NavLink ativo |
| `Header` | — | Cabeçalho com nome da loja |
| `HomePage` | — | Página inicial com produtos e tabela |
| `ProductCard` | `produto`, `tamanho`, `preco` | Linha da tabela de produtos |
| `CadastroPage` | `usuarios`, `setUsuarios` | Formulário de cadastro/edição |
| `FormInput` | `id`, `type`, `placeholder`, `value`, `onChange`, `error`, `touched` | Input com validação visual |
| `UsuariosPage` | `usuarios`, `setUsuarios` | Lista de usuários com busca |
| `UserRow` | `usuario`, `index`, `onEdit`, `onDelete` | Linha da tabela de usuários |
| `CepPage` | — | Consulta de CEP via Fetch API |
| `CepField` | `label`, `value` | Campo somente-leitura do endereço |

---

## 🌐 API Utilizada

### ViaCEP

- **URL Base:** `https://viacep.com.br/ws/{cep}/json/`
- **Método:** `GET`
- **Autenticação:** Não requerida
- **Gratuita:** Sim

**Exemplo de resposta:**
```json
{
  "cep": "01310-100",
  "logradouro": "Avenida Paulista",
  "bairro": "Bela Vista",
  "localidade": "São Paulo",
  "uf": "SP"
}
```

**Documentação:** [viacep.com.br](https://viacep.com.br/)

---

## ✔️ Boas Práticas Aplicadas

- **HTML5 Semântico:** uso de `<nav>`, `<header>`, `<main>`, `<footer>`, `<section>`
- **Box Model:** reset com `box-sizing: border-box`
- **Flexbox:** layout principal, navbar e inputs
- **Grid Layout:** galeria de imagens e campos de CEP
- **Media Queries:** comportamento adaptado via classes Tailwind `md:`
- **Componentização:** cada elemento de UI é um componente React isolado e reutilizável
- **Props tipadas:** todos os componentes recebem e documentam suas props
- **Imutabilidade de estado:** arrays de usuários sempre copiados antes de modificar
- **useCallback:** funções de edição/exclusão memoizadas para evitar re-renders
- **Lazy initialization:** `useState(() => JSON.parse(...))` para leitura única do LocalStorage
- **Async/Await:** código assíncrono legível na consulta de CEP
- **Tratamento de erros:** try/catch no Fetch e validação de resposta da API
- **Feedback ao usuário:** loading, mensagens de sucesso e de erro
- **Acessibilidade:** `lang`, `charset`, `viewport` e `alt` nas imagens configurados

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Siga os passos:

```bash
# 1. Faça um fork do repositório
# 2. Crie uma branch para sua feature
git checkout -b feature/minha-melhoria

# 3. Faça suas alterações e commit
git commit -m "feat: adiciona minha melhoria"

# 4. Envie para o GitHub
git push origin feature/minha-melhoria

# 5. Abra um Pull Request
```

### Convenção de Commits

| Prefixo | Uso |
|---|---|
| `feat:` | Nova funcionalidade |
| `fix:` | Correção de bug |
| `style:` | Alterações de estilo/CSS |
| `refactor:` | Refatoração de código |
| `docs:` | Atualização de documentação |

---

## 📄 Licença

Este projeto está sob a licença **MIT**. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

<div align="center">

Desenvolvido com ❤️ — **StyleWave Moda**

⭐ Se este projeto foi útil, deixe uma estrela no repositório!

</div>
