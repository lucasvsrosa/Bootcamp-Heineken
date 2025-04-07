# 🚗 Oficina Mecânica - Controle de Ordens de Serviço

Este projeto consiste no modelo conceitual de um banco de dados para um sistema de uma Oficina Mecânica, garantindo um controle eficiente sobre os serviços prestados pela oficina, organizando o fluxo desde a chegada do veículo até a conclusão e pagamento do serviço. 

## 📌 Objetivo

Desenvolver um esquema conceitual para um sistema que permita:

- Gerenciar clientes e seus veículos  
- Criar e gerenciar Ordens de Serviço (OS)  
- Atribuir equipes de mecânicos para execução dos serviços  
- Calcular o custo de serviços e peças  

---

## 📌 Narrativa

### 👤 Cliente

- Pode ser Pessoa Física (CPF) ou Jurídica (CNPJ), mas nunca ambos.  
- Pode ter um ou mais veículos registrados.  
- Pode realizar múltiplas OS ao longo do tempo.  

### 🚗 Veículo

- Identificado unicamente pela **placa**.  
- Sempre vinculado a um único cliente.  
- Pode passar por diferentes OSs.

### 📝 Ordem de Serviço (OS)

- Criada quando o cliente solicita um serviço.  
- Contém: data de emissão, previsão de conclusão, status e valor total.  
- Associada a uma equipe de mecânicos.  
- Exige autorização do cliente antes da execução.

### 🔧 Mecânicos

- Identificados por código único.  
- Possuem especialidade (funilaria, elétrica, motor...).  
- Organizados em equipes.

### 👥 Equipe

- Composta por mecânicos com diferentes especialidades.  
- Pode atender múltiplas OSs simultaneamente.

### 🛠️ Serviços

- Possuem nome, descrição e valor de mão de obra.  
- Previamente cadastrados.  
- Uma OS pode conter um ou mais serviços.

### 🚀 Peças

- Nome, descrição e valor unitário.  
- Utilizadas conforme necessidade dos serviços.  
- Origem: estoque ou fornecedor.  
- Seus valores somam ao custo da OS.

### 💰 Orçamento

- Gerado a partir da OS.  
- Soma o valor da mão de obra e das peças.  
- Requer autorização do cliente antes da execução.  
- Pode ser ajustado após a conclusão.

---

## 🔄 Fluxo Completo do Processo da Oficina

1. O cliente chega à oficina e solicita um serviço.  
2. O atendente registra os dados e abre a OS.  
3. A OS é criada com data, status e previsão.  
4. O cliente informa o problema ou serviço desejado.  
5. Uma equipe é designada para diagnóstico.  
6. Serviços são registrados e atribuídos à equipe.  
7. Se necessário, peças são verificadas no estoque:  
   - a. Se disponível, é usada.  
   - b. Se indisponível, é comprada de fornecedor.  
8. Peças utilizadas são registradas com valores e origem.  
9. Cálculo do valor total da OS com:  
   - a. Mão de obra  
   - b. Peças utilizadas  
10. Cliente autoriza execução.  
11. Serviço é realizado.  
12. Cliente efetua o pagamento.  
13. Sistema registra o pagamento e fecha a OS.

---

## ✨ Considerações Finais

Essa estrutura garante um **controle eficiente** sobre os serviços prestados pela oficina, organizando o fluxo desde a chegada do veículo até a conclusão e pagamento do serviço. 🚗🔧
