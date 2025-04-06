
# Desafio - Modelagem e Implementação de Banco de Dados para Oficina

## 📌 Descrição do Desafio

Neste desafio, o objetivo é criar um **banco de dados relacional** para gerenciar as operações de uma oficina mecânica. O projeto envolve desde a modelagem lógica até a implementação em SQL, incluindo a criação de tabelas, inserção de dados e elaboração de consultas SQL complexas.

O projeto deve abranger as principais entidades da oficina, como **clientes, veículos, ordens de serviço, serviços prestados e funcionários**. Além disso, é necessário incluir consultas SQL que realizem **recuperação de dados, filtros, junções, ordenações e cálculos de atributos derivados**.

---

## 🎯 Objetivo

O desafio tem como objetivo desenvolver um **banco de dados funcional**, seguindo as boas práticas de modelagem e otimização de consultas. Para isso, as seguintes etapas devem ser cumpridas:

1. **Modelagem Relacional**  
   - Definir tabelas, chaves primárias e estrangeiras.  
   - Criar relacionamentos entre as entidades do banco de dados.  

2. **Criação do Banco de Dados**  
   - Escrever um script SQL para criação do banco e suas tabelas.  
   - Garantir integridade referencial entre os dados.  

3. **Inserção de Dados**  
   - Popular as tabelas com informações fictícias para testes.  

4. **Consultas SQL Avançadas**  
   - Consultas com `SELECT`, `WHERE`, `ORDER BY`, `HAVING`, `JOIN` e cálculos de atributos derivados.  

5. **Publicação no GitHub**  
   - Criar um repositório contendo o código SQL e a documentação do projeto.  

---

## 🏛️ Entidades Principais

### 🧾 Pedido
- Representa uma solicitação de um cliente.
- Atributos principais: `id_pedido`, `id_cliente`, `data_pedido`.

### 👤 Cliente
- Armazena os dados dos clientes que realizam pedidos.
- Atributos principais: `id_cliente`, `nome_cliente`, `email_cliente`.

### 📦 Produto
- Representa os itens disponíveis para venda.
- Atributos principais: `id_produto`, `nome_produto`, `preco`.

### 🏪 Estoque
- Representa os locais e quantidades disponíveis de cada produto.
- Atributos principais: `id_estoque`, `id_produto`, `quantidade`.

### 🏭 Fornecedor
- Representa os fornecedores que fornecem os produtos.
- Atributos principais: `id_fornecedor`, `nome_fornecedor`, `contato`.

---

## 🔗 Relacionamentos do modelo Lógico

### 📦🧾 Produto - Pedido (N:N)
- Um produto pode estar presente em vários pedidos.
- Um pedido pode conter vários produtos.
- Implementado pela tabela `Relacao_Produto_Pedido` com os campos `id_produto`, `id_pedido` e `quantidade`.

### 📦🏭 Produto - Fornecedor (N:N)
- Um produto pode ser fornecido por vários fornecedores.
- Um fornecedor pode fornecer vários produtos.
- Implementado pela tabela `Produto_Fornecedor` com os campos `id_produto` e `id_fornecedor`.

### 📦🏪 Produto - Estoque (1:N)
- Um produto pode estar associado a vários registros de estoque.
- Cada registro de estoque está vinculado a apenas um produto.

### 🧾👤 Pedido - Cliente (N:1)
- Um cliente pode realizar vários pedidos.
- Cada pedido pertence a apenas um cliente.
