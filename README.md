# Fundamentos do GraphQL na prática (Node.js + React)

Projeto de exemplo que demonstra uma API GraphQL com Node.js (type-graphql + Apollo Server) e um cliente React usando Apollo Client.

## Estrutura principal
- Backend: [backend/index.ts](backend/index.ts) — monta o servidor GraphQL e gera o schema em [backend/schema.gql](backend/schema.gql)
  - Resolvers: [`UserResolver`](backend/src/resolvers/UserResolver.ts)
  - Models: [`User`](backend/src/models/User.ts)
- Frontend: app React com Vite
  - Query/lista de usuários: [`GET_USER`](frontend/src/App.tsx) em [frontend/src/App.tsx](frontend/src/App.tsx)
  - Formulário para criar usuário: [`NewUserForm`](frontend/src/components/NewUserForm.tsx) em [frontend/src/components/NewUserForm.tsx](frontend/src/components/NewUserForm.tsx)
  - Cliente Apollo: [`client`](frontend/src/lib/apollo.ts) em [frontend/src/lib/apollo.ts](frontend/src/lib/apollo.ts)

## Rápido guia de execução

1. Backend
```sh 
cd backend
npm install
npm run dev
```

O servidor inicia e exibe a URL do GraphQL (ver backend/index.ts). O schema GraphQL é salvo automaticamente em backend/schema.gql.

2. Frontend
```sh 
cd frontend
npm install
npm run dev
```

A aplicação React consome a API em http://localhost:4000 (configuração em client).

### Exemplos de uso
Query para listar usuários (usada em GET_USER):

``` sh
query {
  users {
    id
    name
  }
}
```
* Mutation para criar usuário (usada em NewUserForm):

``` sh
mutation CreateUser($name: String!) {
  createUser(name: $name) {
    id
    name
  }
}
```
## Notas
O schema é gerado automaticamente pelo TypeGraphQL a partir dos decorators em User e UserResolver.
Dependências principais:
Backend: ver package.json
Frontend: ver package.json