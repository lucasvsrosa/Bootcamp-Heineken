# Desafio - Modelagem e Implementação de Banco de Dados para E-commerce

## 📌 Descrição do Desafio

Este desafio consiste na criação de um **banco de dados relacional** para um sistema de **e-commerce** completo. O objetivo é realizar a modelagem e a implementação de todas as tabelas necessárias para controlar clientes, pedidos, pagamentos, entregas, produtos, fornecedores, vendedores terceiros e estoque.

A modelagem considera a existência de clientes **Pessoa Física (PF)** e **Pessoa Jurídica (PJ)**, com campos e validações específicas para CPF e CNPJ, além de integrar os pedidos a suas respectivas entregas, pagamentos e produtos adquiridos. Também são levadas em consideração as relações com fornecedores e vendedores terceiros, enriquecendo o cenário de um e-commerce realista.

---

## 🎯 Objetivo

Desenvolver um **banco de dados robusto e funcional**, utilizando boas práticas de modelagem relacional, integridade referencial e normalização. O projeto inclui:

1. **Modelagem Relacional**  
   - Definição das entidades, atributos e relacionamentos.  
   - Chaves primárias e estrangeiras corretamente aplicadas.  

2. **Criação do Banco de Dados**  
   - Script SQL completo para a criação das tabelas.  
   - Uso de `ENUM`, `CHECK`, `UNIQUE` e `ON DELETE CASCADE`.  

3. **Relacionamentos Complexos**  
   - Implementação de relacionamentos N:N e 1:N com tabelas associativas.  

4. **Cenário Realista**  
   - Diferença entre cliente PF e PJ.  
   - Gestão de estoque e múltiplos fornecedores.  
   - Suporte a vendedores terceiros.  

---

## 🏛️ Entidades Principais

### 👤 Cliente
- Armazena os dados dos clientes, podendo ser pessoa física ou jurídica.
- Atributos principais: `id_cliente`, `nome`, `tipo (PF/PJ)`, `cpf`, `cnpj`, `identificacao`, `endereco`.

### 🧾 Pedido
- Representa os pedidos feitos pelos clientes.
- Atributos principais: `id_pedido`, `status_pedido`, `descricao`, `frete`, `id_cliente`.

### 💳 Pagamento
- Registra os pagamentos dos pedidos.
- Atributos principais: `id_pagamento`, `tipo_pagamento`, `dados_pagamento`, `id_pedido`.

### 🚚 Entrega
- Controla o status e rastreio da entrega dos pedidos.
- Atributos principais: `id_entrega`, `id_pedido`, `status_entrega`, `codigo_rastreio`.

### 📦 Produto
- Itens disponíveis para venda.
- Atributos principais: `id_produto`, `categoria`, `descricao`, `valor`.

### 🏪 Estoque
- Local onde os produtos estão armazenados.
- Atributos principais: `id_estoque`, `localizacao`.

### 🏭 Fornecedor
- Empresas fornecedoras dos produtos.
- Atributos principais: `id_fornecedor`, `razao_social`, `cnpj`.

### 🛍️ Vendedor Terceiro
- Vendedores que comercializam seus produtos na plataforma.
- Atributos principais: `id_vendedor_terceiro`, `razao_social`, `localizacao`.

---

## 🔗 Relacionamentos do Modelo Lógico

### 📦🧾 Produto - Pedido (N:N)
- Um pedido pode conter vários produtos.
- Um produto pode estar em vários pedidos.
- Tabela associativa: `Relacao_Produto_Pedido (id_produto, id_pedido, quantidade)`.

### 📦🏭 Produto - Fornecedor (N:N)
- Produtos podem ter múltiplos fornecedores.
- Um fornecedor fornece vários produtos.
- Tabela associativa: `Produto_Fornecedor (id_produto, id_fornecedor)`.

### 📦🏪 Produto - Estoque (N:N)
- Produtos estão associados a diferentes estoques.
- Tabela associativa: `Produto_em_Estoque (id_estoque, id_produto, quantidade)`.

### 📦🛍️ Produto - Vendedor Terceiro (N:N)
- Produtos vendidos por terceiros.
- Tabela associativa: `Produtos_Vendedores_Terceiros (id_produto, id_vendedor_terceiro, quantidade)`.

### 🧾👤 Pedido - Cliente (N:1)
- Cada pedido pertence a um único cliente.
- Um cliente pode realizar vários pedidos.

### 💳🧾 Pagamento - Pedido (1:1)
- Cada pedido possui um único pagamento.
- Pagamento está vinculado diretamente ao pedido.

### 🚚🧾 Entrega - Pedido (1:1)
- Cada pedido possui uma entrega associada.

---

## Link
- [Script E-commerce](https://github.com/lucasvsrosa/Bootcamp-Heineken/blob/main/Desafios/2.%20Refinando%20um%20projeto%20Conceitual%20de%20Banco%20de%20dados%20-%20E-commerce/Script.md) 
- [Modelo Lógico](https://github.com/lucasvsrosa/Bootcamp-Heineken/blob/main/Desafios/4.%20Construa%20um%20Projeto%20Lógico%20de%20Banco%20de%20Dados%20do%20Zero/modelo%20logico.png)
- [Perguntas](https://github.com/lucasvsrosa/Bootcamp-Heineken/blob/main/Desafios/4.%20Construa%20um%20Projeto%20Lógico%20de%20Banco%20de%20Dados%20do%20Zero/Perguntas.md)
