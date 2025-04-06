# 📦 E-Commerce - Modelo de Banco de Dados  

## 📌 Descrição do Projeto  
Este projeto consiste no **modelo conceitual de um banco de dados para um sistema de e-commerce**, onde clientes podem realizar compras online, fornecedores disponibilizam produtos, e vendedores terceiros podem comercializar produtos dentro da plataforma.  

## 🎯 Objetivo  
Refinar o modelo, acrescentando as regras abaixo:  
- **Cliente PJ e PF**: Uma conta pode ser **Pessoa Jurídica (PJ)** ou **Pessoa Física (PF)**, mas não ambas.  
- **Pagamento**: O cliente pode cadastrar mais de uma forma de pagamento.  
- **Entrega**: A entrega deve conter **status** e **código de rastreamento**.  

---

## 📌 Narrativa 
### **Produto 🛍️**
- Os produtos são vendidos por **uma única plataforma online**, mas podem ter diferentes **vendedores terceiros**.  
- Cada **produto tem um fornecedor** registrado na plataforma.  
- Um ou mais produtos podem compor um **pedido**.  

### **Cliente 👤**
- O cliente pode se cadastrar com seu **CPF (Pessoa Física) ou CNPJ (Pessoa Jurídica)**, mas **não pode ter os dois**.  
- O **endereço do cliente** determina o valor do frete.  
- Um cliente pode **realizar múltiplos pedidos**.  
- O cliente possui um **período de carência para devolução** do produto.  

### **Pedido 📝**
- Os pedidos são **criados por clientes** e armazenam as informações da compra, **endereço de entrega e status da entrega**.  
- Um **pedido pode ser cancelado** antes da finalização da compra.  
- Um pedido pode conter **um ou mais produtos**.  

### **Fornecedor 🏭**
- Fornecedores são responsáveis por disponibilizar os produtos que serão vendidos na plataforma.
- Cada produto está vinculado a um único fornecedor, garantindo rastreabilidade e controle de origem.
- Um fornecedor pode fornecer diversos produtos, mas cada produto tem apenas um fornecedor principal.
- Os fornecedores são identificados por informações como razão social e CNPJ.

### **Estoque 📦**
- O estoque representa os locais onde os produtos são armazenados antes da venda.
- Um produto pode estar presente em múltiplos estoques, permitindo uma distribuição eficiente.
- O estoque não está diretamente vinculado ao fornecedor, mas sim aos produtos cadastrados na plataforma.
- A localização do estoque pode influenciar o prazo de entrega dos pedidos.

---

## Modelo usado 
```python
-- E-commerce Modelo

CREATE DATABASE ECommerce;
USE ECommerce;

-- Tabela Cliente
CREATE TABLE Cliente (
    idCliente INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45),
    identificacao VARCHAR(45),
    endereco VARCHAR(45)
);

-- Tabela Pedido
CREATE TABLE Pedido (
    idPedido INT PRIMARY KEY AUTO_INCREMENT,
    statusDoPedido VARCHAR(45),
    descricao VARCHAR(45),
    frete FLOAT,
    Cliente_idCliente INT,
    FOREIGN KEY (Cliente_idCliente) REFERENCES Cliente(idCliente)
);

-- Tabela Produto
CREATE TABLE Produto (
    idProduto INT PRIMARY KEY AUTO_INCREMENT,
    categoria VARCHAR(45),
    descricao VARCHAR(45),
    valor FLOAT
);

-- Tabela Relacao Produto/Pedido (Muitos para Muitos)
CREATE TABLE Relacao_Produto_Pedido (
    Produto_idProduto INT,
    Pedido_idPedido INT,
    PRIMARY KEY (Produto_idProduto, Pedido_idPedido),
    FOREIGN KEY (Produto_idProduto) REFERENCES Produto(idProduto),
    FOREIGN KEY (Pedido_idPedido) REFERENCES Pedido(idPedido)
);

-- Tabela Estoque
CREATE TABLE Estoque (
    idEstoque INT PRIMARY KEY AUTO_INCREMENT,
    local VARCHAR(45)
);

-- Tabela Produto_em_Estoque
CREATE TABLE Produto_em_Estoque (
    Estoque_idEstoque INT,
    Produto_idProduto INT,
    PRIMARY KEY (Estoque_idEstoque, Produto_idProduto),
    FOREIGN KEY (Estoque_idEstoque) REFERENCES Estoque(idEstoque),
    FOREIGN KEY (Produto_idProduto) REFERENCES Produto(idProduto)
);

-- Tabela Fornecedor
CREATE TABLE Fornecedor (
    idFornecedor INT PRIMARY KEY AUTO_INCREMENT,
    razaoSocial VARCHAR(45),
    cnpj VARCHAR(45)
);

-- Tabela Produto_Fornecedor
CREATE TABLE Produto_Fornecedor (
    Produto_idProduto INT,
    Fornecedor_idFornecedor INT,
    PRIMARY KEY (Produto_idProduto, Fornecedor_idFornecedor),
    FOREIGN KEY (Produto_idProduto) REFERENCES Produto(idProduto),
    FOREIGN KEY (Fornecedor_idFornecedor) REFERENCES Fornecedor(idFornecedor)
);

-- Tabela Vendedor Terceiro
CREATE TABLE Vendedor_Terceiro (
    idVendedorTerceiro INT PRIMARY KEY AUTO_INCREMENT,
    razaoSocial VARCHAR(45),
    local VARCHAR(45)
);

-- Tabela Produtos_Vendedores_Terceiros
CREATE TABLE Produtos_Vendedores_Terceiros (
    Produto_idProduto INT,
    Vendedor_Terceiro_idVendedorTerceiro INT,
    quantidade INT,
    PRIMARY KEY (Produto_idProduto, Vendedor_Terceiro_idVendedorTerceiro),
    FOREIGN KEY (Produto_idProduto) REFERENCES Produto(idProduto),
    FOREIGN KEY (Vendedor_Terceiro_idVendedorTerceiro) REFERENCES Vendedor_Terceiro(idVendedorTerceiro)
);
```
