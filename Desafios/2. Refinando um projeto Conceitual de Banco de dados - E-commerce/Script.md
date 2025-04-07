# Script E-commerce

Este arquivo contém os scripts corretos para o desafio

---

``` sql
-- E-commerce Refinado
CREATE DATABASE IF NOT EXISTS ECommerce;
USE ECommerce;

-- Tabela Cliente
CREATE TABLE Cliente (
    id_cliente INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    tipo ENUM('PJ', 'PF') NOT NULL,
    cpf VARCHAR(14) UNIQUE NULL,
    cnpj VARCHAR(18) UNIQUE NULL,
    identificacao VARCHAR(45) NOT NULL,
    endereco VARCHAR(255) NOT NULL,
    CHECK (
        (tipo = 'PJ' AND cnpj IS NOT NULL AND cpf IS NULL) OR
        (tipo = 'PF' AND cpf IS NOT NULL AND cnpj IS NULL)
    )
);

-- Tabela Pedido
CREATE TABLE Pedido (
    id_pedido INT PRIMARY KEY AUTO_INCREMENT,
    status_pedido ENUM('Pendente', 'Pago', 'Cancelado', 'Enviado', 'Entregue') NOT NULL,
    descricao VARCHAR(255),
    frete DECIMAL(10,2) NOT NULL,
    id_cliente INT NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES Cliente(id_cliente) ON DELETE CASCADE
);

-- Tabela Pagamento (revisada)
CREATE TABLE Pagamento (
    id_pagamento INT PRIMARY KEY AUTO_INCREMENT,
    tipo_pagamento ENUM('Cartão de Crédito', 'Cartão de Débito', 'Boleto', 'Pix') NOT NULL,
    dados_pagamento VARCHAR(255) NOT NULL,
    id_pedido INT NOT NULL UNIQUE,
    FOREIGN KEY (id_pedido) REFERENCES Pedido(id_pedido) ON DELETE CASCADE
);

-- Tabela Entrega
CREATE TABLE Entrega (
    id_entrega INT PRIMARY KEY AUTO_INCREMENT,
    id_pedido INT NOT NULL,
    status_entrega ENUM('Aguardando Envio', 'Em Transporte', 'Entregue', 'Problema na Entrega') NOT NULL,
    codigo_rastreio VARCHAR(50) NOT NULL UNIQUE,
    FOREIGN KEY (id_pedido) REFERENCES Pedido(id_pedido) ON DELETE CASCADE
);

-- Tabela Produto
CREATE TABLE Produto (
    id_produto INT PRIMARY KEY AUTO_INCREMENT,
    categoria VARCHAR(45) NOT NULL,
    descricao VARCHAR(255) NOT NULL,
    valor DECIMAL(10,2) NOT NULL
);

-- Tabela Relacao Produto/Pedido (Muitos para Muitos)
CREATE TABLE Relacao_Produto_Pedido (
    id_produto INT,
    id_pedido INT,
    quantidade INT NOT NULL DEFAULT 1,
    PRIMARY KEY (id_produto, id_pedido),
    FOREIGN KEY (id_produto) REFERENCES Produto(id_produto) ON DELETE CASCADE,
    FOREIGN KEY (id_pedido) REFERENCES Pedido(id_pedido) ON DELETE CASCADE
);

-- Tabela Estoque
CREATE TABLE Estoque (
    id_estoque INT PRIMARY KEY AUTO_INCREMENT,
    localizacao VARCHAR(100) NOT NULL
);

-- Tabela Produto em Estoque
CREATE TABLE Produto_em_Estoque (
    id_estoque INT,
    id_produto INT,
    quantidade INT NOT NULL DEFAULT 0,
    PRIMARY KEY (id_estoque, id_produto),
    FOREIGN KEY (id_estoque) REFERENCES Estoque(id_estoque) ON DELETE CASCADE,
    FOREIGN KEY (id_produto) REFERENCES Produto(id_produto) ON DELETE CASCADE
);

-- Tabela Fornecedor
CREATE TABLE Fornecedor (
    id_fornecedor INT PRIMARY KEY AUTO_INCREMENT,
    razao_social VARCHAR(100) NOT NULL,
    cnpj VARCHAR(18) UNIQUE NOT NULL
);

-- Tabela Produto_Fornecedor
CREATE TABLE Produto_Fornecedor (
    id_produto INT,
    id_fornecedor INT,
    PRIMARY KEY (id_produto, id_fornecedor),
    FOREIGN KEY (id_produto) REFERENCES Produto(id_produto) ON DELETE CASCADE,
    FOREIGN KEY (id_fornecedor) REFERENCES Fornecedor(id_fornecedor) ON DELETE CASCADE
);

-- Tabela Vendedor Terceiro
CREATE TABLE Vendedor_Terceiro (
    id_vendedor_terceiro INT PRIMARY KEY AUTO_INCREMENT,
    razao_social VARCHAR(100) NOT NULL,
    localizacao VARCHAR(100) NOT NULL
);

-- Tabela Produtos_Vendedores_Terceiros
CREATE TABLE Produtos_Vendedores_Terceiros (
    id_produto INT,
    id_vendedor_terceiro INT,
    quantidade INT NOT NULL DEFAULT 0,
    PRIMARY KEY (id_produto, id_vendedor_terceiro),
    FOREIGN KEY (id_produto) REFERENCES Produto(id_produto) ON DELETE CASCADE,
    FOREIGN KEY (id_vendedor_terceiro) REFERENCES Vendedor_Terceiro(id_vendedor_terceiro) ON DELETE CASCADE
);

```
