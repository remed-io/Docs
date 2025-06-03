# Especificação do Banco de Dados

> Nesta seção é apresentada a especificação detalhada do banco de dados do sistema ReMed.io.

---

O banco de dados foi desenvolvido para gerenciar um sistema de estoque de produtos farmacêuticos e cosméticos, incluindo suplementos alimentares, medicamentos e cosméticos. Ele contempla controle de fornecedores, armazenamento, movimentação de estoque e vendas.

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
- Todas as chaves primárias são únicas e não nulas.
- Foreign Keys garantem integridade referencial entre as tabelas.
- Campos como `codigo_barras` e `nome_restricao` possuem restrições de unicidade.
- Movimentações possuem domínio restrito para o campo `tipo` ('entrada' ou 'saida').

---
