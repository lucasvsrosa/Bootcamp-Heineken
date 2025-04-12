# ❓ Perguntas de Negócio

Este painel responde perguntas estratégicas utilizando os nomes reais das colunas da base de dados. Os dados estão organizados em blocos temáticos com base nas perguntas de negócio.

---

## 🧭 1. Dashboard  
**Visão geral com indicadores principais e gráficos resumo**

### 📅 Qual a evolução das assinaturas ao longo do tempo?
- **Campo:** `Start Date`
- **Tabela Dinâmica:**
  - **Linhas:** `Start Date` (agrupado por mês/ano)
  - **Valores:** Soma de `Total Value`
- **Gráfico:** Linha
- **Aba:** Visão Geral

### 💰 Qual o faturamento total?
- **Campo:** `Total Value`
- **Fórmula:** `=SOMA(Total Value)`
- **Visual:** Cartão
- **Aba:** Visão Geral

### 👥 Quantos assinantes únicos existem?
- **Campo:** `Subscriber ID`
- **Fórmula:** `=NÚM.UNIQUE(Subscriber ID)`
- **Visual:** Cartão
- **Aba:** Visão Geral

### 🧍‍♂️ Qual o ticket médio por assinante?
- **Campo:** `Total Value` / `Subscriber ID`
- **Fórmula:** `=SOMA(Total Value) / NÚM.UNIQUE(Subscriber ID)`
- **Visual:** Cartão com forma personalizada
- **Aba:** Visão Geral

### 🧾 Qual o faturamento por tipo de assinatura?
- **Campos:** `Subscription Type`, `Total Value`
- **Tabela Dinâmica:**
  - **Linhas:** `Subscription Type`
  - **Valores:** Soma de `Total Value`
- **Gráfico:** Pizza ou colunas empilhadas
- **Aba:** Visão Geral

---

## 📈 2. Performance Comercial  
**Análise por plano de assinatura e comportamento de vendas adicionais**

### 📊 Qual o faturamento por plano?
- **Campos:** `Plan`, `Total Value`
- **Tabela Dinâmica:**
  - **Linhas:** `Plan`
  - **Valores:** Soma de `Total Value`
- **Gráfico:** Colunas Clusterizadas
- **Aba:** Performance Comercial

### 🔁 % de renovação automática por plano?
- **Campos:** `Plan`, `Auto Renewal`
- **Cálculo:** % com "Sim" por total do plano
- **Gráfico:** Barras ou linhas
- **Aba:** Performance Comercial

---

## 👤 3. Perfil dos Assinantes  
**Comportamento, tipo de plano e uso de passes**

### 🔁 Quantos usuários têm renovação automática?
- **Campo:** `Auto Renewal`
- **Tabela Dinâmica:**
  - **Linhas:** `Auto Renewal`
  - **Valores:** Contagem de `Subscriber ID`
- **Gráfico:** Barras
- **Aba:** Perfil dos Assinantes

### 💳 Distribuição por tipo de assinatura (Mensal x Anual)
- **Campo:** `Subscription Type`
- **Tabela Dinâmica:**
  - **Linhas:** `Subscription Type`
  - **Valores:** Contagem de `Subscriber ID`
- **Gráfico:** Pizza ou barras horizontais
- **Aba:** Perfil dos Assinantes

### 🎮 Quantos assinaram passes (EA / Minecraft)?
- **Campos:** `EA Play Season Pass`, `Minecraft Season Pass`
- **Filtro:** "Sim"
- **Cálculo:** Contagem de `Subscriber ID`
- **Gráfico:** Barras empilhadas
- **Aba:** Perfil dos Assinantes

---

## 💸 4. Descontos e Impacto Financeiro  
**Avaliação de uso de cupons, impacto no faturamento e comportamento dos usuários**

### 🎟️ Receita de usuários com e sem cupom
- **Campo:** `Coupon Value`
- **Filtro:** 0 vs > 0
- **Cálculo:** Soma de `Total Value`
- **Gráfico:** Colunas agrupadas (lado a lado)
- **Aba:** Descontos

### 🧮 Ticket médio com e sem cupom
- **Campos:** `Total Value`, `Subscriber ID`, `Coupon Value`
- **Cálculo:** Soma de `Total Value` / Nº de assinantes com e sem cupom
- **Gráfico:** Colunas lado a lado
- **Aba:** Descontos

### 💸 Valor total aplicado em cupons
- **Campo:** `Coupon Value`
- **Fórmula:** `=SOMA(Coupon Value)`
- **Gráfico:** Cartão ou coluna simples
- **Aba:** Descontos

### 📉 O uso de cupom compromete o faturamento?
- **Cálculo:** % de desconto médio = `SOMA(Coupon Value)` / `SOMA(Valor Bruto)`
- **Visual:** Indicador ou gráfico de colunas
- **Aba:** Descontos

---

## 🧠 Tabela de Métricas, Cálculos e Visualizações

| 🔎 Pergunta | 🧮 Cálculo | 📊 Gráfico | 📁 Aba |
|------------|-----------|------------|--------|
| 🧍‍♂️ Qual o ticket médio por assinante? | Soma de `Total Value` / Nº únicos de `Subscriber ID` | Cartão com forma ou borda | Visão Geral |
| 💰 Qual o faturamento total? | Soma de `Total Value` | Cartão | Visão Geral |
| 👥 Quantos assinantes únicos existem? | Contagem única de `Subscriber ID` | Cartão | Visão Geral |
| 🧾 Qual o faturamento por tipo de assinatura? | Tabela dinâmica com `Subscription Type` e `Total Value` | Pizza ou colunas empilhadas | Visão Geral |
| 📊 Qual o faturamento por plano? | `Plan` nas linhas, `Total Value` nos valores | Colunas clusterizadas | Performance Comercial |
| 🔁 Quantos usuários têm renovação automática? | `Auto Renewal` nas linhas + contagem de `Subscriber ID` | Barras | Perfil dos Assinantes |
| 🎟️ Receita com e sem cupom? | Filtrar `Coupon Value` = 0 vs > 0 → soma de `Total Value` | Colunas agrupadas lado a lado | Descontos |
| 💳 Distribuição por tipo de assinatura? | `Subscription Type` nas linhas + contagem de `Subscriber ID` | Pizza ou barras horizontais | Perfil dos Assinantes |
| 🎮 Quantos assinaram passes? | Filtro "Sim" em `EA Play` e `Minecraft` → contagem | Barras empilhadas | Perfil dos Assinantes |
| 🧮 Ticket médio com e sem cupom? | Soma de `Total Value` / nº de assinantes com ou sem cupom | Colunas lado a lado | Descontos |
| 📈 Evolução mensal do faturamento? | Agrupar `Start Date` por Ano-Mês + soma `Total Value` | Linhas | Visão Geral |
| 💸 Valor total aplicado em cupons? | Soma de `Coupon Value` | Cartão ou colunas | Descontos |
| 📉 Uso de cupom compromete o faturamento? | % de desconto médio: soma `Coupon Value` / soma `Valor Bruto` | Indicador ou colunas | Descontos |
| 🔁 % de renovação automática por plano? | Auto Renewal = Sim / total por `Plan` | Barras ou linhas | Perfil dos Assinantes |
