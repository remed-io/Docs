# Dicionário de Dados

> Nesta seção é apresentado o dicionário de dados do banco de dados do sistema ReMed.io, fornecendo detalhes sobre as tabelas, campos e relacionamentos utilizados no sistema.

---
## Sumário

<ul style="list-style-type: none;">
    <li><a href="#tabela-armazem">Tabela <em>armazem</em></a></li>
    <li><a href="#tabela-fornecedor">Tabela <em>fornecedor</em></a></li>
    <li><a href="#tabela-funcionario">Tabela <em>funcionario</em></a></li>
    <li><a href="#tabela-medicamento">Tabela <em>medicamento</em></a></li>
    <li><a href="#tabela-cuidado_pessoal">Tabela <em>cuidado_pessoal</em></a></li>
    <li><a href="#tabela-suplemento_alimentar">Tabela <em>suplemento_alimentar</em></a></li>
    <li><a href="#tabela-item_estoque">Tabela <em>item_estoque</em></a></li>
    <li><a href="#tabela-item_armazenado">Tabela <em>item_armazenado</em></a></li>
    <li><a href="#tabela-movimentacao_estoque">Tabela <em>movimentacao_estoque</em></a></li>
    <li><a href="#tabela-subcategoria_cuidado_pessoal">Tabela <em>subcategoria_cuidado_pessoal</em></a></li>
    <li><a href="#tabela-restricao_alimentar">Tabela <em>restricao_alimentar</em></a></li>
    <li><a href="#tabela-restricao_suplemento">Tabela <em>restricao_suplemento</em></a></li>
</ul>

---

## Tabela *armazem*
| Campo          | Tipo         | PK | FK | Nullable | Descrição                         |
|----------------|--------------|----|----|----------|-----------------------------------|
| id             | SERIAL       | ✔️ |    | ❌       | ID do armazém                     |
| local_armazem  | VARCHAR(100) |    |    | ❌       | Localização do armazém (único)   |

---

## Tabela *fornecedor*
| Campo    | Tipo         | PK | FK | Nullable | Descrição                  |
|----------|--------------|----|----|----------|----------------------------|
| id       | SERIAL       | ✔️ |    | ❌       | ID do fornecedor           |
| nome     | VARCHAR(100) |    |    | ❌       | Nome do fornecedor         |
| cnpj     | VARCHAR(20)  |    |    | ❌       | CNPJ do fornecedor         |
| contato  | VARCHAR(100) |    |    | ✔️       | Contato (telefone/email)   |

---

## Tabela *funcionario*
| Campo            | Tipo         | PK | FK | Nullable | Descrição                          |
|------------------|--------------|----|----|----------|------------------------------------|
| id               | SERIAL       | ✔️ |    | ❌       | ID do funcionário                  |
| nome             | VARCHAR(50)  |    |    | ❌       | Nome completo                      |
| cpf              | VARCHAR(11)  |    |    | ❌       | CPF (único)                        |
| email            | VARCHAR(100) |    |    | ❌       | Email (único)                      |
| senha_hash       | VARCHAR(255) |    |    | ❌       | Hash da senha                      |
| cargo            | VARCHAR(50)  |    |    | ❌       | Cargo ou função                    |
| data_contratacao | TIMESTAMP    |    |    | ❌       | Data da contratação                |

---

