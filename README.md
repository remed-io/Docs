# remed.io 🥼💊

**remed.io** é um sistema de estoque divertido e eficiente, que busca simplificar o controle de medicamentos e itens, trazendo praticidade e uma pitada de humor.

## Estrutura do Projeto

Este projeto está dividido em três partes principais:

- **[Frontend](https://github.com/remed-io/Frontend)**: Interface do usuário, desenvolvida com React.
- **[Backend-estoque](https://github.com/remed-io/Backend-estoque)**: A API que gerencia o estoque, construída com FastAPI.
- **[Docs](https://github.com/remed-io/Docs)**: Toda a documentação do projeto, incluindo diagramas, Product Backlog, e informações do desenvolvimento.

## Motivação do Nome

O nome "remed.io" é inspirado em medicamentos (remédios) e traz um toque cômico e divertido para um sistema de controle de estoque. A ideia é criar uma plataforma que "cuide" da saúde do estoque da sua farmácia de forma fácil e eficiente!

## Product Backlog

Acompanhe as tarefas e histórias de usuário no nosso [Product Backlog](link_para_o_backlog).

## Como Rodar o Projeto

### Backend

1. Clone o repositório do **Backend-estoque**.
2. Navegue até a pasta do backend e execute:

    ```bash
    docker-compose up
    ```

3. O servidor estará rodando no `http://localhost:8000`.

### Frontend

1. Clone o repositório do **Frontend**.
2. Navegue até a pasta do frontend e execute:

    ```bash
    npm install
    npm run dev
    ```

3. O frontend estará acessível em `http://localhost:3000`.

## Estrutura de Pastas

- **backend-estoque**:
  - `models/`: Classes Pydantic.
  - `schemas/`: DTOs.
  - `services/`: Regras de negócio.
  - `routes/`: Endpoints da API.
  - `tests/`: Testes unitários com pytest.

- **frontend**:
  - React App com estrutura básica e comunicação com o backend.

## Logo

A logo do projeto é uma representação divertida da ideia de remédios e saúde, com um estilo ácido e cômico. Confira no [README do Frontend](link_para_o_frontend) e [README do Docs](link_para_o_docs).
