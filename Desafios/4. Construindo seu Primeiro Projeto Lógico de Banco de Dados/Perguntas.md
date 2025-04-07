# Perguntas - Queries Complexas

## 1. Quantos pedidos foram feitos por cada cliente?
```sql
SELECT c.nome, COUNT(p.id_pedido) AS total_pedidos
FROM Cliente c
JOIN Pedido p ON c.id_cliente = p.id_cliente
GROUP BY c.nome;
```

Explicação:
Essa query retorna o nome de cada cliente e quantos pedidos ele já fez.
- Usa JOIN para ligar as tabelas Cliente e Pedido pela chave estrangeira.
- COUNT(p.id_pedido) conta os pedidos associados a cada cliente.
- GROUP BY agrupa os resultados por cliente.

## 2. Algum vendedor também é fornecedor? (Assumindo que vendedor seria o cliente PJ)
```sql

SELECT c.nome
FROM Cliente c
JOIN Fornecedor f ON c.cnpj = f.cnpj
WHERE c.tipo = 'PJ';
```

Explicação: Retorna os nomes de clientes do tipo PJ que também estão cadastrados como fornecedores.
- Compara os CNPJs nas tabelas Cliente e Fornecedor.
- Usa JOIN para unir as informações das duas tabelas.
- WHERE c.tipo = 'PJ' filtra somente os clientes pessoa jurídica.

## 3. Relação de produtos, fornecedores e estoques
```sql

SELECT pr.descricao AS produto, f.razao_social AS fornecedor, SUM(pe.quantidade) AS total_estoque
FROM Produto pr
JOIN Produto_Fornecedor pf ON pr.id_produto = pf.id_produto
JOIN Fornecedor f ON pf.id_fornecedor = f.id_fornecedor
LEFT JOIN Produto_em_Estoque pe ON pr.id_produto = pe.id_produto
GROUP BY pr.descricao, f.razao_social;
```

Explicação: Retorna a lista de produtos, seus respectivos fornecedores e a quantidade total em estoque.

- Usa JOIN entre Produto, Produto_Fornecedor, Fornecedor e Produto_em_Estoque.
- SUM(pe.quantidade) soma o total em estoque para cada produto.
- LEFT JOIN garante que mesmo produtos sem estoque atual sejam listados.

## 4. Relação de nomes dos fornecedores e nomes dos produtos
```sql
SELECT f.razao_social AS fornecedor, p.descricao AS produto
FROM Fornecedor f
JOIN Produto_Fornecedor pf ON f.id_fornecedor = pf.id_fornecedor
JOIN Produto p ON pf.id_produto = p.id_produto;
```

Explicação: Mostra quais produtos são fornecidos por cada fornecedor.
- Usa JOIN entre Fornecedor, Produto_Fornecedor e Produto.
- Retorna os nomes dos fornecedores e as descrições dos produtos associados.

## 5. Total gasto por cliente (atributo derivado)
```sql
SELECT c.nome, SUM(rpp.quantidade * p.valor) AS total_gasto
FROM Cliente c
JOIN Pedido pd ON c.id_cliente = pd.id_cliente
JOIN Relacao_Produto_Pedido rpp ON pd.id_pedido = rpp.id_pedido
JOIN Produto p ON rpp.id_produto = p.id_produto
GROUP BY c.nome
ORDER BY total_gasto DESC;
```

Explicação: Calcula quanto cada cliente já gastou em pedidos.
- Multiplica a quantidade de cada produto pelo seu valor.
- Usa JOIN entre Cliente, Pedido, Relacao_Produto_Pedido e Produto.
- Agrupa por cliente (GROUP BY) e ordena por total gasto (ORDER BY DESC).

## 6. Clientes com mais de 1 pedido
```sql
SELECT c.nome, COUNT(p.id_pedido) AS qtd_pedidos
FROM Cliente c
JOIN Pedido p ON c.id_cliente = p.id_cliente
GROUP BY c.nome
HAVING COUNT(p.id_pedido) > 1;
```

Explicação: Mostra os clientes que fizeram mais de um pedido.
- Conta os pedidos de cada cliente com COUNT.
- Usa GROUP BY para agrupar por nome de cliente.
- HAVING COUNT(p.id_pedido) > 1 filtra apenas aqueles com mais de um pedido.
