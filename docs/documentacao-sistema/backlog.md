# Product Backlog — Sistema ReMed.io

> Nesta seção é apresentado o Product Backlog do sistema ReMed.io, contendo as histórias de usuário planejadas para o desenvolvimento do sistema usando o Kanban.

---

## Histórias

#### História 1 — Cadastro de Produtos (Catálogo)
**Como** administrador  
**Quero** cadastrar produtos no catálogo  
**Para** organizar os tipos de produtos que a farmácia comercializa  

**Critérios de aceitação:** 

- Deve ser possível cadastrar produtos base, vinculando-os a uma subcategoria: Medicamento, Cuidado Pessoal ou Suplemento Alimentar.  
- Cada subclasse deve conter atributos específicos (ex.: tarja para medicamentos, tipo de pele para cuidados pessoais, sabor para suplementos).  
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
**Quero** cadastrar locais de armazem  
**Para** organizar onde os produtos estão fisicamente ou logicamente armazenados  

**Critérios de aceitação:**  

- Cadastro do nome do armazém (ex.: Estoque Central, Balcão, Cuidados Pessoais).  
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
**Como** funcionário autenticado  
**Quero** registrar entradas e saídas de estoque  
**Para** manter o controle atualizado dos produtos disponíveis  

**Critérios de aceitação:**  

- Movimentação deve conter: data, tipo (entrada ou saída), quantidade e item de estoque (lote).  
- Deve atualizar automaticamente a quantidade no armazém.  
- Valida se há saldo suficiente para saídas.  
- Somente usuários autenticados com permissão de acesso podem realizar essa operação.  

---

#### História 6 — Consulta e Monitoramento de Estoque
**Como** funcionário autenticado  
**Quero** consultar o estoque atual  
**Para** verificar quantidades, validade, localização e status dos produtos  

**Critérios de aceitação:**  

- Listagem de quantidade atual, validade, armazém e fornecedor dos itens.  
- Destacar produtos vencidos ou com estoque abaixo do mínimo.  
- Requer autenticação para acesso.  

---

#### História 7 — Relatório de Produtos Vencidos e Próximos do Vencimento
**Como** administrador  
**Quero** gerar relatórios de produtos vencidos ou prestes a vencer  
**Para** tomar decisões de descarte ou promoção dos produtos  

**Critérios de aceitação:** 

- Listagem de produtos com validade expirada ou a vencer em até X dias (parâmetro configurável).  

---

#### História 8 — Relatório de Movimentações de Estoque
**Como** administrador  
**Quero** gerar um relatório de movimentações  
**Para** acompanhar todo o histórico de entradas e saídas do estoque  

**Critérios de aceitação:**  

- Relatório deve incluir: data, tipo de movimentação, quantidade, item de estoque (produto + lote), e armazém.  

---

#### História 9 — Alerta de Estoque Crítico
**Como** administrador  
**Quero** receber alertas de estoque crítico  
**Para** evitar falta de produtos essenciais  

**Critérios de aceitação:**  

- O sistema deve emitir alertas sempre que a quantidade de um item estiver igual ou abaixo da quantidade mínima definida para o armazém.  

---

#### História 10 — Autenticação de Funcionários
**Como** funcionário  
**Quero** me autenticar no sistema  
**Para** garantir acesso seguro às funcionalidades de estoque  

**Critérios de aceitação:**  

- O funcionário deve se autenticar utilizando e-mail e senha (armazenada como hash).  
- Apenas usuários autenticados têm permissão para acessar ou modificar dados sensíveis.  
- Dados do funcionário incluem nome, CPF, e-mail, cargo e data de contratação.  

---

## Board Kanban

| História                      | Implementada  | Observações                         |
| ----------------------------- | ------------- | ----------------------------------- |
| H1 — Produto Base             | ✅ Completo    | CRUDs completos para Medicamento, CuidadoPessoal, SuplementoAlimentar |
| H2 — Fornecedor               | ✅ Completo    | CRUD completo com validação CNPJ |
| H3 — Armazéns                 | ✅ Completo    | CRUD completo + campo quantidade_minima implementado |
| H4 — Itens de Estoque         | ✅ Completo    | CRUD completo com relacionamentos |
| H5 — Movimentação Estoque     | ✅ Completo    | CRUD + lógica atualizar estoque + auth obrigatória |
| H6 — Consulta Estoque         | ✅ Completo    | Endpoints implementados com filtros avançados + auth |
| H7 — Relatório Vencidos       | ✅ Completo    | Relatórios completos + exportação CSV + filtros |
| H8 — Relatório Movimentações  | ✅ Completo    | Relatórios completos + exportação CSV + filtros |
| H9 — Alerta Estoque Crítico   | ✅ Completo    | Sistema completo de alertas + dashboard + configurações |
| H10 — Autenticação            | ✅ Simplificado | Login básico implementado (sem JWT) |
