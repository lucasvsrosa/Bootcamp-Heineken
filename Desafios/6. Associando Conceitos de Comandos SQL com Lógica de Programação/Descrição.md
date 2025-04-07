# Desafios de Comandos SQL

## Desafio 1: Reconhecendo Comandos SQL Básicos

### Descrição
Em um banco de dados relacional, diferentes comandos SQL são usados para manipular dados. Sua tarefa é criar uma função que receba o nome de um comando SQL e retorne uma breve descrição de sua função.

### Entrada
O nome de um comando SQL, como:
- `SELECT`
- `INSERT`
- `UPDATE`
- `DELETE`

### Saída
A saída esperada será a descrição correspondente ao comando SQL:
- `SELECT`: "Usado para consultar dados em uma tabela"
- `INSERT`: "Usado para inserir novos dados em uma tabela"
- `UPDATE`: "Usado para atualizar registros existentes em uma tabela"
- `DELETE`: "Usado para deletar registros de uma tabela"

### Código Base

```python
# Recebe a entrada do usuário e armazena na variável "entrada"
entrada = input()

# Função responsável por receber um comando SQL e retornar sua descrição.
def descrever_comando_sql(comando):
    if comando == "SELECT":
        return "Usado para consultar dados em uma tabela"
    elif comando == "INSERT":
        return "Usado para inserir novos dados em uma tabela"
    elif comando == "UPDATE":
        return "Usado para atualizar registros existentes em uma tabela"
    elif comando == "DELETE":
        return "Usado para deletar registros de uma tabela"
    else:
        return "Comando SQL desconhecido"

# Imprime a descrição do comando recebido na entrada
print(descrever_comando_sql(entrada))
```

---

## Desafio 2: Associando Tipos de Dados SQL

### Descrição
Diferentes tipos de dados são usados para armazenar informações específicas em um banco de dados relacional. Sua tarefa é implementar uma função que associe o nome de um tipo de dado SQL à sua descrição básica.

### Entrada
O nome de um tipo de dado SQL, como:
- `VARCHAR`
- `INT`
- `DATE`
- `FLOAT`

### Saída
A saída esperada será a descrição correspondente ao tipo de dado SQL:
- `VARCHAR`: "Usado para armazenar cadeias de caracteres"
- `INT`: "Usado para armazenar números inteiros"
- `DATE`: "Usado para armazenar datas"
- `FLOAT`: "Usado para armazenar números decimais"

### Código Base

```python
# Recebe a entrada do usuário e armazena na variável "entrada"
entrada = input()

# Função responsável por associar tipos de dados SQL a suas descrições
def descrever_tipo_dado_sql(tipo):
    if tipo == "VARCHAR":
        return "Usado para armazenar cadeias de caracteres"
    elif tipo == "INT":
        return "Usado para armazenar números inteiros"
    elif tipo == "DATE":
        return "Usado para armazenar datas"
    elif tipo == "FLOAT":
        return "Usado para armazenar números decimais"
    else:
        return "Tipo de dado SQL desconhecido"

# Imprime a descrição do tipo de dado recebido na entrada
print(descrever_tipo_dado_sql(entrada))
```

---

## Desafio 3: Comandos SQL de Filtragem, Agrupamento e Ordenação

### Descrição
Além dos comandos básicos, SQL possui cláusulas específicas para filtragem, agrupamento e ordenação de registros. Sua tarefa é implementar uma função que associe o nome de um desses comandos à sua descrição básica.

### Entrada
O nome de um comando SQL, como:
- `WHERE`
- `GROUP BY`
- `ORDER BY`
- `HAVING`

### Saída
A saída esperada será a descrição correspondente ao comando SQL:
- `WHERE`: "Usado para filtrar registros com base em uma condição"
- `GROUP BY`: "Usado para agrupar registros por colunas específicas"
- `ORDER BY`: "Usado para ordenar os registros de uma consulta"
- `HAVING`: "Usado para filtrar grupos com base em uma condição"

### Código Base

```python
# Recebe a entrada do usuário e armazena na variável "entrada"
entrada = input()

# Função responsável por associar comandos SQL de filtragem, agrupamento e ordenação às suas descrições
def descrever_comando_sql(comando):
    if comando == "WHERE":
        return "Usado para filtrar registros com base em uma condição"
    elif comando == "GROUP BY":
        return "Usado para agrupar registros por colunas específicas"
    elif comando == "ORDER BY":
        return "Usado para ordenar os registros de uma consulta"
    elif comando == "HAVING":
        return "Usado para filtrar grupos com base em uma condição"
    else:
        return "Comando SQL desconhecido"

# Imprime a descrição do comando recebido na entrada
print(descrever_comando_sql(entrada))
```
