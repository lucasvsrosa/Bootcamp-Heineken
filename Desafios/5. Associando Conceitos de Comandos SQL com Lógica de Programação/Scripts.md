# Scripts SQL - Desafios

Este arquivo contém os scripts corretos para cada desafio proposto.

---

## Desafio 1: Reconhecendo Comandos SQL Básicos

```python
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

# Entrada e saída
entrada = input()
print(descrever_comando_sql(entrada))
```

---

## Desafio 2: Associando Tipos de Dados SQL

```python
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

# Entrada e saída
entrada = input()
print(descrever_tipo_dado_sql(entrada))
```

---

## Desafio 3: Comandos SQL de Filtragem, Agrupamento e Ordenação

```python
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

# Entrada e saída
entrada = input()
print(descrever_comando_sql(entrada))
```
