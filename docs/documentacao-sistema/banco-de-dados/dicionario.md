# Dicionário de Dados

> Nesta seção é apresentado o dicionário de dados do banco de dados do sistema ReMed.io, fornecendo detalhes sobre as tabelas, campos e relacionamentos utilizados no sistema.

---

### **ProdutoBase**
| Campo            | Tipo         | PK | FK | Nullable | Descrição                                       |
|------------------|--------------|----|----|----------|-------------------------------------------------|
| produto_base_id  | SERIAL       | ✔️ |    | ❌       | Identificador único do produto base            |
| nome             | CHAR(100)    |    |    | ❌       | Nome do produto                                |
| descricao        | CHAR(255)    |    |    | ✔️       | Descrição opcional do produto                   |

---

### **SuplementoAlimentar**
| Campo            | Tipo         | PK | FK | Nullable | Descrição                                      |
|------------------|--------------|----|----|----------|-------------------------------------------------|
| produto_base_id  | INT          | ✔️ | ✔️ | ❌       | Ref. ProdutoBase(produto_base_id)               |
| peso_volume      | CHAR(20)     |    |    | ✔️       | Peso ou volume do suplemento                    |
| sabor            | CHAR(50)     |    |    | ✔️       | Sabor                                           |
| restricoes       | TEXT         |    |    | ✔️       | Restrições alimentares gerais                   |

---

### **Medicamento**
| Campo                | Tipo         | PK | FK | Nullable | Descrição                                      |
|----------------------|--------------|----|----|----------|-------------------------------------------------|
| produto_base_id      | INT          | ✔️ | ✔️ | ❌       | Ref. ProdutoBase(produto_base_id)               |
| tarja                | CHAR(20)     |    |    | ✔️       | Cor da tarja                                    |
| necessita_receita    | BOOLEAN      |    |    | ✔️       | Indica se necessita receita                     |
| dosagem              | CHAR(50)     |    |    | ✔️       | Dosagem                                         |
| principio_ativo      | CHAR(100)    |    |    | ✔️       | Princípio ativo                                 |
| forma_farmaceutica   | CHAR(50)     |    |    | ✔️       | Forma farmacêutica                              |
| via_administracao    | CHAR(50)     |    |    | ✔️       | Via de administração                            |

---

### **CuidadoPessoal**
| Campo             | Tipo         | PK | FK | Nullable | Descrição                                                         |
|-------------------|--------------|----|----|----------|-------------------------------------------------------------------|
|produto_base_id    | INT          | ✔️ |✔️ |  ❌     |  Ref. ProdutoBase(produto_base_id)                                 |
|subcategoria_id    | INT          |    | ✔️ |  ❌     |  Ref. SubcategoriaCuidadoPessoal(subcategoria_id)                  |
|formato            | CHAR(50)     |    |    |   ✔️     | Forma física do produto (ex: líquido, gel, sólido, spray, lenço)  |
|quantidade         | CHAR(20)     |    |    |   ✔️     | Quantidade ou volume (ex: 200ml, 20 unidades)                     |
|uso_recomendado    | CHAR(100)    |    |    |   ✔️     | Descrição curta de uso (ex: uso diário, noturno, infantil)        |
|publico_alvo       | CHAR(50)     |    |    |   ✔️     | Público-alvo (ex: adulto, infantil, unissex, feminino)            |

---

### **Restricao**
| Campo            | Tipo         | PK | FK | Nullable | Descrição                                      |
|------------------|--------------|----|----|----------|-------------------------------------------------|
| restricao_id     | SERIAL       | ✔️ |    | ❌       | ID único da restrição                           |
| nome_restricao             | CHAR(50)     |    |    | ❌       | Nome da restrição (Ex.: lactose, glúten)       |

---

### **RestricaoSuplemento**
| Campo            | Tipo         | PK | FK | Nullable | Descrição                                      |
|------------------|--------------|----|----|----------|-------------------------------------------------|
| produto_base_id  | INT          | ✔️ | ✔️ | ❌       | Ref. SuplementoAlimentar(produto_base_id)      |
| restricao_id     | INT          | ✔️ | ✔️ | ❌       | Ref. Restricao(restricao_id)                   |

---

### **SubcategoriaCuidadoPessoal**

| Campo            | Tipo         | PK | FK | Nullable | Descrição                                               |
|------------------|--------------|----|----|----------|---------------------------------------------------------|
|subcategoria_id   |  SERIAL      |✔️ |     |❌       |  Identificador único da subcategoria                    |
|nome              |  CHAR(50)    |    |    | ❌       |  Nome da subcategoria (ex: Higiene, Beleza, Utilitário) |
|descricao         |  CHAR(255)   |    |    | ✔️       |  Descrição opcional da subcategoria                     |

