# SQL SELECT - Exemplos consultas ao banco Fly BY Night

O comando `SELECT` é usado para **consultar dados armazenados nas tabelas do banco de dados**

# SELECT basico: consultar todos os dados de uma tabela:

```sql
SELECT * FROM produtos;
```

## SELECT para apenas determinadas colunas

```sql
SELECT nome, preco FROM produtos;
```

## Alterando o nome de exibição das colunas

Usamos o comando `AS` para criar um **apelido (alias)**.

```sql
SELECT
      nome AS produto,
      preco AS valor 
FROM  produtos;
```

## filtrando registros com WHERE

o `WHERE` permite determinar **quais registros deve aparecer** no resultado. Na pratica, são condiçoes para execução do `SELECT`.

### Comparação de igualdade

```sql
SELECT * FROM produtos WHERE quantidade = 0;
```

### Comparação de maior 

```sql
SELECT nome, preco FROM produtos WHERE preco > 1000;
```

## Comparação de menor igual
```sql
SELECT nome, preco FROM produtos WHERE preco <= 1000;
```

## Comparação de diferença

Normalmenre se usa o operador `<>` em de `!=`.

```sql
SELECT * FROM produtos WHERE fornecedor_id <> 1;
```


```sql
```




