<div align="center">
  <h1>RocketLog</h1>

  <p>
    API REST para gerenciamento de entregas de encomendas
  </p>

  <p>
    <a href="#️-tecnologias">Tecnologias</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
    <a href="#-projeto">Projeto</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
    <a href="#-estrutura">Estrutura</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
    <a href="#-api">API</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
    <a href="#️-configuração">Configuração</a>
  </p>
</div>

---

## 🛠️ Tecnologias

- Node.js
- TypeScript
- Express
- Prisma ORM
- PostgreSQL
- JWT
- bcrypt
- Zod
- Jest
- Docker

---

## 💡 Projeto

O **RocketLog** é uma API REST para gerenciamento de entregas de encomendas, desenvolvida para simular um sistema real de logística. A aplicação permite o controle de usuários, pedidos de entrega e o acompanhamento completo do fluxo de uma encomenda, desde sua criação até o registro de eventos que indicam seu progresso.

O projeto foi construído com foco em **arquitetura backend, segurança e consistência de dados**, utilizando autenticação baseada em JWT, modelagem relacional com PostgreSQL e regras de negócio bem definidas para refletir cenários reais de sistemas de entrega.

### Funcionalidades

- Cadastro e autenticação de usuários
- Criação e acompanhamento de entregas
- Atualização de status da entrega
- Registro de logs de cada etapa da entrega
- Controle de acesso por tipo de usuário (cliente e vendedor)

### Aplicação

- API REST com Express e TypeScript
- Autenticação e autorização com JWT
- Persistência de dados com Prisma e PostgreSQL
- Validação de dados com Zod
- Tratamento centralizado de erros
- Testes automatizados com Jest
- Separação de camadas (rotas, controllers, middlewares)

---

## 📁 Estrutura

```
src/
├── configs/           # Configurações (auth)
├── controllers/       # Regras de negócio
├── database/          # Conexão com o banco
├── middlewares/       # Autenticação e erros
├── routes/            # Rotas da API
├── tests/             # Testes unitários
├── utils/             # Utilitários (AppError)
├── app.ts             # Configuração do Express
└── server.ts          # Inicialização do servidor

prisma/
├── schema.prisma
└── migrations/

docker-compose.yml
```

---

## 🌐 API

### Autenticação

`POST /sessions`

```json
{
  "email": "user@example.com",
  "password": "123456"
}
```

---

### Usuários

`POST /users`

```json
{
  "name": "Bob Silva",
  "email": "bob@example.com",
  "password": "123456"
}
```

---

### Entregas

`POST /deliveries`

```json
{
  "description": "Electronics delivery"
}
```

`GET /deliveries`

`PUT /deliveries/:id/status`

```json
{
  "status": "shipped"
}
```

---

### Logs de Entrega

`POST /delivery-logs`

```json
{
  "description": "Package collected at warehouse",
  "deliveryId": "delivery-uuid"
}
```

`GET /delivery-logs/:deliveryId`

---

## ⚙️ Configuração

### 1. Instalar dependências

```bash
npm install
```

### 2. Configurar variáveis de ambiente

Crie um arquivo `.env`:

```
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/rocketlog"
JWT_SECRET="your-secret-key-here"
PORT=3333
```

### 3. Iniciar o banco com Docker

```bash
docker-compose up -d
```

### 4. Executar as migrations

```bash
npx prisma migrate dev
```

### 5. Iniciar o servidor

```bash
npm run dev
```

Será iniciada em:

```
http://localhost:3333
```

### 📦 Build para produção

Para gerar a versão otimizada:

```bash
npm run build
```

Os arquivos finais serão gerados na pasta `build/`.

Para executar a versão de produção localmente:

```bash
npm start
```

---

## 👨‍💻 Créditos

Thales Amaral Lima

Aplicação desenvolvida na Formação Fullstack da Rocketseat.
