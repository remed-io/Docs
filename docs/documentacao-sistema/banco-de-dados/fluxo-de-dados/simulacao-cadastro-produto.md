# Simulação de Cadastro de um Produto no Estoque 

> Esta seção apresenta um passo a passo prático para simular o cadastro de diferentes tipos de produtos (medicamento, cuidado pessoal e suplemento alimentar) no estoque do sistema ReMed.io, passando pela principal função do projeto.

---

## Pré-requisitos

Antes de iniciar, certifique-se de que:

- O **container do backend** esteja em execução (`docker-compose up`).
- O **banco de dados** esteja corretamente inicializado (`init.sql` já executado).
- Você tenha acesso a uma **ferramenta de requisição HTTP** (como Insomnia, Postman ou Swagger UI).
- A aplicação esteja acessível em `http://localhost:8000/docs` (interface Swagger).

---

## Etapas do Cadastro

O processo é dividido nas seguintes etapas:

1. [Acesso ao Swagger e verificação da API](#1-acesso-ao-swagger-e-verificação-da-api)  
2. [Cadastro de um Fornecedor](#2-cadastro-de-um-fornecedor)  
3. [Cadastro de um Produto (Medicamento, Cuidado Pessoal ou Suplemento Alimentar)](#3-cadastro-de-um-produto)  
4. [Cadastro de Item no Estoque](#4-cadastro-do-item-no-estoque)

---

## 1. Acesso ao Swagger e Verificação da API

- Abra seu navegador e acesse: [`http://localhost:8000/docs`](http://localhost:8000/docs)
- Você verá a interface interativa do **Swagger UI**, com todos os endpoints do sistema listados.
- Expanda os endpoints que você utilizará: `/fornecedor/`, `/medicamento/`, `/cuidado-pessoal/`, `/suplemento-alimentar/`, `/item-estoque/`.

---


## 2. Cadastro de um Fornecedor
> O fornecedor é uma entidade obrigatória para qualquer item de estoque.

  - Acesse `POST /fornecedor/`
  - Adicione os seguintes dados no corpo da requisição:

```json
    {
      "nome": "Fornecedor Exemplo",
      "cnpj": "12345678000199",
      "contato": "contato@exemplo.com"
    }
```

---

## 3. Cadastro de Produtos

Você pode cadastrar **apenas um tipo de produto por item de estoque**. Escolha um dos tipos abaixo:
> ⚠️ Anote o `id` retornado do produto cadastrado, pois será necessário para o próximo passo.

### 3.1. Medicamento

 - Acesse `POST /medicamento/`
 - Exemplo de corpo da requisição:

```json
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

### 3.2 Cuidado Pessoal

> Antes de cadastrar um cuidado pessoal, é necessário cadastrar uma subcategoria (se ainda não existir).

 - Acesse `POST /cuidado-pessoal/`
 - Exemplo de corpo da requisição:

```json
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

**3.2.1 Cadastro de Subcategoria (opcional)**

> Esta etapa é necessária apenas para produtos do tipo **Cuidado Pessoal**.

- Acesse `POST /subcategoria-cuidado-pessoal/`
- Exemplo de corpo da requisição:

```json
    {
      "nome": "Higiene Pessoal",
      "descricao": "Produtos para cuidados diários"
    }
```

### 3.3 Suplemento Alimentar

 - Acesse `POST /suplemento-alimentar/`
 - Exemplo de corpo da requisição:

```json
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

**3.3.1 Cadastro de Restrição Alimentar (opcional para suplementos)**

> Para suplementos alimentares, é possível cadastrar restrições alimentares e associá-las ao suplemento.

- Acesse `POST /restricao-alimentar/`
- Exemplo de corpo da requisição:

```json
    {
      "nome": "Lactose"
    }
```

Repita para cada restrição desejada (ex: Glúten, Açúcar, etc).

**3.3.2 Associação de Restrição ao Suplemento Alimentar**

- Acesse `POST /restricao-suplemento/`
- Exemplo de corpo da requisição:

```json
    {
      "suplemento_alimentar_id": 1,
      "restricao_alimentar_id": 1,
      "severidade": "grave",
      "observacoes": "Contém traços de lactose."
    }
```

> Repita para cada restrição que deseja associar ao suplemento.

---

## 4. Cadastro do Item no Estoque

Agora com o `fornecedor` e o `id` do produto cadastrados, você pode criar um item no estoque.

- Acesse `POST /item-estoque/`
- Envie o JSON correspondente ao tipo de produto cadastrado. 

**Exemplo para um medicamento:**
```json
    {
      "codigo_barras": "7891234567890",
      "preco": 12.50,
      "data_validade": "2026-12-31T00:00:00",
      "fornecedor_id": 1,
      "medicamento_id": 1
    }
```

 **Exemplo para um cuidado pessoal:**

```json
    {
      "codigo_barras": "7891234567891",
      "preco": 8.99,
      "data_validade": "2025-06-30T00:00:00",
      "fornecedor_id": 1,
      "cuidado_pessoal_id": 1
    }
```

 **Exemplo para um suplemento alimentar:**

```json
    {
      "codigo_barras": "7891234567892",
      "preco": 45.00,
      "data_validade": "2027-03-15T00:00:00",
      "fornecedor_id": 1,
      "suplemento_alimentar_id": 1
    }
```
---

## Observações Finais

 - Os `ids` nos exemplos são ilustrativos. Use os valores reais retornados pelas requisições anteriores.

 - Apenas **um tipo de produto** deve estar presente no item-estoque.

 - Os campos devem estar em conformidade com os tipos definidos no Swagger.

 - O campo `data_validade` deve estar no **formato ISO 8601.**

 - Caso algum erro ocorra, verifique se os IDs referenciados realmente existem.