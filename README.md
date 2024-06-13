#  Disciplina: Desenvolvimento de Aplicações Web II

## Professor:  [Otávio Lube dos Santos](https://www.linkedin.com/in/otaviolube/)🔗

# 📘 Projeto Prático da C2 e C3

Este repositório contém o projeto prático desenvolvido nas disciplinas C2 e C3, conforme discutido em sala de aula. O projeto consiste na implementação de uma API utilizando Node.js, TypeScript, Prisma e um banco de dados à sua escolha (sugestão: SQLite).

## 📋 Descrição do Projeto

### C2: Implementação da API com Node.js, TypeScript e Prisma

O objetivo principal da C2 é a criação de uma API seguindo o padrão MVC (Model-View-Controller). A implementação será baseada nos modelos existentes no Prisma Quickstart ([Prisma Quickstart](https://www.prisma.io/docs/getting-started/quickstart)). 

#### Funcionalidades:
- **Modelo de Comentários:**
  - Um Post possui vários Comentários.
  - Cada Comentário pertence a um único Post.
  - Um Usuário pode fazer vários Comentários.

### C3: Autenticação com Tokens JWT

O objetivo principal da C3 é a implementação de um mecanismo de autenticação utilizando Tokens JWT (JSON Web Tokens) para a API desenvolvida na C2.

#### Funcionalidades:
- **Rotas de Autenticação:**
  - **Cadastro de Usuários:** Rota para cadastro de novos usuários.
  - **Login de Usuários:** Rota para login de usuários, emitindo um token JWT.

### 🚀 Tecnologias Utilizadas
- Prisma ORM
- Visual Studio Code
- Thunder Client
- SQLite
- Node.js
- TypeScript
- Swagger
- JWT
- Docker

![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white)
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![Swagger](https://img.shields.io/badge/-Swagger-%23Clojure?style=for-the-badge&logo=swagger&logoColor=white)
![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-3982CE?style=for-the-badge&logo=Prisma&logoColor=white)
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
--- 

## 📂 Estrutura do Projeto

```bash
.
├── src
├── controller
│   ├── AuthController.ts
│   ├── CommentController.ts
│   ├── PostController.ts
│   └── UserController.ts
├── middlewares
│   └── autorizacao.ts
├── routes
│   ├── AuthRoutes.ts
│   ├── CommentRoutes.ts
│   ├── PostRoutes.ts
│   └── UserRoutes.ts
├── service
│   ├── AuthDataBaseService.ts
│   ├── CommentDataBaseService.ts
│   ├── PostDataBaseService.ts
│   └── UserDataBaseService.ts
├── utils
│    └── ComparadorDiaHoras.ts
├── prisma
│   ├── schema.prisma
│   └── migrations
├── Dockerfile
├── package.json
└── README.md
```

## 🔧 Configuração e Execução

### Pré-requisitos

- **Node.js** instalado
- **Docker** instalado (para implantação via Docker)

### Instalação

## 🚀 Rodando o Projeto

Para rodar o projeto, siga estas etapas:

1. Clone o repositório para o seu computador usando o seguinte comando:

    ```bash
    git clone https://github.com/ifeslopes/PROJETOWEB2.git
    ```

2. Navegue até o diretório do projeto:

    ```bash
    cd PROJETOWEB2
    ```

 # 🐳 Rodando Com Docker:
Se você tiver o Docker e o Docker Compose instalados, execute os seguintes comandos:


```bash
docker-compose up --build -d
 ```
Este comando irá construir as imagens do Docker e iniciar os contêineres em modo detached (em segundo plano).
para subir o contêineres:

```bash
docker compose up 
 ```
Se você não tiver o Docker instalado, siga para o passo 3 .
  
3. Execute o comando npm install para instalar todas as dependências do projeto:

 ```bash
    npm install package.json
 ```

4. Execute os comandos para gerar o banco de dados do Prisma com SQLite:

 ```bash
    npx prisma generate
    npx prisma migrate      
    npx prisma migrate --schema=./prisma/schema.prisma               
```
5. Execute um dos comandos abaixo,  npm run, dentro  da pasta backend, para api_dev para iniciar o servidor de desenvolvimento da API:

 ```bash
       npx ts-node-dev index.ts    
```
 ```bash
       npm run dev    
```
 ```bash
       npm run swagger    
```


Será iniciado um servidor local do frontend na seguinte URL:

```
http://localhost:3005/
```
---

## 📚 Endpoints da API

Aqui estão os principais endpoints da API, incluindo exemplos de requisições usando `curl`:

### 1. Criar Usuário

Cria um novo usuário na aplicação.

```sh
curl -X 'POST' \
  'http://localhost:3005/User' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "email": "user@gmail.com",
  "name": "beta teste",
  "password": "123"
}'
```

### 2. Login de Usuário

Realiza o login de um usuário existente, retornando um token JWT.

```sh
curl -X 'POST' \
  'http://localhost:3005/login' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "email": "user@gmail.com",
  "password": "123"
}'
```

### 3. Criar Post

Cria um novo post na aplicação. Requer autenticação via token JWT.

```sh
curl -X 'POST' \
  'http://localhost:3005/post' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6Mywibm9tZSI6ImJldGEgdGVzdGUiLCJpYXQiOjE3MTgzMTAzODAsImV4cCI6MTcxODMxMjE4MH0.DQRHbdN4wTGhtT6ohj5UmzclmTQzfR5Q5NqAYzZRVjs' \
  -H 'Content-Type: application/json' \
  -d '{
  "title": "Post Novo",
  "content": "Estou criando novo post."
}'
```

### 4. Criar Comentário

Cria um novo comentário em um post existente. Requer autenticação via token JWT.

```sh
curl -X 'POST' \
  'http://localhost:3005/Comment' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6Mywibm9tZSI6ImJldGEgdGVzdGUiLCJpYXQiOjE3MTgzMTAzODAsImV4cCI6MTcxODMxMjE4MH0.DQRHbdN4wTGhtT6ohj5UmzclmTQzfR5Q5NqAYzZRVjs' \
  -H 'Content-Type: application/json' \
  -d '{
  "content": "fazendo comentario post novo.",
  "postId": 2,
  "authorId": 2
}'
```
---
## 📤 Documentação da Api via Swagger:
```
http://localhost:3005/docs
```
![Logo do GitHub](imgreadme/Swagger.png)

---

Este README fornece uma visão geral clara e estruturada do projeto, incluindo seus objetivos, tecnologias utilizadas, estrutura do projeto e instruções para configuração e execução.<br>
💻 Desenvolvido por [Leonardo Lopes](https://github.com/ifeslopes)

![GitHub](https://img.shields.io/github/followers/ifeslopes?style=social)

