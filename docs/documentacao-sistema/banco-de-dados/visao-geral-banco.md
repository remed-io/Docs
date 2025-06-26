# Especificação do Banco de Dados

> Nesta seção é apresentada a especificação detalhada do banco de dados do sistema ReMed.io.

---

As tabelas principais incluem:

- `armazem`: armazena informações de locais fisicos de armazenamento.  
- `fornecedor`: armazena informações dos fornecedores.
- `funcionario`: contém dados dos funcionários que gerenciam o estoque.
- `item_armazenado`: relaciona itens do estoque com os locais de armazenamento.
- `movimentacao_estoque`: registra entradas e saídas de produtos.
- `medicamento`: contém dados dos medicamentos.
- `cuidado_pessoal`: para produtos de cuidado pessoal.
- `subcategoria_cuidado_pessoal`: relaciona produtos de cuidado pessoal com suas subcategorias.
- `suplemento_alimentar`: para suplementos alimentares.
- `restricao_alimentar`: armazena infoemações sobre restrições alimentares.
- `restricao_suplemento`: relaciona suplementos com restrições alimentares.
- `item_estoque`: relaciona produtos com informações fundamentais de estoque.

---

## Diagrama Entidade-Relacionamento (DER)
<br>
<p align="center">
    <a href="https://raw.githubusercontent.com/remed-io/Docs/refs/heads/main/docs/assets/remedio-db.png">
        <img src="/../../assets/remedio-db.png" alt="Diagrama Físico do Banco" width="600"/>
    </a>
</p>

---

## Regras de Integridade
- **Chaves Primárias**: Todas as tabelas possuem uma chave primária única.
- **Chaves Estrangeiras**: As relações entre tabelas são estabelecidas por chaves estrangeiras, garantindo integridade referencial.
- **Validações de Dados**: O backend valida os dados antes de inseri-los no banco, garantindo que atendam aos requisitos do modelo.
- **Relação de Medicamento, Cuidado Pessoal e Suplementos com Item Estoque**: Cada produto deve estar vinculado a um item de estoque, e cada item de estoque deve estar vinculado a um produto.
