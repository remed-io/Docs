# Fluxo de Dados Completo do Sistema ReMed.io

> Este documento descreve o fluxo completo de dados do sistema **ReMed.io**, desde a interação do usuário com a interface até o armazenamento e atualização de informações no banco de dados.

## Visão Geral

O sistema ReMed.io foi projetado para gerenciar o estoque de medicamentos de forma eficiente, garantindo rastreabilidade e controle de entrada e saída de produtos. O fluxo de dados contempla as seguintes etapas principais:

1. **Entrada de Dados** via Interface Web
2. **Envio de Requisição HTTP** para o Backend
3. **Validação e Processamento** pelo Backend (FastAPI)
4. **Persistência de Dados** no Banco PostgreSQL
5. **Resposta ao Cliente** e atualização da interface

---

## Descrição Detalhada

### 1. Interação com o Frontend (React)

O usuário interage com a interface para realizar ações como:

- Cadastro de novos medicamentos
- Atualização de estoque
- Visualização de itens armazenados
- Geração de relatórios

Cada ação aciona funções no React que disparam **requisições HTTP (via Axios)** para a API.

---

### 2. Processamento no Backend (FastAPI)

O backend recebe as requisições via rotas definidas no `main.py`, e realiza:

- **Validação de dados de entrada**
- **Execução de regras de negócio**
- **Interações com o banco via ORM ou SQL direto**

As operações são atomizadas, garantindo integridade dos dados.

---

### 3. Banco de Dados (PostgreSQL)

As tabelas principais incluem:

  - **`armazem`** 
  - **`fornecedor`**
  - **`funcionario`**
  - **`item_armazenado`**
  - **`movimentacao_estoque`**
  - **`medicamento`**
  - **`cuidado_pessoal`**
  - **`subcategoria_cuidado_pessoal`**
  - **`suplemento_alimentar`**
  - **`restricao_alimentar`**
  - **`restricao_suplemento`**
  - **`item_estoque`**

Os dados são inseridos, atualizados ou consultados conforme os comandos disparados pelo backend.

---

### 4. Resposta ao Frontend

Após processar a requisição, o backend envia uma resposta JSON contendo:

- Mensagem de sucesso ou erro
- Dados solicitados (em caso de GET)
- Novos estados para renderização na interface

O frontend atualiza dinamicamente os componentes com base nessa resposta.

---

## Considerações Técnicas

- Toda comunicação é feita via **API RESTful**
- A persistência garante **consistência transacional**
- Erros são tratados com respostas apropriadas (códigos HTTP + mensagens descritivas)
- As imagens do fluxo são mantidas na pasta `/assets/`

