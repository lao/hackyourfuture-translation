# Folha de dicas SQL

## Consultas

### Especifique quais informações extrair

```sql
SELECIONAR coluna
```

## De qual tabela

```sql
DA mesa
```

## Extraia apenas linhas onde a condição é válida

(Usado com um operador: `>, <, >=, <=, =, <>, BETWEEN, LIKE, IN`)
```sql
WHERE coluna = 'valor'
```

## Combinando cláusulas `WHERE`:

(Usado com: 'AND, OR')
```sql
WHERE coluna = 'valor' OU
      coluna = 'outro valor'
```

## Agregando resultados:

(Usado com: `SUM, COUNT, MIN, MAX, AVG`)
```sql
SELECIONAR SOMA(coluna)
DA mesa
```

## Tabelas de alias

```sql
SELECT coluna AS alias
DA mesa
```
