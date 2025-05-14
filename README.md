# remed.io 💊

O projeto consiste na reestruturação do projeto **[Farmácia da Marcia](https://github.com/acamposs/Projeto_oo1)** desenvolvido na disciplina Orientação a Objetos cursada no terceiro semestre do curso. O objetivo é melhorar o sistema aplicando conceitos adquiridos posteriormente no curso. 

O projeto consiste em um sistema de controle de estoque para farmácias, com foco na gestão eficiente de medicamentos e produtos farmacêuticos. 

## Estrutura do Projeto

Este projeto está dividido em três partes principais:

- **[Frontend](https://github.com/remed-io/Frontend)**: Interface do usuário, desenvolvida com React.
- **[Backend-estoque](https://github.com/remed-io/Backend-estoque)**: A API que gerencia o estoque, construída com FastAPI.
- **[Docs](https://github.com/remed-io/Docs)**: Toda a documentação do projeto, incluindo diagramas, Product Backlog, e informações do desenvolvimento.

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

