# 🎮 Xbox - Dashboard de Assinaturas e Vendas

## 🏆 Objetivo  
O objetivo deste desafio é criar um **dashboard de vendas com foco em assinaturas** utilizando o Excel, transformando dados brutos em informações visuais claras, organizadas e estratégicas. O intuito é facilitar a **análise de desempenho das assinaturas**, ajudando gestores e diretores a tomarem **decisões baseadas em dados**.

---

## 📖 Narrativa  
Você faz parte da equipe de dados de uma empresa que oferece planos de assinatura para jogos e passes de temporada (como **EA Play** e **Minecraft**). A diretoria precisa de um **painel interativo** para entender melhor o comportamento dos assinantes, os planos mais vendidos, o impacto de cupons de desconto no faturamento e a evolução das assinaturas ao longo do tempo.

Com base na base de dados disponibilizada, é possível analisar:

- 📅 **Evolução das assinaturas ao longo do tempo**
- 💰 **Faturamento total com assinaturas e produtos adicionais**
- 🛍️ **Produtos e planos mais populares**
- 🔁 **Taxa de renovação automática**
- 🧾 **Impacto dos cupons de desconto**
- 🔍 **Análise por tipo e valor de plano**

---

## 🗂️ Estrutura do Arquivo Excel

### 📁 Aba: `Assets`
Contém os elementos visuais utilizados no dashboard, como:

- Ícones de apoio visual
- Paleta de cores
- Ilustrações e imagens

---

### 📊 Aba: `Dashboard`
Estruturado em **4 blocos estratégicos** com base nas perguntas-chave da diretoria:

---

#### 1. 📌 Visão Geral  
🔍 **Objetivo:** Apresentar os indicadores principais do negócio.

- 🔢 Receita total (`Total Value`)
- 👥 Quantidade de assinantes únicos (`Subscriber ID`)
- 💸 Ticket médio (`Total Value` / assinantes)
- 📦 Receita por tipo de assinatura (`Subscription Type`)

---

#### 2. 📈 Performance Comercial  
🔍 **Objetivo:** Avaliar os resultados financeiros e os planos mais vendidos.

- 📊 Receita total por `Plan`
- 📈 Evolução das vendas ao longo do tempo (`Start Date` agrupado por mês)
- 🧾 Impacto dos cupons de desconto (`Coupon Value`)
- 🛒 Produtos adicionais mais vendidos: `EA Play Season Pass` e `Minecraft Season Pass`
- 🔁 Taxa de renovação automática por plano (`Auto Renewal` + `Plan`)

---

#### 3. 👤 Perfil dos Assinantes  
🔍 **Objetivo:** Entender o comportamento e preferências dos clientes.

- ✅ Distribuição de `Auto Renewal` (Sim/Não)
- 🗂️ Participação por `Subscription Type` (Mensal, Anual…)
- 🧩 Uso de passes adicionais: `EA Play Season Pass`, `Minecraft Season Pass`
- 💡 Comparação entre planos com e sem benefício extra

---

#### 4. 💸 Descontos e Impacto Financeiro  
🔍 **Objetivo:** Mensurar o efeito dos cupons na receita total.

- 📉 Receita com e sem cupom (`Coupon Value`)
- 🔍 Média de desconto aplicado por assinatura
- 📈 Comparação de receita bruta (`Subscription Price` + `Season Pass Price`) vs receita final (`Total Value`)
- 💰 Análise do % de assinantes que usaram cupons

---

## 📎 Filtros Interativos no Dashboard

- 📅 `Start Date`
- 🔁 `Auto Renewal`
- 📦 `Plan`
- 🗂️ `Subscription Type`

---

## 📊 Aba: `Bases` (Base de Dados Bruta)

### 🗂️ Dicionário de Dados

| Coluna                         | Descrição                                                                 |
|--------------------------------|---------------------------------------------------------------------------|
| `Subscriber ID`               | Identificador único de cada assinante                                    |
| `Name`                        | Nome do assinante                                                        |
| `Plan`                        | Plano de assinatura adquirido (Ex: Gold, Ultimate, etc.)                 |
| `Start Date`                  | Data de início da assinatura                                             |
| `Auto Renewal`                | Indica se a renovação automática está ativada (Sim ou Não)               |
| `Subscription Price`          | Valor pago pela assinatura principal                                     |
| `Subscription Type`           | Tipo da assinatura (Ex: Mensal, Anual, etc.)                             |
| `EA Play Season Pass`         | Indica se o assinante comprou o passe EA Play (Sim ou Não)               |
| `EA Play Season Pass Price`   | Valor pago pelo EA Play                                                  |
| `Minecraft Season Pass`       | Indica se o assinante comprou o passe Minecraft (Sim ou Não)             |
| `Minecraft Season Pass Price` | Valor pago pelo Minecraft                                                |
| `Coupon Value`                | Valor de desconto aplicado                                               |
| `Total Value`                 | Valor total pago após descontos                                          |
