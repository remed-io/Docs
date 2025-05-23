# Product Backlog — Sistema **ReMed.io**

> Este backlog contém as funcionalidades principais do sistema, baseadas no [Diagrama de Classe](index.md) e nas regras de negócio do sistema ReMed.io.

---

## Board Kanban

### 🔴 Histórias

---

#### História 1 — Cadastro de Produtos (Catálogo)
**Como** administrador  
**Quero** cadastrar produtos no catálogo  
**Para** organizar os tipos de produtos que a farmácia comercializa  

**Critérios de aceitação:** 

- Deve ser possível cadastrar produtos base, vinculando-os a uma subcategoria: Medicamento, Cosmético ou Suplemento Alimentar.  
- Cada subclasse deve conter atributos específicos (ex.: tarja para medicamentos, tipo de pele para cosméticos, sabor para suplementos).  
- Este cadastro não contém informações operacionais como preço, validade ou quantidade — apenas dados descritivos.  

---

#### História 2 — Cadastro de Fornecedores
**Como** administrador  
**Quero** cadastrar fornecedores  
**Para** associá-los aos lotes de produtos adquiridos  

**Critérios de aceitação:**  

- Cadastro de nome, CNPJ, telefone, e-mail e endereço.  
- Fornecedor pode ser associado a diferentes lotes (`ItemEstoque`).  

---

#### História 3 — Cadastro de Armazéns
**Como** administrador  
**Quero** cadastrar locais de armazenamento  
**Para** organizar onde os produtos estão fisicamente ou logicamente armazenados  

**Critérios de aceitação:**  

- Cadastro do nome do armazém (ex.: Estoque Central, Balcão, Cosméticos).  
- Definição de quantidade mínima para cada produto nesse armazém (para alertas de estoque baixo).  

---

#### História 4 — Cadastro de Itens de Estoque 
**Como** administrador  
**Quero** cadastrar itens de estoque  
**Para** controlar validade, preço e fornecedor de cada entrada de produto  

**Critérios de aceitação:**  

- Cadastro de código de barras, preço de venda, data de validade, fornecedor e armazém.  
- Cada `ItemEstoque` está vinculado a um `ProdutoBase`.  

---

#### História 5 — Movimentação de Estoque (Entradas e Saídas)
**Como** administrador  
**Quero** registrar entradas e saídas de estoque  
**Para** manter o controle atualizado dos produtos disponíveis  

**Critérios de aceitação:**  

- Movimentação deve conter: data, tipo (entrada ou saída), quantidade, e item de estoque (lote).  
- Deve atualizar automaticamente a quantidade no armazém.  
- Valida se há saldo suficiente para saídas.  

---

#### História 6 — Consulta e Monitoramento de Estoque
**Como** administrador  
**Quero** consultar o estoque atual  
**Para** verificar quantidades, validade, localização e status dos produtos  

**Critérios de aceitação:**  

- Listagem de quantidade atual, validade, armazém e fornecedor dos itens.  
- Destacar produtos vencidos ou com estoque abaixo do mínimo.  

---

#### História 7 — Venda de Produtos com Rastreamento de Lote (Itens de estoque)

**Como** atendente  
**Quero** realizar vendas selecionando itens específicos do estoque  
**Para** garantir rastreabilidade dos lotes e validade  

**Critérios de aceitação:**  

- A venda deve permitir selecionar quais lotes estão sendo vendidos.  
- Impede a venda de produtos vencidos.  
- Calcula automaticamente o valor total.  
- Gera comprovante textual da venda com detalhes dos itens (incluindo lote e validade).  

---

#### História 8 — Relatório de Produtos Vencidos e Próximos do Vencimento
**Como** administrador  
**Quero** gerar relatórios de produtos vencidos ou prestes a vencer  
**Para** tomar decisões de descarte ou promoção dos produtos  

**Critérios de aceitação:** 

- Listagem de produtos com validade expirada ou a vencer em até X dias (parâmetro configurável).  

---

#### História 9 — Relatório de Movimentações de Estoque
**Como** administrador  
**Quero** gerar um relatório de movimentações  
**Para** acompanhar todo o histórico de entradas e saídas do estoque  

**Critérios de aceitação:**

- Relatório deve incluir: data, tipo de movimentação, quantidade, item de estoque (produto + lote), e armazém.  

---

#### História 10 — Alerta de Estoque Crítico
**Como** administrador  
**Quero** receber alertas de estoque crítico  
**Para** evitar falta de produtos essenciais  

**Critérios de aceitação:**  

- O sistema deve emitir alertas sempre que a quantidade de um item estiver igual ou abaixo da quantidade mínima definida para o armazém.  

---

## 🟡 Em andamento  
*Histórias que estão em desenvolvimento.*  

## 🟢 Concluído  
*Histórias que já foram finalizadas.*  
