# ❔ Tabela de Perguntas Estratégicas e Como Analisar no Excel

Esta tabela reúne as principais perguntas estratégicas de negócio que podem ser respondidas com os dados disponíveis, além de orientar como realizar cada análise no Excel.

# 📊 Painel Analítico de Assinaturas

## 🧭 1. Dashboard
**Visão geral com indicadores principais e gráficos resumo**

### 🎯 Indicadores Principais (Cartões):
- **Total de Assinaturas**  
  - `Contagem de Subscriber ID`
- **Faturamento Total**  
  - `Soma de Price`
- **Ticket Médio por Assinante**  
  - `Soma de Price / Contagem de Subscriber ID`
- **Plano Mais Vendido**  
  - `Product Name` (maior contagem)
- **Produto Adicional Mais Comprado**  
  - `Product Name` filtrado por “EA Play”, “Minecraft”

### 📈 Gráficos:
- **Evolução de Assinaturas por Mês**  
  - Agrupar `Date` por mês + contar `Subscriber ID`
- **Tendência de Faturamento**  
  - Agrupar `Date` por mês + somar `Price`

---

## 📊 2. Performance Comercial
**Análise dos planos, tipos de assinaturas e faturamento**

### 🛍️ Quais planos são os mais vendidos?
- `Product Name` (contagem)
- Filtro por `Subscription Type` ou `Plan Type`

### 🗃️ Qual tipo de plano gera mais receita?
- `Subscription Type` + `Soma de Price`

### 💰 Faturamento por Tipo
- `Product Name` ou `Subscription Type` + `Soma de Price`

### 🔁 Taxa de Renovação Automática por Plano
- Linhas: `Auto Renew` (Yes/No)
- Colunas: `Product Name`
- Valores: % por linha ou coluna

---

## 🧑‍💼 3. Perfil dos Assinantes
**Quem são os clientes e como se comportam**

### 🧍‍♂️ Ticket Médio por Assinante
- `Soma de Price / Contagem de Subscriber ID`

### 📅 Evolução de Assinaturas
- `Date` agrupado por mês + `Contagem de Subscriber ID`

### 🎮 Produtos Adicionais Mais Comprados
- `Product Name` filtrando “EA Play” / “Minecraft”
- Contagem ou soma de `Price`

### 🔄 Renovação por Perfil
- `Auto Renew` (Yes/No) + cruzamento com `Product Name`

---

## 🧾 4. Análise Descontos e Passes
**Impacto dos cupons e passes extras no faturamento**

### 💡 Impacto dos Cupons
- `Soma de Coupon Value / Soma de Price`
- % de pedidos com cupom (`Coupon Value > 0`)

### 💸 Receita com e sem Cupom
- Filtro 1: `Coupon Value > 0` → `Soma de Price`
- Filtro 2: `Coupon Value = 0` → `Soma de Price`
- Comparativo em gráfico

### 🎟️ Análise de Passes Adicionais
- `Product Name` com palavras-chave como “Passe”
- Contagem ou `Soma de Price`

---
