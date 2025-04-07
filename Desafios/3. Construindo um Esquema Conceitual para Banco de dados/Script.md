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

---

# 🔄 Fluxo Completo do Processo da Oficina
1. O cliente chega à oficina e solicita um serviço.  
2. O atendente registra os dados do cliente e abre uma Ordem de Serviço (OS).  
3. A OS é criada com data de emissão, status e previsão de conclusão.  
4. O cliente informa o problema ou tipo de serviço desejado.  
5. Uma equipe é designada para analisar o veículo e confirmar os serviços necessários.  
6. Os serviços são registrados na OS e associados à equipe responsável.  
7. Se os serviços exigirem peças:  
   a. O sistema verifica se há peças no estoque.  
   b. Se não houver, realiza-se a compra via fornecedor.  
8. As peças utilizadas são registradas, com origem e valores.  
9. O valor da OS é calculado com base:  
   a. Nos serviços realizados (tabela de mão de obra).  
   b. Nas peças utilizadas (estoque ou fornecedor).  
10. O cliente autoriza a execução e o serviço é realizado.  
11. Após a conclusão, o cliente efetua o pagamento.  
12. O sistema registra o pagamento e encerra a OS.
