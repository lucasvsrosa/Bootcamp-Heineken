# Script 
O Script abrange todas as etapas do atendimento ao cliente, desde o registro da ordem de serviço até o pagamento, incluindo controle de serviços executados, equipe técnica, uso de peças (estoque ou fornecedor) e cálculo de valores com base em mão de obra e materiais.

``` SQL
-- Tabela de Clientes
CREATE TABLE clientes (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    telefone VARCHAR(20),
    email VARCHAR(100)
);

-- Tabela de Ordens de Serviço
CREATE TABLE ordens_servico (
    id SERIAL PRIMARY KEY,
    cliente_id INT NOT NULL,
    data_emissao DATE NOT NULL,
    data_conclusao DATE,
    status VARCHAR(50) NOT NULL,
    FOREIGN KEY (cliente_id) REFERENCES clientes(id)
);

-- Tabela de Pagamentos
CREATE TABLE pagamentos (
    id SERIAL PRIMARY KEY,
    ordem_servico_id INT NOT NULL,
    valor_total DECIMAL(10,2) NOT NULL,
    data_pagamento DATE NOT NULL,
    metodo_pagamento VARCHAR(50),
    FOREIGN KEY (ordem_servico_id) REFERENCES ordens_servico(id)
);

-- Tabela de Equipes
CREATE TABLE equipes (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL
);

-- Tabela de Mecânicos
CREATE TABLE mecanicos (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    endereco TEXT,
    especialidade VARCHAR(100),
    equipe_id INT,
    FOREIGN KEY (equipe_id) REFERENCES equipes(id)
);

-- Tabela de Serviços
CREATE TABLE servicos (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    descricao TEXT,
    valor_mao_obra DECIMAL(10,2),
    equipe_id INT,
    FOREIGN KEY (equipe_id) REFERENCES equipes(id)
);

-- Tabela associativa: Ordem de Serviço <-> Serviço
CREATE TABLE ordem_servico_servico (
    id SERIAL PRIMARY KEY,
    ordem_servico_id INT NOT NULL,
    servico_id INT NOT NULL,
    FOREIGN KEY (ordem_servico_id) REFERENCES ordens_servico(id),
    FOREIGN KEY (servico_id) REFERENCES servicos(id)
);

-- Tabela de Estoque
CREATE TABLE estoque (
    id SERIAL PRIMARY KEY,
    localizacao VARCHAR(100)
);

-- Tabela de Fornecedores
CREATE TABLE fornecedores (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    contato VARCHAR(100)
);

-- Tabela de Peças
CREATE TABLE pecas (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    valor DECIMAL(10,2) NOT NULL,
    origem VARCHAR(50), -- 'estoque' ou 'fornecedor'
    estoque_id INT,
    fornecedor_id INT,
    FOREIGN KEY (estoque_id) REFERENCES estoque(id),
    FOREIGN KEY (fornecedor_id) REFERENCES fornecedores(id)
);

-- Tabela associativa: Serviço <-> Peça
CREATE TABLE servico_peca (
    id SERIAL PRIMARY KEY,
    servico_id INT NOT NULL,
    peca_id INT NOT NULL,
    quantidade INT NOT NULL,
    FOREIGN KEY (servico_id) REFERENCES servicos(id),
    FOREIGN KEY (peca_id) REFERENCES pecas(id)
);

```