---

### **Fornecedor**
| Campo            | Tipo         | PK | FK | Nullable | Descrição                                      |
|------------------|--------------|----|----|----------|-------------------------------------------------|
| fornecedor_id    | SERIAL       | ✔️ |    | ❌       | ID do fornecedor                               |
| nome             | CHAR(100)    |    |    | ❌       | Nome do fornecedor                             |
| cnpj             | CHAR(20)     |    |    | ❌       | CNPJ                                           |
| contato          | CHAR(100)    |    |    | ✔️       | Contato (telefone, email, etc)                 |

---

### **ItemEstoque**
| Campo            | Tipo         | PK | FK | Nullable | Descrição                                      |
|------------------|--------------|----|----|----------|-------------------------------------------------|
| item_estoque_id  | SERIAL       | ✔️ |    | ❌       | ID do item no estoque                          |
| codigo_barras    | CHAR(50)     |    |    | ❌       | Código de barras (único)                       |
| fornecedor_id    | INT          |    | ✔️ | ❌       | Ref. Fornecedor(fornecedor_id)                 |
| produto_base_id  | INT          |    | ✔️ | ❌       | Ref. ProdutoBase(produto_base_id)              |
| preco            | FLOAT        |    |    | ✔️       | Preço                                          |
| validade         | DATE         |    |    | ✔️       | Data de validade                               |

---

### **ItemArmazenado**
| Campo             | Tipo         | PK | FK | Nullable | Descrição                                      |
|-------------------|--------------|----|----|----------|-------------------------------------------------|
| item_armazenado_id| SERIAL       | ✔️ |    | ❌       | ID do item armazenado                          |
| armazem_id        | INT          |    | ✔️ | ❌       | Ref. Armazem(armazem_id)                       |
| item_estoque_id   | INT          |    | ✔️ | ❌       | Ref. ItemEstoque(item_estoque_id)              |
| quantidade        | INT          |    |    | ❌       | Quantidade em estoque                          |

---

### **Armazem**
| Campo            | Tipo         | PK | FK | Nullable | Descrição                                      |
|------------------|--------------|----|----|----------|-------------------------------------------------|
| armazem_id       | SERIAL       | ✔️ |    | ❌       | ID do armazém                                  |
| local_armazem | CHAR(100) |    |    | ❌       | Localização do armazém                         |

---

### **MovimentoEstoque**
| Campo                  | Tipo         | PK | FK | Nullable | Descrição                                      |
|------------------------|--------------|----|----|----------|-------------------------------------------------|
| movimentacao_estoque_id| SERIAL       | ✔️ |    | ❌       | ID da movimentação                             |
| item_estoque_id        | INT          |    | ✔️ | ❌       | Ref. ItemEstoque(item_estoque_id)              |
| data                   | TIMESTAMP    |    |    | ❌       | Data da movimentação                           |
| tipo                   | CHAR(20)     |    |    | ❌       | Tipo ('entrada' ou 'saida')                    |
| quantidade             | INT          |    |    | ❌       | Quantidade movimentada                         |
| cpf_comprador         | CHAR(11)     |    |    | ✔️       | CPF do comprador (se aplicável)                |
| nome_comprador        | CHAR(100)    |    |    | ✔️       | Nome do comprador (se aplicável)               |
| receita_medica_digital| TEXT         |    |    | ✔️       | Receita médica digital (se aplicável)          |
| funcionario_id        | INT          |    | ✔️ | ❌       | Ref. Funcionario(funcionario_id)               |

---

### **Funcionario**
| Campo            | Tipo         | PK | FK | Nullable | Descrição                                       |
|------------------|--------------|----|----|----------|-------------------------------------------------|
| funcionario_id   | SERIAL       | ✔️ |    | ❌      | Identificador único do funcionário              |
| nome             | CHAR(100)    |    |    | ❌      | Nome completo do funcionário                    |
| cpf              | CHAR(11)     |    |    | ❌      | CPF do funcionário (somente números)            |
| email            | CHAR(100)    |    |    | ❌      | E-mail do funcionário                           |
| senha_hash       | CHAR(255)    |    |    | ❌      | Senha do funcionário (armazenada com hash)      |
| cargo            | CHAR(50)     |    |    | ❌      | Cargo ou função do funcionário                  |
| data_contratacao | DATE         |    |    | ❌      | Data de contratação do funcionário              |

---