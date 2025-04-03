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

## 🛠️ Tecnologias Utilizadas  
-  **MySQL** - Banco de Dados Relacional  
-  **Workbench** - Modelagem do Banco de Dados  
-  **Git/GitHub** - Versionamento de Código
