# 📊 Tabela de Perguntas Estratégicas e Como Analisar no Excel

Esta tabela reúne as principais perguntas estratégicas de negócio que podem ser respondidas com os dados disponíveis, além de orientar como realizar cada análise no Excel.

| ❓ Pergunta Estratégica | 🔍 Como Analisar no Excel |
|------------------------|---------------------------|
| 📅 Qual a evolução das assinaturas ao longo do tempo? | Criar uma coluna `Ano-Mês` com `=TEXTO([@Start Date];"aaaa-mm")` e gerar um gráfico de linha com contagem de assinantes por mês. |
| 💰 Qual o faturamento total considerando todos os produtos? | Criar coluna `Valor Bruto` somando assinatura + adicionais. Usar soma em tabela dinâmica. |
| 🧾 Qual o impacto dos cupons de desconto no faturamento? | Criar colunas `Faturamento Real` (com desconto) e `Faturamento Total` (sem desconto). Comparar as duas em gráfico ou tabela dinâmica. |
| 🧍‍♂️ Qual o ticket médio por assinante? | Dividir o `Faturamento Real` pelo número de assinantes ou fazer a média do campo `Faturamento Real`. |
| 🛍️ Quais planos são os mais vendidos? | Contar a frequência de cada valor/descrição na coluna `Plan` em uma tabela dinâmica. |
| 🎮 Quais produtos adicionais são mais comprados (EA Play / Minecraft)? | Contar a quantidade de vezes que o valor de cada produto for maior que zero (`> 0`). Pode ser feito com fórmula ou tabela dinâmica com filtro. |
| 🔁 Qual a taxa de renovação automática por plano? | Usar a coluna `Auto Renewal` e fazer contagem de "Sim" por plano. Calcular percentual em relação ao total. |
| 💡 Qual a diferença de receita entre usuários que usaram e não usaram cupom? | Criar campo "Com Cupom/Sem Cupom" e fazer soma do faturamento para cada grupo. Comparar os valores. |
| 🗃️ Qual tipo de plano gera mais receita? | Agrupar por `Subscription Type` e somar o `Faturamento Real`. Comparar com gráfico de colunas. |
| 📈 Qual a tendência de vendas nos últimos meses? | Utilizar a coluna `Ano-Mês` e criar um gráfico de linha com soma de faturamento ou número de assinaturas por mês. |

> 💡 **Dica**: Utilize segmentações (filtros) no Excel para cruzar variáveis como `Plan`, `Auto Renewal`, `Subscription Type` e `Ano-Mês` no dashboard final.
