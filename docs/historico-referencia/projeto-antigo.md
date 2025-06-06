# Projeto Antigo - Farmácia da Márcia

> Nesta seção é apresentado o projeto original que serviu como base para o desenvolvimento do ReMed.io, detalhando tudo sobre o projeto para a compreensão do sistema.

---

O Projeto **Farmácia da Márcia** foi desenvolvido inicialmente como parte da disciplina de **Orientação a Objetos** com o objetivo de criar um sistema simples de gerenciamento de estoque farmacêutico. A aplicação permite que o administrador **visualize, adicione, remova e edite** produtos disponíveis em sua farmácia por meio de uma interface

---
## Tecnologias Utilizadas

<br>

<div align="center">

<table style="font-size: 16px; text-align: center; border-collapse: collapse;">
    <tr>
      <th>Camada</th>
      <th>Ferramentas / Tecnologias</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Frontend</strong></td>
      <td>Java Swing</td>
    </tr>
    <tr>
      <td><strong>Backend</strong></td>
      <td>Java 11</td>
    </tr>
    <tr>
      <td><strong>Banco de Dados</strong></td>
      <td>MySQL</td>
    </tr>
    <tr>
      <td><strong>Testes</strong></td>
      <td>JUnit</td>
    </tr>
    <tr>
      <td><strong>Outras libs</strong></td>
      <td> Maven, Hibernate (JPA)</td>
  </tbody>
</table>

</div>

---



## Arquitetura Original

A arquitetura do projeto foi construída em **Java** utilizando o padrão orientado a objetos clássico. Ela se baseia em três principais camadas:

- [`Modelo (Model)`](https://github.com/acamposs/Projeto_oo1/tree/main/farmacia-maven/src/main/java/br/com/farmacia/farmaciamaven/Model): Representa as entidades do domínio, como `Produto`, `Medicamento`, `Cosmetico` e `Farmacia`.
- [`Persistência (DAO)`](https://github.com/acamposs/Projeto_oo1/tree/main/farmacia-maven/src/main/java/br/com/farmacia/farmaciamaven/services): Camada responsável pelo gerenciamento dos dados via JPA/Hibernate com banco de dados MySQL.
- [`Interface (View)`](https://github.com/acamposs/Projeto_oo1/tree/main/farmacia-maven/src/main/java/br/com/farmacia/farmaciamaven/view): Interação via console com menus de seleção para o administrador da farmácia.

Além disso, o sistema utiliza o Maven para gerenciamento de dependências e o JUnit para testes unitários.

---

## Diagrama de Classes

> A estrutura de classes do sistema é apresentada abaixo

<br>
<p align="center">
    <a href="https://raw.githubusercontent.com/remed-io/Docs/refs/heads/main/docs/assets/diagrama-antigo.png">
        <img src="/../../assets/diagrama-antigo.png" alt="Diagrama Físico do Banco" width="600"/>
    </a>
</p>

### Principais Componentes

- **Farmacia**  
  Representa a farmácia que possui uma lista de produtos. Responsável por adicionar e remover itens do estoque.

- **Produto (abstrata)**  
  Superclasse para os produtos cadastrados, contendo atributos comuns como nome, fabricante, validade e valor.

- **Medicamento**  
  Subclasse de `Produto` com informações específicas como indicação terapêutica, dosagem e via de administração.

- **Cosmetico**  
  Subclasse de `Produto` contendo dados sobre aplicação e função estética.

