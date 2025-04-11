# ❓ Perguntas de Negócio

Este painel responde perguntas estratégicas utilizando os nomes reais das colunas da base de dados. Os dados estão organizados em blocos temáticos com base nas perguntas de negócio.

---

## 🧭 1. Dashboard  
**Visão geral com indicadores principais e gráficos resumo**

### 📅 Qual a evolução das assinaturas ao longo do tempo?
- **Campo:** `Start Date`
- **Tabela Dinâmica:**
  - **Linhas:** `Start Date` (agrupado por mês/ano)
  - **Valores:** Contagem de `Subscriber ID`

### 💰 Qual o faturamento total considerando todos os produtos?
- **Campo:** `Total Value`
- **Tabela Dinâmica:**
  - **Valores:** Soma de `Total Value`

### 🧍‍♂️ Qual o ticket médio por assinante?
- **Campo:** `Total Value`
- **Tabela Dinâmica:**
  - **Valores:** Soma de `Total Value`
  - **Linhas:** `Subscriber ID`
  - **Resultado Final:** Criar campo calculado fora da Tabela Dinâmica com fórmula: `=Soma_Total / Qtde_Assinantes_Unicos`

---

## 📊 2. Performance Comercial  
**Análise dos planos, tipos de assinaturas e faturamento**

### 🛍️ Quais planos são os mais vendidos?
- **Campo:** `Plan`
- **Tabela Dinâmica:**
  - **Linhas:** `Plan`
  - **Valores:** Contagem de `Subscriber ID`

### 🗃️ Qual tipo de plano gera mais receita?
- **Campos:** `Subscription Type`, `Subscription Price`
- **Tabela Dinâmica:**
  - **Linhas:** `Subscription Type`
  - **Valores:** Soma de `Subscription Price`

### 🔁 Qual a taxa de renovação automática por plano?
- **Campos:** `Auto Renewal`, `Plan`
- **Tabela Dinâmica:**
  - **Linhas:** `Plan`
  - **Colunas:** `Auto Renewal`
  - **Valores:** Contagem de `Subscriber ID`
  - **Resultado Final:** Calcular % de "Sim" com fórmula fora da Tabela Dinâmica

### 📈 Qual a tendência de vendas nos últimos meses?
- **Campos:** `Start Date`, `Subscription Price`
- **Tabela Dinâmica:**
  - **Linhas:** `Start Date` (agrupado por mês/ano)
  - **Valores:** Soma de `Subscription Price`

---

## 🧑‍💼 3. Perfil dos Assinantes  
**Quem são os clientes e como se comportam**

### 🧍‍♂️ Qual o ticket médio por assinante?
- **Campo:** `Total Value`
- **Tabela Dinâmica:**
  - **Linhas:** `Subscriber ID`
  - **Valores:** Soma de `Total Value`
  - **Resultado Final:** Média dos valores gerados por assinante

### 📅 Qual a evolução das assinaturas ao longo do tempo?
- **Campo:** `Start Date`
- **Tabela Dinâmica:**
  - **Linhas:** `Start Date` (agrupado por mês/ano)
  - **Valores:** Contagem de `Subscriber ID`

### 🎮 Quais produtos adicionais são mais comprados (EA Play / Minecraft)?
- **Campos:** `EA Play Season Pass`, `Minecraft Season Pass`
- **Tabela Dinâmica (1):**
  - **Linhas:** `EA Play Season Pass`
  - **Valores:** Contagem de `Subscriber ID`
- **Tabela Dinâmica (2):**
  - **Linhas:** `Minecraft Season Pass`
  - **Valores:** Contagem de `Subscriber ID`

### 🔁 Qual a taxa de renovação automática por plano?
- **Campos:** `Auto Renewal`, `Plan`
- **Tabela Dinâmica:**
  - **Linhas:** `Plan`
  - **Colunas:** `Auto Renewal`
  - **Valores:** Contagem de `Subscriber ID`

---

## 🧾 4. Análise Descontos e Passes  
**Impacto dos cupons e passes extras no faturamento**

### 🧾 Qual o impacto dos cupons de desconto no faturamento?
- **Campos:** `Coupon Value`, `Total Value`
- **Tabela Dinâmica:**
  - **Valores:** Soma de `Coupon Value`, Soma de `Total Value`
  - **Resultado Final:** Fora da tabela, calcular percentual: `Soma_Coupon_Value / Soma_Total_Value`

### 💡 Qual a diferença de receita entre usuários que usaram e não usaram cupom?
- **Campo:** `Coupon Value`
- **Tabela Dinâmica:**
  - **Linhas:** `Subscriber ID`
  - **Valores:** Soma de `Total Value`
  - **Filtro:** `Coupon Value` igual a 0 (sem cupom) e maior que 0 (com cupom)
  - **Comparação:** Separar os dois grupos e comparar receitas

### 🎟️ Análise de produtos adicionais como passes
- **Campos:** `EA Play Season Pass`, `EA Play Season Pass Price`, `Minecraft Season Pass`, `Minecraft Season Pass Price`
- **Tabela Dinâmica 1:**
  - **Linhas:** `EA Play Season Pass`
  - **Valores:** Soma de `EA Play Season Pass Price`
- **Tabela Dinâmica 2:**
  - **Linhas:** `Minecraft Season Pass`
  - **Valores:** Soma de `Minecraft Season Pass Price`
