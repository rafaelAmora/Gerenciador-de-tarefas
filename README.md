# 🚀 TaskManager API

Um sistema completo de autenticação, gerenciamento de usuários, times e tarefas!  
Desenvolvido com **Express**, **Prisma**, **JWT**, **Zod** e **middlewares personalizados** para uma estrutura limpa, segura e escalável.

---

## 📦 Tecnologias

- **Node.js + Express** — API robusta e rápida
- **Prisma ORM** — mapeamento de banco de dados moderno
- **PostgreSQL (via Docker)** ou **SQLite** — flexível via `.env`
- **JWT** — autenticação segura
- **Zod** — validação de dados
- **Middlewares customizados** — para autenticação, autorização e erros

---

## 🚧 Pré-requisitos

- [Node.js](https://nodejs.org) (v18+ recomendado)
- [Yarn](https://yarnpkg.com) ou npm
- **Docker** e **Docker Compose** (caso use PostgreSQL)
- **Arquivo `.env` configurado**

---

## ⚙️ Configuração do projeto

```bash
# 1. Clone o repositório
git clone https://github.com/rafaelAmora/Gerenciador-de-tarefas.git

# 2. Acesse o diretório
cd sua-pasta

# 3. Instale as dependências
yarn install
# ou
npm install
🧪 Variáveis de ambiente
Crie um arquivo .env na raiz do projeto com as seguintes chaves:

env
JWT_SECRET=sua_chave_super_secreta
DATABASE_URL=postgresql://postgres:postgres@localhost:5432/taskmanager
🔒 JWT_SECRET deve ser uma string segura e longa.
🐘 DATABASE_URL se estiver usando PostgreSQL com Docker, use exatamente como acima.

🐳 Usando Docker + PostgreSQL
Você pode rodar um banco PostgreSQL facilmente com Docker:

docker-compose.yml
yaml
version: '3.8'

services:
  postgres:
    image: postgres:15
    container_name: taskmanager_postgres
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: taskmanager
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
Rode com:

bash
docker-compose up -d
🔄 Setup do banco de dados
bash
npx prisma migrate dev
Isso cria o banco, aplica as migrações e gera o Prisma Client automaticamente.

▶️ Rodando o projeto
bash
yarn dev
# ou
npm run dev
A API estará disponível em http://localhost:3333.

📂 Estrutura de pastas
├── prisma/                  # Migrations e schema do Prisma
├── src/
│   ├── config/              # Configurações globais
│   ├── controllers/         # Lógica dos endpoints
│   ├── db/                  # Instância do Prisma Client
│   ├── middlewares/         # Autenticação, validação, erros etc.
│   ├── routes/              # Definição das rotas da API
│   ├── types/               # Tipagens compartilhadas
│   ├── utils/               # Helpers e funções reutilizáveis
│   ├── app.ts               # Configuração principal da aplicação
│   ├── env.ts               # Carregamento e validação do .env
│   └── server.ts            # Inicialização do servidor
├── .env                     # Variáveis de ambiente (NÃO versionado)
├── .env-public.ts          # Chaves públicas (separadas por segurança)
├── .gitignore               # Arquivos ignorados pelo Git
├── docker-compose.yml      # PostgreSQL containerizado
├── package.json             # Scripts e dependências
├── package-lock.json        # Lockfile de dependências
├── README.md                # Este arquivo que você está lendo :)
└── tsconfig.json            # Configuração do TypeScript
🔐 Rotas protegidas
Algumas rotas requerem autenticação com token JWT no header:

Authorization: Bearer <token>
Use ferramentas como Insomnia ou Postman para testar.

✅ Boas práticas aplicadas
🔁 DRY com middlewares reutilizáveis

🧼 Validação de entrada com Zod

🔒 Segurança com JWT

🛠️ Código modularizado e fácil de manter
