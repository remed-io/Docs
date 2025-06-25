# Simulação de Cadastro de Produto no Item de Estoque

> Esta seção apresenta um passo a passo prático para simular o cadastro de diferentes tipos de produtos (medicamento, cuidado pessoal e suplemento alimentar) no módulo de `item_estoque` do sistema ReMed.io, utilizando exemplos de requisições HTTP.


## Pré-requisitos
- Backend rodando (FastAPI + Docker)
- Banco de dados inicializado
- Ferramenta de requisição HTTP (ex: Insomnia, Postman ou curl)

---

## 1. Cadastro de Fornecedor
Antes de cadastrar qualquer produto, cadastre um fornecedor:

```http
POST /fornecedor/
Content-Type: application/json

{
  "nome": "Fornecedor Exemplo",
  "cnpj": "12345678000199",
  "contato": "contato@exemplo.com"
}
```

---

## 2. Cadastro de Medicamento

```http
POST /medicamento/
Content-Type: application/json

{
  "nome": "Dipirona",
  "descricao": "Analgésico e antipirético",
  "dosagem": "500mg",
  "principio_ativo": "Dipirona Monoidratada",
  "tarja": "Sem tarja",
  "necessita_receita": false,
  "forma_farmaceutica": "Comprimido",
  "fabricante": "Farmaco S.A.",
  "registro_anvisa": "1234567890"
}
```

---

## 3. Cadastro de Cuidado Pessoal

Primeiro, cadastre uma subcategoria (se necessário):

```http
POST /subcategoria-cuidado-pessoal/
Content-Type: application/json

{
  "nome": "Higiene",
  "descricao": "Produtos de higiene pessoal"
}
```

Depois, cadastre o cuidado pessoal:

```http
POST /cuidado-pessoal/
Content-Type: application/json

{
  "nome": "Sabonete Líquido",
  "descricao": "Sabonete para mãos",
  "subcategoria_id": 1,
  "quantidade": "250ml",
  "volume": "250ml",
  "uso_recomendado": "Uso diário",
  "publico_alvo": "Adulto",
  "fabricante": "Higiene S.A."
}
```

---

## 4. Cadastro de Suplemento Alimentar

```http
POST /suplemento-alimentar/
Content-Type: application/json

{
  "nome": "Whey Protein",
  "descricao": "Suplemento proteico",
  "principio_ativo": "Proteína do soro do leite",
  "sabor": "Baunilha",
  "peso_volume": "900g",
  "fabricante": "Suplementos Brasil",
  "registro_anvisa": "9876543210"
}
```

---

## 5. Cadastro de Item de Estoque

### 5.1. Medicamento
```http
POST /item-estoque/
Content-Type: application/json

{
  "codigo_barras": "7891234567890",
  "preco": 12.50,
  "data_validade": "2026-12-31T00:00:00",
  "fornecedor_id": 1,
  "medicamento_id": 1
}
```

### 5.2. Cuidado Pessoal
```http
POST /item-estoque/
Content-Type: application/json

{
  "codigo_barras": "7899876543210",
  "preco": 8.90,
  "data_validade": "2025-10-15T00:00:00",
  "fornecedor_id": 1,
  "cuidado_pessoal_id": 1
}
```

### 5.3. Suplemento Alimentar
```http
POST /item-estoque/
Content-Type: application/json

{
  "codigo_barras": "7891112223334",
  "preco": 99.90,
  "data_validade": "2027-03-01T00:00:00",
  "fornecedor_id": 1,
  "suplemento_alimentar_id": 1
}
```

---

## Observações
- Os IDs utilizados nos exemplos (ex: `fornecedor_id`, `medicamento_id`, etc.) devem ser ajustados conforme o retorno das requisições de cadastro.
- Certifique-se de cadastrar apenas **um tipo de produto** por item de estoque.
- O campo `data_validade` deve estar no formato ISO 8601.