## Tabela *medicamento*
| Campo               | Tipo         | PK | FK | Nullable | Descrição                           |
|---------------------|--------------|----|----|----------|-------------------------------------|
| id                  | SERIAL       | ✔️ |    | ❌       | ID do medicamento                   |
| nome                | VARCHAR(100) |    |    | ❌       | Nome do medicamento                 |
| descricao           | VARCHAR(255) |    |    | ✔️       | Descrição                           |
| dosagem             | VARCHAR(50)  |    |    | ✔️       | Dosagem (ex 500mg)                 |
| principio_ativo     | VARCHAR(100) |    |    | ✔️       | Princípio ativo                     |
| tarja               | VARCHAR(50)  |    |    | ✔️       | Cor da tarja                        |
| necessita_receita   | BOOLEAN      |    |    | ❌       | Se exige receita                    |
| forma_farmaceutica  | VARCHAR(50)  |    |    | ✔️       | Forma farmacêutica (ex comprimido)|
| fabricante          | VARCHAR(100) |    |    | ✔️       | Nome do fabricante                  |
| registro_anvisa     | VARCHAR(50)  |    |    | ✔️       | Registro ANVISA                     |

---

## Tabela *cuidado_pessoal*
| Campo           | Tipo         | PK | FK | Nullable | Descrição                                      |
|------------------|--------------|----|----|----------|------------------------------------------------|
| id               | SERIAL       | ✔️ |    | ❌       | ID do produto de cuidado pessoal              |
| nome             | VARCHAR(100) |    |    | ❌       | Nome do produto                               |
| descricao        | VARCHAR(255) |    |    | ✔️       | Descrição                                      |
| subcategoria_id  | INT          |    | ✔️ | ✔️       | FK SubcategoriaCuidadoPessoal(id)             |
| quantidade       | VARCHAR(20)  |    |    | ✔️       | Quantidade                                     |
| volume           | VARCHAR(20)  |    |    | ✔️       | Volume (ex 200ml)                             |
| uso_recomendado  | VARCHAR(100) |    |    | ✔️       | Ex uso diário, noturno                        |
| publico_alvo     | VARCHAR(50)  |    |    | ✔️       | Ex adulto, infantil                           |
| fabricante        | VARCHAR(100) |   |    | ✔️       | Fabricante                                     |

---

## Tabela *suplemento_alimentar*
| Campo             | Tipo         | PK | FK | Nullable | Descrição                                      |
|-------------------|--------------|----|----|----------|------------------------------------------------|
| id                | SERIAL       | ✔️ |    | ❌       | ID do suplemento                               |
| nome              | VARCHAR(100) |    |    | ❌       | Nome do suplemento                             |
| descricao         | VARCHAR(255) |    |    | ✔️       | Descrição                                      |
| principio_ativo   | VARCHAR(100) |    |    | ✔️       | Princípio ativo (se houver)                   |
| sabor             | VARCHAR(50)  |    |    | ✔️       | Sabor (ex morango, baunilha)                 |
| peso_volume       | VARCHAR(20)  |    |    | ✔️       | Peso ou volume                                 |
| fabricante        | VARCHAR(100) |    |    | ✔️       | Fabricante                                     |
| registro_anvisa   | VARCHAR(50)  |    |    | ✔️       | Registro ANVISA                                |

---

## Tabela *item_estoque*
| Campo                            | Tipo         | PK | FK | Nullable | Descrição                                                       |
|----------------------------------|--------------|----|----|----------|-----------------------------------------------------------------|
| id                               | SERIAL       | ✔️ |    | ❌       | ID do item em estoque                                          |
| codigo_barras                    | VARCHAR(80)  |    |    | ❌       | Código de barras (único)                                       |
| fornecedor_id                    | INT          |    | ✔️ | ❌       | FK Fornecedor(id)                                              |
| preco                            | DECIMAL(10,2)|    |    | ❌       | Preço                                                          |
| lote                             | VARCHAR(50)  |    |    | ❌       | Lote de fabricação                                             |
| data_fabricacao                  | DATE         |    |    | ✔️       | Data de fabricação                                             |
| data_validade                    | DATE         |    |    | ❌       | Data de validade                                               |
| produto_medicamento_id           | INT          |    | ✔️ | ✔️       | FK Medicamento(id) (se for medicamento)                        |
| produto_cuidado_pessoal_id       | INT          |    | ✔️ | ✔️       | FK CuidadoPessoal(id) (se for produto de cuidado pessoal)      |
| produto_suplemento_alimentar_id  | INT          |    | ✔️ | ✔️       | FK SuplementoAlimentar(id) (se for suplemento)                 |
| tipo_produto                     | VARCHAR(20)  |    |    | ❌       | ‘medicamento’, ‘cuidado_pessoal’ ou ‘suplemento_alimentar’     |
| *Regra CHECK*                    | -            |    |    |          | Apenas um dos três produtos pode ser preenchido por registro   |

