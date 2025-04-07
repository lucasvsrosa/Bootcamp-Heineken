# 🔍 Consultas SQL - Oficina Mecânica

Este arquivo apresenta uma série de **consultas SQL complexas** baseadas no modelo lógico do projeto Oficina Mecânica. Elas foram desenvolvidas para fornecer uma análise mais profunda do banco de dados, conforme solicitado no desafio.

---

## 1. Qual é o valor estimado total de cada Ordem de Serviço considerando mão de obra e peças utilizadas?

```sql
SELECT os.id, 
       SUM(s.valor_mao_obra + (osp.quantidade * p.valor_unitario)) AS valor_estimado
FROM OrdemServico os
JOIN OrdemServicoServico oss ON oss.ordem_servico_id = os.id
JOIN Servico s ON s.id = oss.servico_id
LEFT JOIN OrdemServicoPeca osp ON osp.ordem_servico_id = os.id
LEFT JOIN Peca p ON p.id = osp.peca_id
GROUP BY os.id;
```

---

## 2. Quais equipes realizaram mais de 3 ordens de serviço?

```sql
SELECT equipe_id, COUNT(*) AS total_os
FROM OrdemServico
GROUP BY equipe_id
HAVING total_os > 3;
```

---

## 3. Qual foi o valor total pago por cada cliente nas ordens de serviço?

```sql
SELECT c.nome, SUM(p.valor_total) AS total_pago
FROM Cliente c
JOIN OrdemServico os ON os.cliente_id = c.id
JOIN Pagamento p ON p.ordem_servico_id = os.id
GROUP BY c.nome
ORDER BY total_pago DESC;
```

---

## 4. Quais são os serviços mais utilizados nas ordens de serviço?

```sql
SELECT s.nome, COUNT(*) AS total_execucoes
FROM OrdemServicoServico oss
JOIN Servico s ON s.id = oss.servico_id
GROUP BY s.nome
ORDER BY total_execucoes DESC;
```

---

## 5. Quais peças foram mais utilizadas e qual o total gasto com cada uma?

```sql
SELECT p.nome, 
       SUM(osp.quantidade) AS total_usada, 
       SUM(osp.quantidade * p.valor_unitario) AS total_gasto
FROM OrdemServicoPeca osp
JOIN Peca p ON p.id = osp.peca_id
GROUP BY p.nome
ORDER BY total_gasto DESC;
```

---

## 6. Qual o valor médio das ordens de serviço concluídas em cada mês?

```sql
SELECT DATE_FORMAT(data_emissao, '%Y-%m') AS mes, 
       AVG(p.valor_total) AS media_os
FROM OrdemServico os
JOIN Pagamento p ON p.ordem_servico_id = os.id
WHERE os.status = 'Concluída'
GROUP BY mes
ORDER BY mes;
```

---

## 7. Quais veículos de um cliente específico já passaram por manutenção?

```sql
SELECT v.placa, v.modelo, os.id AS ordem_servico_id
FROM Veiculo v
JOIN OrdemServico os ON os.veiculo_placa = v.placa
JOIN Cliente c ON c.id = v.cliente_id
WHERE c.nome = 'João da Silva';
```

---

📝 Essas queries cobrem cláusulas como `WHERE`, `GROUP BY`, `HAVING`, `ORDER BY`, expressões derivadas, e junções entre múltiplas tabelas.

