# Regras de Negócio - Sistema ReMed.io
> Nesta seção são apresentadas as regras de negócio do sistema, baseadas na modelagem atualizada e nas funcionalidades propostas.

## Objetivos do Sistema

- Gerenciar produtos farmacêuticos, de cuidados pessoais e suplementos alimentares.
- Controlar o estoque (incluindo entradas, saídas e quantidade mínima).
- Monitorar a validade dos produtos e bloquear o uso de itens vencidos.
- Registrar e rastrear movimentações de estoque.
- Associar produtos a fornecedores.
- Emitir alertas de estoque baixo e vencimento próximo.
- Garantir autenticação e controle de acesso por meio de contas de funcionários.

---

## Modelagem de Estoque — Descrição Geral

### **Separação entre Produto e ItemEstoque**

- **Produto (`ProdutoBase` e suas subclasses)** representa o catálogo de produtos da farmácia. Armazena informações descritivas como: 
    
    - Nome
    - Descrição
    - **`Medicamento`:** Tarja, necessidade de receita, dosagem, principio ativo, forma farmaceutica e via de administração
    - **`CuidadoPessoal`:** Subcategoria, formato, quantidade, volume, uso recomendado, publico alvo 
    - **`SuplementoAlimentar`:** Tipo, peso(volume), sabor e restrição
  
  > ⚠️ Produtos não possuem informações operacionais como preço, validade ou quantidade — essas informações estão no `ItemEstoque`.

- **ItemEstoque** representa uma unidade física ou lote de um produto dentro da farmácia. Contém informações operacionais:

    - Código de barras
    - Preço de venda
    - Data de validade
    - Fornecedor associado

> **Analogia:**  
`ProdutoBase`: *"Dipirona 500mg comprimido"*  
`ItemEstoque`: *"Caixa de Dipirona 500mg, validade 05/2026, preço R$10,00, fornecedor Farmac Distribuidora"*


### **Gestão de Estoque e Armazem**

- A classe **Armazem** representa os locais de armazem, que podem ser físicos (ex.: estoque central, balcão) ou lógicos (ex.: estoque de cosméticos).
- Cada armazém possui uma lista de **`ItemEstoque`** e controla:

    - Quantidade atual
    - Quantidade mínima (para disparo de alertas)
    - Localização dos produtos
    - Validade dos itens (permitindo identificar vencidos ou próximos do vencimento)


### **Movimentação de Estoque**

- Toda entrada (compra, reposição) ou saída (venda, descarte) de itens gera uma **MovimentacaoEstoque**, que:

    - Possui data, tipo (`Entrada` ou `Saída`), quantidade e item associado.
    - Atualiza automaticamente a quantidade disponível no armazém.
    - Mantém um histórico rastreável de movimentações.


### **Autenticação e Controle de Acesso**

- O sistema requer que ações críticas (como movimentações de estoque) sejam realizadas por um **Funcionario autenticado**.
- A classe **Funcionario** armazena as credenciais de acesso e informações do colaborador, incluindo:

        • Nome  
        • CPF  
        • E-mail  
        • Hash da senha  
        • Cargo  
        • Data de contratação

- A autenticação garante a segurança do sistema e permite auditoria de ações sensíveis.


---

## Regras de Negócio Aplicadas

- **Controle de movimentação de item sem estoque suficiente**: Nenhuma saída pode ser registrada se a quantidade disponível for insuficiente.
- **Controle de produtos vencidos**: Itens vencidos não podem ser movimentados para uso ou distribuição (checado via método `checar_validade()`).
- **Controle de quantidade mínima em estoque**: Alertas são emitidos automaticamente caso a quantidade de um item atinja ou fique abaixo da quantidade mínima estabelecida.
- **Rastreabilidade de movimentações**: Todas as movimentações de estoque são registradas com informações do produto, lote e data, garantindo rastreabilidade conforme exigências legais.
- **Controle de acesso por funcionário**: Apenas usuários autenticados com perfil de funcionário podem registrar movimentações ou visualizar dados sensíveis do estoque.