---

## Tabela *item_armazenado*
| Campo           | Tipo      | PK | FK | Nullable | Descrição                                  |
|------------------|-----------|----|----|----------|--------------------------------------------|
| id               | SERIAL    | ✔️ |    | ❌       | ID do item armazenado                      |
| armazem_id       | INT       |    | ✔️ | ❌       | FK Armazem(id)                             |
| item_estoque_id  | INT       |    | ✔️ | ❌       | FK ItemEstoque(id)                         |
| quantidade       | INT       |    |    | ❌       | Quantidade disponível                      |
| data_atualizacao | TIMESTAMP |    |    | ❌       | Data da última atualização (auto)          |

---

## Tabela *movimentacao_estoque*
| Campo              | Tipo         | PK | FK | Nullable | Descrição                                           |
|--------------------|--------------|----|----|----------|-----------------------------------------------------|
| id                 | SERIAL       | ✔️ |    | ❌       | ID da movimentação                                 |
| item_estoque_id    | INT          |    | ✔️ | ❌       | FK ItemEstoque(id)                                 |
| funcionario_id     | INT          |    | ✔️ | ✔️       | FK Funcionario(id)                                 |
| data_movimentacao  | TIMESTAMP    |    |    | ❌       | Data da movimentação                               |
| tipo               | VARCHAR(20)  |    |    | ❌       | ‘entrada’ ou ‘saida’                               |
| quantidade         | INT          |    |    | ❌       | Quantidade movimentada                             |
| cpf_comprador      | VARCHAR(14)  |    |    | ✔️       | CPF do comprador                                   |
| nome_comprador     | VARCHAR(100) |    |    | ✔️       | Nome do comprador                                  |
| receita_digital    | TEXT         |    |    | ✔️       | Receita médica digital (quando aplicável)          |
| observacoes        | TEXT         |    |    | ✔️       | Observações gerais                                 |

---

## Tabela *subcategoria_cuidado_pessoal*
| Campo     | Tipo         | PK | FK | Nullable | Descrição                                |
|-----------|--------------|----|----|----------|------------------------------------------|
| id        | SERIAL       | ✔️ |    | ❌       | ID da subcategoria                       |
| nome      | VARCHAR(100) |    |    | ❌       | Nome (único)                             |
| descricao | VARCHAR(255) |    |    | ✔️       | Descrição da subcategoria                |

---

## Tabela *restricao_alimentar*
| Campo | Tipo        | PK | FK | Nullable | Descrição                     |
|--------|-------------|----|----|----------|-------------------------------|
| id     | SERIAL      | ✔️ |    | ❌       | ID da restrição alimentar     |
| nome   | VARCHAR(50) |    |    | ❌       | Nome da restrição (único)     |

---

## Tabela *restricao_suplemento*
| Campo                   | Tipo         | PK | FK | Nullable | Descrição                                    |
|-------------------------|--------------|----|----|----------|----------------------------------------------|
| suplemento_alimentar_id | INT          | ✔️ | ✔️ | ❌       | FK SuplementoAlimentar(id)                   |
| restricao_alimentar_id  | INT          | ✔️ | ✔️ | ❌       | FK RestricaoAlimentar(id)                    |
| severidade              | VARCHAR(20)  |    |    | ✔️       | ‘leve’, ‘moderada’ ou ‘grave’                |
| observacoes             | TEXT         |    |    | ✔️       | Comentários adicionais sobre a restrição     |