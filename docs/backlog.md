# Product Backlog

> Este backlog contém as funcionalidades principais do sistema, com base nas histórias de usuários definidas a partir do [Diagrama de Classe](index.md).

---

## Board Kanban

### 🔴 Histórias

#### História 1 — Cadastro de Produtos
**Como** administrador  
**Quero** cadastrar produtos no sistema  
**Para** manter o controle de estoque

**Critérios de aceitação:**

 - Deve ser possível cadastrar: código de barras, nome, preço, validade e fornecedor.
 - Produto deve pertencer a uma subcategoria: Medicamento, Cosmético ou Suplemento.
 - Cada subclasse deve aceitar atributos específicos:

    - **Medicamento**: tarja, necessita receita, princípio ativo.
    - **Cosmético**: tipo de pele, faixa etária.
    - **Suplemento Alimentar**: sabor, tipo, restrições.

---

#### História 2 — Cadastro de Fornecedores
**Como** administrador  
**Quero** cadastrar fornecedores  
**Para** associá-los aos produtos da farmácia

**Critérios de aceitação:**

- Deve ser possível cadastrar nome, CNPJ e dados de contato.

---

#### História 3 — Cadastro de Estoque
**Como** administrador  
**Quero** registrar dados de estoque  
**Para** manter controle da localização e quantidade mínima

**Critérios de aceitação:**

- Deve ser possível definir local de armazenamento, quantidade mínima e quantidade atual.

---

#### História 4 — Movimentação de Estoque
**Como** administrador  
**Quero** registrar entradas e saídas de produtos  
**Para** atualizar corretamente o estoque

**Critérios de aceitação:**

- A movimentação deve ter data, tipo (entrada/saída), quantidade e produto.
- Deve atualizar automaticamente a quantidade atual no estoque.

---

#### História 5 — Consulta de Estoque
**Como** administrador  
**Quero** consultar os dados do estoque  
**Para** acompanhar a quantidade atual e validade dos produtos

**Critérios de aceitação:**

- Deve listar quantidade, localização e validade.
- Produtos vencidos ou com estoque abaixo do mínimo devem ser destacados.

---

#### História 6 — Relatório de Produtos Vencidos
**Como** administrador  
**Quero** gerar um relatório de produtos vencidos  
**Para** tomar ações corretivas no estoque

**Critérios de aceitação:**

- Deve listar produtos cujo campo validade já passou.

---

#### História 7 — Relatório de Movimentações
**Como** administrador  
**Quero** gerar relatórios de movimentações  
**Para** visualizar o histórico de entradas e saídas

**Critérios de aceitação:**

- Deve conter data, tipo, quantidade e produto.

---

#### História 8 — Registro de Venda
**Como** atendente  
**Quero** registrar vendas de produtos  
**Para** realizar o controle financeiro

**Critérios de aceitação:**

- Deve ser possível selecionar um ou mais produtos.
- Deve calcular o valor total automaticamente.
- Deve gerar comprovante textual.

---

### 🟡 Em andamento

*histórias que estão em desenvolvimento.*

---

### 🟢 Concluído

*histórias que já foram finalizadas.*

