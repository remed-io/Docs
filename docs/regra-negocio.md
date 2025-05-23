# Regras de Negócio - Sistema ReMed.io
> Nesta seção são apresentadas as regras de negócio do sistema, baseadas na modelagem atualizada e nas funcionalidades propostas. Este documento oferece uma visão clara e objetiva dos processos que serão implementados, alinhados com as práticas operacionais do setor farmacêutico.

## Objetivos do Sistema

- Gerenciar produtos farmacêuticos, cosméticos e suplementos alimentares.
- Controlar o estoque (incluindo entradas, saídas e quantidade mínima).
- Monitorar validade dos produtos e bloquear vendas de itens vencidos.
- Registrar e rastrear movimentações de estoque.
- Associar produtos a fornecedores.
- Registrar vendas, garantindo rastreabilidade dos lotes vendidos.
- Emitir alertas de estoque baixo e vencimento próximo.

---

## Modelagem de Estoque — Descrição Geral

### **Separação entre Produto e ItemEstoque**

- **Produto (`ProdutoBase` e suas subclasses)** representa o catálogo de produtos da farmácia. Armazena informações descritivas como: 
    
    - Nome
    - Descrição
    - volume
    - `medicamentos`: Tarja, necessidade de receita, dosagem, principio ativo, forma farmaceutica e via de administração
    - `consméticos`:Tipo e faixa etária 
    - `suplementos`:Tipo, sabor e restrição
  
  > ⚠️ Produtos não possuem informações operacionais como preço, validade ou quantidade — essas informações estão no `ItemEstoque`.

- **ItemEstoque** representa uma unidade física ou lote de um produto dentro da farmácia. Contém informações operacionais:

    - Código de barras
    - Preço de venda
    - Data de validade
    - Fornecedor associado

> **Analogia:**  
`ProdutoBase`: *"Dipirona 500mg comprimido"*  
`ItemEstoque`: *"Caixa de Dipirona 500mg, validade 05/2026, preço R$10,00, fornecedor Farmac Distribuidora"*


### **Gestão de Estoque e Armazenamento**

- A classe **Armazem** representa os locais de armazenamento, que podem ser físicos (ex.: estoque central, balcão) ou lógicos (ex.: estoque de cosméticos).
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


### **Processo de Venda**

- A venda é representada pela classe **Venda**, composta por um ou mais **ItemVenda**, cada um vinculado a um **`ItemEstoque`**.
- Permite:
    - Identificar exatamente qual lote foi vendido.
    - Associar preço, validade e fornecedor específicos do momento da venda.
    - Atender às exigências da vigilância sanitária sobre rastreabilidade.


---

## Regras de Negócio Aplicadas
- **Controle de venda de produto sem estoque**: Nenhuma venda pode ser realizada de um item que não tenha quantidade suficiente no estoque.
- **Controle de venda de produtos vencidos**Produtos vencidos não podem ser vendidos (checado via método checar_validade()).
- **Controle de quantidade de estoque**Alertas são emitidos caso a quantidade de um item atinja ou fique abaixo da quantidade mínima estabelecida.
- **Controle de rastreabilidade**: Todo produto vendido mantém vínculo com o lote específico (via ItemEstoque), permitindo rastreabilidade conforme exigências legais da vigilância sanitária.

