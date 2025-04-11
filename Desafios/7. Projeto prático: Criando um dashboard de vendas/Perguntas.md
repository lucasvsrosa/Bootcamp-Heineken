# ❓ Perguntas de Negócio

Este painel foi dividido em quatro blocos principais para responder perguntas estratégicas sobre assinaturas, desempenho comercial, perfil dos assinantes e impacto de cupons/passes.

---

## 🧭 1. Dashboard  
**Visão geral com indicadores principais e gráficos resumo**

### Perguntas Respondidas:
- 📅 **Qual a evolução das assinaturas ao longo do tempo?**
  - Campo: `Date` agrupado por mês
  - Valor: `Contagem de Subscriber ID`
  - Gráfico: Linha/Coluna mostrando crescimento

- 💰 **Qual o faturamento total considerando todos os produtos?**
  - Campo: `Price`
  - Valor: `Soma de Price`
  - Exibir em cartão de KPI

- 🧍‍♂️ **Qual o ticket médio por assinante?**
  - Fórmula: `Soma de Price / Contagem de Subscriber ID`
  - Exibir em cartão

- 🛍️ **Quais planos são os mais vendidos?**
  - Campo: `Product Name`
  - Valor: `Contagem`
  - Exibir o top 5 em gráfico de barras/pizza

- 🎮 **Quais produtos adicionais são mais comprados (EA Play / Minecraft)?**
  - Campo: `Product Name`
  - Filtro: apenas “EA Play”, “Minecraft”
  - Valor: `Contagem` ou `Soma de Price`

---

## 📊 2. Performance Comercial  
**Análise dos planos, tipos de assinaturas e faturamento**

### Perguntas Respondidas:
- 🛍️ **Quais planos são os mais vendidos?**
  - Campo: `Product Name`
  - Valor: `Contagem`
  - Pode segmentar por `Subscription Type`

- 🗃️ **Qual tipo de plano gera mais receita?**
  - Campo: `Subscription Type` ou `Product Name`
  - Valor: `Soma de Price`

- 🔁 **Qual a taxa de renovação automática por plano?**
  - Linhas: `Auto Renew` (Yes/No)
  - Colunas: `Product Name`
  - Valores: `Contagem de Assinaturas` (mostrar como % por coluna)

- 📈 **Qual a tendência de vendas nos últimos meses?**
  - Campo: `Date` agrupado por mês
  - Valor: `Contagem de Product Name` ou `Subscriber ID`

---

## 🧑‍💼 3. Perfil dos Assinantes  
**Quem são os clientes e como se comportam**

### Perguntas Respondidas:
- 🧍‍♂️ **Qual o ticket médio por assinante?**
  - Fórmula: `Soma de Price / Contagem de Subscriber ID`
  - Exibir em cartão

- 📅 **Qual a evolução das assinaturas ao longo do tempo?**
  - Campo: `Date` por mês + `Subscriber ID`
  - Gráfico de linha/coluna com contagem

- 🎮 **Quais produtos adicionais são mais comprados (EA Play / Minecraft)?**
  - Campo: `Product Name` filtrando “EA Play”, “Minecraft”
  - Valor: `Contagem` ou `Soma de Price`

- 🔄 **Qual a taxa de renovação automática por plano?**
  - Campo: `Auto Renew` + `Product Name`
  - Mostrar % por plano

---

## 🧾 4. Análise Descontos e Passes  
**Impacto dos cupons e passes extras no faturamento**

### Perguntas Respondidas:
- 🧾 **Qual o impacto dos cupons de desconto no faturamento?**
  - Campo: `Coupon Value`
  - Cálculo: `Soma de Coupon Value / Soma de Price`

- 💡 **Qual a diferença de receita entre usuários que usaram e não usaram cupom?**
  - Filtro: `Coupon Value > 0` e `Coupon Value = 0`
  - Campo: `Price` → `Soma`
  - Gráfico comparativo

- 🎟️ **Produtos adicionais comprados (como passes)**
  - Campo: `Product Name` com palavras como “Passe”
  - Valor: `Contagem` ou `Soma de Price`
