# ❓ Perguntas de Negócio

Este painel responde perguntas estratégicas utilizando os nomes reais das colunas da base de dados. Os dados estão organizados em blocos temáticos com base nas perguntas de negócio.

---

## 🧭 1. Dashboard  
**Visão geral com indicadores principais e gráficos resumo**

### 📅 Qual a evolução das assinaturas ao longo do tempo?
- **Campo:** `Start Date`
- **Ação:** Agrupar por mês e contar `Subscriber ID`

### 💰 Qual o faturamento total considerando todos os produtos?
- **Campo:** `Total Value`
- **Ação:** Soma total

### 🧍‍♂️ Qual o ticket médio por assinante?
- **Campo:** `Total Value`
- **Cálculo:** Soma de `Total Value` / Distintos `Subscriber ID`

---

## 📊 2. Performance Comercial  
**Análise dos planos, tipos de assinaturas e faturamento**

### 🛍️ Quais planos são os mais vendidos?
- **Campo:** `Plan`
- **Ação:** Contar frequência de cada plano

### 🗃️ Qual tipo de plano gera mais receita?
- **Campo:** `Subscription Type`
- **Ação:** Soma de `Subscription Price` por tipo

### 🔁 Qual a taxa de renovação automática por plano?
- **Campos:** `Auto Renewal`, `Plan`
- **Ação:** Calcular percentual de "Sim" em `Auto Renewal` por `Plan`

### 📈 Qual a tendência de vendas nos últimos meses?
- **Campo:** `Start Date`
- **Ação:** Agrupar por mês e contar `Subscriber ID` ou soma de `Subscription Price`

---

## 🧑‍💼 3. Perfil dos Assinantes  
**Quem são os clientes e como se comportam**

### 🧍‍♂️ Qual o ticket médio por assinante?
- **Campo:** `Total Value`
- **Cálculo:** Soma de `Total Value` / Distintos `Subscriber ID`

### 📅 Qual a evolução das assinaturas ao longo do tempo?
- **Campo:** `Start Date`
- **Ação:** Agrupar por mês e contar `Subscriber ID`

### 🎮 Quais produtos adicionais são mais comprados (EA Play / Minecraft)?
- **Campos:** `EA Play Season Pass`, `Minecraft Season Pass`
- **Ação:** Contar quantos "Sim" por campo

### 🔁 Qual a taxa de renovação automática por plano?
- **Campos:** `Auto Renewal`, `Plan`
- **Ação:** Proporção de "Sim" por plano

---

## 🧾 4. Análise Descontos e Passes  
**Impacto dos cupons e passes extras no faturamento**

### 🧾 Qual o impacto dos cupons de desconto no faturamento?
- **Campos:** `Coupon Value`, `Total Value`
- **Cálculo:** Soma de `Coupon Value` / Soma de `Total Value`

### 💡 Qual a diferença de receita entre usuários que usaram e não usaram cupom?
- **Campo:** `Coupon Value`
- **Filtro:** `= 0` (sem cupom) e `> 0` (com cupom)
- **Cálculo:** Soma de `Total Value` em cada grupo

### 🎟️ Análise de produtos adicionais como passes
- **Campos:** `EA Play Season Pass`, `EA Play Season Pass Price`, `Minecraft Season Pass`, `Minecraft Season Pass Price`
- **Ação:** Contar os "Sim" e somar os respectivos valores
