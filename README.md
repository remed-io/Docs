# ReMed.io 🧪

Sistema completo de gerenciamento de estoque para farmácias, com controle de medicamentos, suplementos alimentares, produtos de cuidado pessoal, fornecedores, armazéns e rastreabilidade de movimentações.

---

## Visão Geral do Projeto

O projeto **ReMed.io** é composto por três repositórios principais:

- **Backend-estoque** ([link](https://github.com/remed-io/Backend-estoque)) — API RESTful desenvolvida em FastAPI e PostgreSQL, responsável por toda a lógica de negócio, persistência e regras de estoque.
- **Frontend** ([link](https://github.com/remed-io/Frontend)) — Aplicação web em React e TypeScript, interface amigável para interação com o sistema.
- **Docs** (este repositório) — Documentação técnica, diagramas, backlog, regras de negócio e guias de uso/teste.

---

## Tecnologias Utilizadas

- **Backend:** Python, FastAPI, SQLAlchemy, PostgreSQL, Docker
- **Frontend:** React, TypeScript, TailwindCSS
- **Documentação:** MkDocs, Markdown

---

## Arquitetura Geral

O sistema segue uma arquitetura modular, desacoplando backend, frontend e documentação. A comunicação entre frontend e backend é feita via API REST. O backend utiliza banco relacional PostgreSQL e é facilmente orquestrado via Docker Compose.

---

## Como rodar o projeto

Consulte os READMEs de cada repositório para instruções detalhadas:
- [Backend-estoque](https://github.com/remed-io/Backend-estoque)
- [Frontend](https://github.com/remed-io/Frontend)
- [Docs](https://github.com/remed-io/Docs)

---

## Sobre este repositório (Docs)

Aqui você encontra:
- Visão geral do sistema
- Product Backlog (Kanban, histórias de usuário)
- Dicionário de dados
- Diagramas (ER, classes, arquitetura)
- Regras de negócio
- Guias de uso e testes
- Histórico do projeto original

### Como visualizar a documentação

1. Instale o MkDocs:
   ```bash
   pip install mkdocs
   ```
2. Inicie o servidor de documentação:
   ```bash
   mkdocs serve
   ```
   Acesse em [http://localhost:8000](http://localhost:8000).

---

## Licença

MIT

