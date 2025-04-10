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
## 🗂️ Abas do Arquivo Excel

### 📁 Aba: `Assets`
Esta aba reúne os elementos visuais utilizados no dashboard, como:

- Ícones (ex: calendário, carrinho, dinheiro, seta, etc.)
- Cores e estilos para padronização visual
- Legendas ou imagens auxiliares

### 📊 Aba: `Dashboard`

O dashboard foi estruturado em **múltiplas abas**, cada uma com um foco estratégico:

#### 1. **📌 Visão Geral**
- Receita total
- Quantidade de assinantes
- Ticket médio
- Receita por tipo de assinatura
- Filtros: Start Date, Auto Renewal, Plan, Subscription Type

#### 2. **📈 Performance Comercial**
- Receita por plano
- Análise do uso de cupons
- Participação de Season Pass (EA e Minecraft)
- Receita com/sem desconto

#### 3. **👤 Perfil dos Assinantes**
- Comportamento de renovação automática
- Distribuição dos planos
- Adesão a benefícios extras (Season Pass)
- Comparativo entre assinaturas mensais e anuais

#### 4. **💸 Descontos e Impacto Financeiro**
- Quantidade de cupons utilizados
- Comparativo de receita com e sem cupons
- Avaliação se os cupons estão reduzindo excessivamente a margem de lucro

#### OBS: **🔎 Filtros Interativos**

Para uma análise personalizada, o dashboard permite aplicar os seguintes **filtros dinâmicos**:

- 📅 Start Date  
- 🔁 Auto Renewal  
- 📦 Plan  
- 📂 Subscription Type

### 🏦 Aba: `Bases`
Esta é a aba principal com os dados brutos de assinaturas, que foram utilizados para construir o dashboard.

#### 🗂️ Dicionário de Dados

| Coluna                       | Descrição                                                                 |
|-----------------------------|---------------------------------------------------------------------------|
| `Subscriber ID`             | Identificador único de cada assinante                                    |
| `Name`                      | Nome do assinante                                                        |
| `Plan`                      | Plano de assinatura adquirido (Ex: Gold, Ultimate, etc.)                 |
| `Start Date`                | Data de início da assinatura                                             |
| `Auto Renewal`              | Indica se a renovação automática está ativada (Sim ou Não)               |
| `Subscription Price`        | Valor pago pela assinatura principal                                     |
| `Subscription Type`        | Tipo da assinatura (Ex: Mensal, Anual, etc.)                             |
| `EA Play Season Pass`       | Indica se o assinante comprou o passe de temporada do EA Play (Sim ou Não) |
| `EA Play Season Pass Price` | Valor pago pelo passe de temporada do EA Play                            |
| `Minecraft Season Pass`     | Indica se o assinante comprou o passe de temporada do Minecraft (Sim ou Não) |
| `Minecraft Season Pass Price` | Valor pago pelo passe de temporada do Minecraft                        |
| `Coupon Value`              | Valor de desconto aplicado por cupom                                     |
| `Total Value`               | Valor total gasto pelo assinante após desconto (assinatura + passes)     |


### 🧮 Aba: Cálculos
Esta aba concentra todas as colunas auxiliares e fórmulas criadas para análise e visualização no dashboard.

#### 📌 Principais colunas calculadas:

- `Ano-Mês:` usada para agrupar assinaturas por mês (extraída do Start Date)
- `Valor Bruto:` soma de Subscription Price + EA Play + Minecraft
- `Ticket Médio:` cálculo do valor médio por assinante
- `Com Cupom / Sem Cupom:` para comparar o impacto do uso de cupons no faturamento
- `Faturamento Total:` total pago sem descontos
- `Faturamento Real:` total pago com descontos aplicados
- `% Renovação:` percentual de renovação automática por plano ou tipo
