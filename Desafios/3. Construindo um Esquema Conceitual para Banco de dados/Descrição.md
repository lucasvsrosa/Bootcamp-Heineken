# 🚗 Oficina Mecânica - Controle de Ordens de Serviço

Este projeto apresenta o esquema conceitual para um sistema de gerenciamento de ordens de serviço de uma oficina mecânica. 

## 📌 Objetivo
Desenvolver um esquema conceitual para um sistema que permita:
- Gerenciar clientes e seus veículos
- Criar e gerenciar Ordens de Serviço (OS)
- Atribuir equipes de mecânicos para execução dos serviços
- Cálculo do custo de serviços e peças

## **📌 Narrativa**

### **Cliente 👤**  
Os clientes são os responsáveis pelos veículos que necessitam de manutenção ou revisão na oficina.  
- Cada cliente pode se cadastrar utilizando **CPF (Pessoa Física) ou CNPJ (Pessoa Jurídica)**, mas nunca ambos.  
- O cliente pode ter **um ou mais veículos registrados** em seu nome.  
- Um cliente pode **realizar múltiplas ordens de serviço (OS)** ao longo do tempo.  

### **Veículo 🚗**  
Os veículos são levados pelos clientes à oficina para execução dos serviços.  
- Cada veículo é identificado **unicamente pela placa**.  
- Um veículo está **sempre vinculado a um único cliente**.  
- Os veículos podem passar por **diferentes ordens de serviço** ao longo do tempo.  

### **Ordem de Serviço (OS) 📝**  
As ordens de serviço representam os serviços realizados na oficina para cada veículo.  
- Uma OS é **criada quando um cliente solicita um serviço** para seu veículo.  
- Contém informações como **data de emissão, data de conclusão prevista, status e valor total**.  
- O cliente deve **autorizar** a execução dos serviços antes da finalização da OS.  
- Cada OS é atribuída a **uma única equipe de mecânicos**, que será responsável pela execução dos serviços.  

### **Mecânicos 🔧**  
Os mecânicos são os profissionais responsáveis pela execução dos serviços na oficina.  
- Cada mecânico possui **um código de identificação único**.  
- Os mecânicos têm uma **especialidade**, como funilaria, elétrica ou motor.  
- São organizados em **equipes**, e cada equipe pode atender a múltiplas OSs.  

### **Equipe 👥**  
As equipes são compostas por mecânicos que trabalham em conjunto na execução das ordens de serviço.  
- Cada equipe pode ser **responsável por múltiplas OSs simultaneamente**.  
- Uma equipe pode ter **mecânicos com diferentes especialidades** para garantir uma execução completa dos serviços.  

### **Serviços 🛠️**  
Os serviços representam as atividades realizadas nos veículos.  
- Cada serviço possui um **nome, descrição e valor de mão de obra**.  
- Os serviços são cadastrados previamente e utilizados nas OSs conforme necessário.  
- Uma OS pode conter **um ou mais serviços**, dependendo do tipo de manutenção.  

### **Peças 🚀**  
As peças são utilizadas para a manutenção dos veículos durante a execução dos serviços.  
- Cada peça possui um **nome, descrição e valor unitário**.  
- Uma OS pode conter **diversas peças**, dependendo da necessidade do serviço.  
- As peças são adquiridas separadamente, e seus valores são somados ao custo final da OS.  

### **Orçamento 💰**  
O orçamento é gerado a partir da OS para definir o custo total dos serviços e peças.  
- O cálculo do orçamento considera **o valor da mão de obra e o custo das peças**.  
- O orçamento precisa ser **autorizado pelo cliente** antes da execução dos serviços.  
- Após a conclusão dos serviços, o valor final pode ser ajustado conforme necessário.  

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


Essa estrutura garante um controle eficiente sobre os serviços prestados pela oficina, organizando o fluxo desde a chegada do veículo até a conclusão do serviço. 🚗🔧✨  
