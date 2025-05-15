# Regras de Negócio - Sistema ReMed.io
> Nessa seção são apresentadas as regras de negócio do sistema baseadas nas melhorias e novas funcionalidades propostas para a aplicação, oferecendo uma visão clara e objetiva do que será implementado. 
## Objetivos do Sistema

- Armazenar e gerenciar produtos farmacêuticos e cosméticos.
- Controlar o estoque (entradas, saídas e quantidade mínima).
- Monitorar produtos vencidos.
- Registrar movimentações de estoque.
- Associar produtos a fornecedores.
- Registrar vendas de produtos (funcionalidade adicional para implementação futura).

---

## Novas Classes e Funcionalidades

### 1. Estoque

Armazena informações de controle de produtos no estoque.

**Atributos:**

 - `quantidadeAtual: int`
 - `quantidadeMinima: int`
 - `localArmazenamento: str`

**Métodos:**

- `adicionarQuantidade(qtd: int)`
- `removerQuantidade(qtd: int)`
- `verificarEstoqueMinimo() -> bool`
- `produtoVencido() -> bool`

---

### 2. MovimentacaoEstoque

Registra o histórico de entradas e saídas de produtos.

**Atributos:**

- `data: datetime`
- `tipo: str` (`Entrada` ou `Saída`)
- `quantidade: int`
- `produto: Produto`

---

### 3. Fornecedor

Representa o fornecedor dos produtos.

**Atributos:**

- `nome: str`
- `cnpj: str`
- `contato: str`

---

### 4. Venda 

*(Funcionalidade futura)*

Registra uma venda de um ou mais produtos.

**Atributos:**

- `dataVenda: datetime`
- `itens: List[ItemVenda]`
- `valorTotal: float`

---

### 5. ItemVenda

Representa um item dentro de uma venda.

**Atributos:**

- `produto: Produto`
- `quantidade: int`
- `precoUnitario: float`

---

## Melhorias nas Classes Existentes

### Farmacia

**Novos Atributos:**

- `estoque: List[Estoque]`
- `fornecedores: List[Fornecedor]`
- `movimentacoes: List[MovimentacaoEstoque]`

**Novos Métodos:**

- `consultarEstoque()`
- `registrarEntrada(produto, quantidade)`
- `registrarSaida(produto, quantidade)`
- `listarProdutosVencidos()`
- `relatorioMovimentacoes()`

---

### Produto 

**Novos Atributos:**

- `codigoBarras: str`
- `fornecedor: Fornecedor`

**Novos Métodos:**

- `verificarValidade()`
- `associarFornecedor(fornecedor: Fornecedor)`

---

## Subclasses de Produto

### 1. Medicamento

- `tarja: str` *(ex: preta, vermelha, isento)*
- `necessitaReceita: bool`
- `principioAtivo: str`

### 2. Cosmetico

- `tipoPele: str`
- `faixaEtaria: str`

### 3. SuplementoAlimentar

- `sabor: str`
- `tipo: str` *(proteína, multivitamínico, energético, etc.)*
- `restricoes: List[str]` *(ex: lactose, glúten)*
