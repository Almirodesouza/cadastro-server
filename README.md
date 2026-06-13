<div align="center">

# 📦 cadastro-server

**API REST para cadastro de usuários**  
Servidor backend construído com Node.js, Express e Prisma ORM integrado ao MongoDB Atlas.

![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=for-the-badge&logo=prisma&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

</div>

---

## 📋 Sobre o projeto

O **cadastro-server** é a camada backend de um sistema fullstack de cadastro de usuários. Ele expõe uma API REST com as quatro operações do CRUD — criar, listar, atualizar e remover usuários — com dados persistidos no MongoDB Atlas via Prisma ORM.

Este servidor é consumido pelo frontend **[react-cadastro](https://github.com/Almirodesouza/react-cadastro)**, também desenvolvido por mim.

---

## 🚀 Tecnologias utilizadas

| Tecnologia | Versão | Função |
|---|---|---|
| Node.js | ≥ 18 | Runtime JavaScript |
| Express | ^5.2.1 | Framework HTTP |
| Prisma Client | 6.19 | ORM / acesso ao banco |
| Prisma CLI | 6.19 | Geração do schema e client |
| MongoDB Atlas | — | Banco de dados em nuvem |
| dotenv | ^17.4.2 | Gerenciamento de variáveis de ambiente |
| CORS | ^2.8.6 | Liberação de acesso ao frontend |

> O projeto utiliza **ES Modules** (`"type": "module"` no `package.json`).

---

## 📁 Estrutura do projeto

```
cadastro-server/
├── generated/
│   └── prisma/
│       └── client.js       # Prisma Client gerado (não editar manualmente)
├── prisma/
│   └── schema.prisma       # Schema do banco de dados (modelo User)
├── .vscode/                # Configurações do editor
├── server.js               # Ponto de entrada — rotas e configuração do servidor
├── .env                    # Variáveis de ambiente (não versionado)
├── .gitignore
├── package.json
└── package-lock.json
```

---

## ⚙️ Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- [Node.js](https://nodejs.org/) versão 18 ou superior
- [Git](https://git-scm.com/)
- Uma conta no [MongoDB Atlas](https://www.mongodb.com/atlas) com um cluster criado

---

## 🔧 Instalação e configuração

### 1. Clone o repositório

```bash
git clone https://github.com/Almirodesouza/cadastro-server.git
cd cadastro-server
```

### 2. Instale as dependências

```bash
npm install
```

### 3. Configure as variáveis de ambiente

Crie um arquivo `.env` na raiz do projeto:

```env
DATABASE_URL="mongodb+srv://<usuario>:<senha>@<cluster>.mongodb.net/<nome-do-banco>?retryWrites=true&w=majority"
```

> Substitua os valores pelos dados do seu cluster no MongoDB Atlas.

### 4. Gere o Prisma Client

```bash
npx prisma generate
```

O client será gerado em `./generated/prisma/client.js`, conforme configurado no `schema.prisma`.

---

## ▶️ Executando o servidor

```bash
npm run dev
```

O comando utiliza `node --watch server.js`, recurso nativo do Node.js 18+ que reinicia o servidor automaticamente ao salvar qualquer arquivo.

O servidor ficará disponível em:

```
http://localhost:3000
```

---

## 🔗 Endpoints da API

> Base URL: `http://localhost:3000`

### `GET /usuarios`
Retorna a lista de todos os usuários cadastrados.

**Resposta:** `200 OK`
```json
[
  {
    "id": "664f1a2b3c4d5e6f7a8b9c0d",
    "name": "Almiro de Souza",
    "email": "almiro@email.com",
    "age": 30
  }
]
```

---

### `POST /usuarios`
Cria um novo usuário.

**Body (JSON):**
```json
{
  "name": "Almiro de Souza",
  "email": "almiro@email.com",
  "age": 30
}
```

**Resposta:** `201 Created`
```json
{
  "id": "664f1a2b3c4d5e6f7a8b9c0d",
  "name": "Almiro de Souza",
  "email": "almiro@email.com",
  "age": 30
}
```

---

### `PUT /usuarios/:id`
Atualiza os dados de um usuário existente pelo `id`.

**Parâmetro de rota:** `id` — ID do usuário no MongoDB

**Body (JSON):**
```json
{
  "name": "Novo Nome",
  "email": "novo@email.com",
  "age": 25
}
```

**Resposta:** `200 OK` — retorna o usuário atualizado.

---

### `DELETE /usuarios/:id`
Remove um usuário pelo `id`.

**Parâmetro de rota:** `id` — ID do usuário no MongoDB

**Resposta:** `200 OK`
```json
{
  "message": "Usuário deletado com sucesso"
}
```

---

## 🔒 CORS

O servidor utiliza o middleware **cors** sem restrições de origem, permitindo que o frontend React (rodando em `http://localhost:5173` no desenvolvimento) consuma a API sem bloqueios.

---

## 🌐 Frontend relacionado

Este servidor é o backend do projeto:

👉 **[react-cadastro](https://github.com/Almirodesouza/react-cadastro)** — Interface React que consome esta API para realizar o cadastro, listagem, edição e remoção de usuários.

---

## 👤 Autor

**Almiro de Souza**  
Desenvolvedor Full Stack | Node.js · React · JavaScript · Prisma

[![GitHub](https://img.shields.io/badge/GitHub-Almirodesouza-181717?style=flat-square&logo=github)](https://github.com/Almirodesouza)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Almiro%20de%20Souza-0A66C2?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/almiro-de-souza)

---

## 📄 Licença

Este projeto está sob a licença **ISC**.
