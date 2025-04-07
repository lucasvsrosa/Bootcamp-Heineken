# 🚗 Desafio - Modelagem e Implementação de Banco de Dados para Oficina Mecânica

## 📌 Descrição do Desafio

Este projeto tem como objetivo a construção de um **banco de dados relacional** voltado para o gerenciamento completo de uma **oficina mecânica**. O desafio envolve a criação do **modelo lógico**, desenvolvimento do **script SQL** com todas as tabelas necessárias, inserção de dados para testes e elaboração de **consultas SQL complexas** para análise e apoio à gestão.

Durante a realização do desafio, foram contempladas as principais etapas do ciclo de atendimento da oficina, desde o **cadastro dos clientes**, passando pela **emissão da ordem de serviço**, **execução de serviços e aplicação de peças**, até o **registro do pagamento**.

---

## 🎯 Objetivos

O desafio foi estruturado com os seguintes objetivos:

1. **Modelagem Relacional**
   - Definição de tabelas com seus respectivos campos, chaves primárias e estrangeiras.
   - Criação de relacionamentos entre entidades (1:N, N:N).

2. **Criação do Banco de Dados**
   - Desenvolvimento de um script SQL completo para a criação das tabelas com restrições de integridade.

3. **Persistência de Dados**
   - Inserção de registros fictícios para testes e simulações.

4. **Consultas SQL Avançadas**
   - Execução de queries complexas utilizando:
     - `SELECT`
     - `WHERE`
     - `ORDER BY`
     - `HAVING`
     - `JOIN`
     - Expressões para atributos derivados
---

## 🏛️ Entidades Principais

### `clientes`
- Armazena os dados dos clientes que solicitam os serviços da oficina.
- Atributos: `id`, `nome`, `telefone`, `email`.

### `ordens_servico`
- Representa cada atendimento solicitado por um cliente.
- Atributos: `id`, `cliente_id`, `data_emissao`, `data_conclusao`, `status`.

### `pagamentos`
- Registra os pagamentos realizados pelos clientes.
- Atributos: `id`, `ordem_servico_id`, `valor_total`, `data_pagamento`, `metodo_pagamento`.

### `equipes`
- Representa as equipes responsáveis pelos serviços.
- Atributos: `id`, `nome`.

### `mecanicos`
- Contém informações dos mecânicos da oficina.
- Atributos: `id`, `nome`, `endereco`, `especialidade`, `equipe_id`.

### `servicos`
- Registra os serviços oferecidos pela oficina.
- Atributos: `id`, `nome`, `descricao`, `valor_mao_obra`, `equipe_id`.

### `ordem_servico_servico`
- Tabela associativa entre ordens de serviço e serviços realizados.
- Atributos: `id`, `ordem_servico_id`, `servico_id`.

### `estoque`
- Representa os locais de armazenamento de peças.
- Atributos: `id`, `localizacao`.

### `fornecedores`
- Armazena informações sobre os fornecedores de peças.
- Atributos: `id`, `nome`, `contato`.

### `pecas`
- Tabela que registra todas as peças utilizadas nos serviços.
- Atributos: `id`, `nome`, `valor`, `origem`, `estoque_id`, `fornecedor_id`.

### `servico_peca`
- Tabela associativa entre serviços e peças utilizadas.
- Atributos: `id`, `servico_id`, `peca_id`, `quantidade`.

---

## 🔗 Relacionamentos do modelo Lógico

### 👤🧾 Cliente - Ordem de Serviço (1:N)
- Um cliente pode abrir várias ordens de serviço.
- Cada ordem de serviço está vinculada a apenas um cliente.

### 🧾💰 Ordem de Serviço - Pagamento (1:1)
- Cada ordem de serviço possui apenas um pagamento associado.
- Cada pagamento está ligado a uma única ordem de serviço.

### 🧾🛠️ Ordem de Serviço - Serviço (N:N)
- Uma ordem de serviço pode conter vários serviços.
- Um serviço pode estar presente em várias ordens de serviço.
- Implementado pela tabela `ordem_servico_servico` com os campos `ordem_servico_id` e `servico_id`.

### 🛠️🔧 Serviço - Peça (N:N)
- Um serviço pode utilizar várias peças.
- Uma peça pode ser utilizada em vários serviços.
- Implementado pela tabela `servico_peca` com os campos `servico_id`, `peca_id` e `quantidade`.

### 🛠️👨‍🔧 Serviço - Equipe (N:1)
- Uma equipe pode realizar vários serviços.
- Cada serviço é atribuído a apenas uma equipe.

### 👨‍🔧👥 Mecânico - Equipe (N:1)
- Uma equipe pode ter vários mecânicos.
- Cada mecânico pertence a apenas uma equipe.

### 🔧🏪 Peça - Estoque (N:1)
- Um estoque pode armazenar várias peças.
- Cada peça pertence a um único local de estoque.

### 🔧🏢 Peça - Fornecedor (N:1)
- Um fornecedor pode fornecer várias peças.
- Cada peça pode ter um fornecedor associado (quando a origem for "fornecedor").

---

## 🔗 Links (exemplo)

- [Script Oficina de Carro](https://github.com/lucasvsrosa/Bootcamp-Heineken/blob/main/Desafios/3.%20Construindo%20um%20Esquema%20Conceitual%20para%20Banco%20de%20dados/Script.md)
- [Perguntas](https://github.com/lucasvsrosa/Bootcamp-Heineken/blob/main/Desafios/5.%20%20Construa%20um%20Projeto%20L%C3%B3gico%20de%20Banco%20de%20Dados%20do%20Zero/Perguntas.md)
- [Modelo Lógico]()
