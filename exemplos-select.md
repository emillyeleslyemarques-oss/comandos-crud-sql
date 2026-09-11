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

---

## Combinando condições
Usamos `WHERE` e operadores lógicos e relacionais.

### Operador AND (E)

Exibir os produtos que custem menos de 500 e quantidade acima de 20.

```sql
SELECT nome, preco, quantidade FROM produtos
WHERE preco < 500 AND quantidade > 20;
```

## Operador OR (OU)

Exibir os produtos que custem mais de 3000 ou com quantidade zerada.

```sql
SELECT nome, preco, quantidade FROM produtos
WHERE preco > 3000 OR quantidade = 0;
```

### Operador NOT (NÃO)
Exibir os produtos que **Não possuem preço acima de 1000**.

````sql
SELECT nome, preco FROM produtos WHERE NOT preco > 1000;
````
**OBS:** o uso do not nao é obrigatorio, desde que voce consiga o mesmo resultado usando uma logica diferente.

### BETWEEN

Exibir produtos com preco **entre 100 e 500**

````sql
SELECT nome, preco FROM produtos
WHERE preco BETWEEN 100 AND 500;
````

### IN

Exibir produtos que tenham o fornecedor ID , 1, 4 OU 8;

```sql
SELECT * FROM produtos 
WHERE fornecedor_id IN (1, 4, 8);
```

### Operador LIKE

`LIKE` é usado principalmente para realizar pesquisas em textos. Junto com o caractere `%` permite fazer buscas baseadas em partes de uma string.

Exemplo: procurar produtos que tenham a palavra **Gamer** em qualquer posição do nome.

```sql
SELECT nome, preco FROM produtos
WHERE nome LIKE '%Gamer%';
```

## DISTINCT

Eliminar valores repetidos da consulta

```sql
SELECT DISTINCT fornecedor_id FROM produtos;
```

## ORDENAÇÃO (CLASSIFICAÇÃO)

Usamos o `ORDER BY` para organizar os registros do resultado

### ORDEM CRESCENTE

Exemplos: do menor para o maior, ou de A a Z,
 de mais antigo para mais recente

```sql
SELECT nome, preco FROM produtos
ORDER BY preco ASC; 
-- nem precisa colocar é padrão o ASC.
```

### ORDEM DECRESCENTE

Exemplos: do maior para o menor, ou de Z a A, ou de mais recente para o mais antigo.

```sql
SELECT nome, preco FROM produtos
ORDER BY preco DESC;
```


### Ordenando por mais de uma coluna 
```sql
SELECT nome, preco FROM produtos
ORDER BY preco DESC, nome ASC;
```

## Funções de agregação 

Funções de agregação realizam cálculos ou processos em registros de um resultado.

Entre as principais

-`COUNT()` -> conta registros
-`SUM()` -> soma valores
-`AVG()` -> calcula a média de valores
-`MIN()` -> encontra o valor menor
-`MAX()` -> encontra o valor maior
-`ROUND` -> arredonda valores e define casas decimais

### COUNT

Contando quantos registros existem na tabela produtos

```sql
SELECT COUNT(*) AS total FROM produtos;
```

### SUM

Somar quantidade de todos os produtos da tabela.

```sql
SELECT SUM(quantidade) AS "Quantidade total" FROM produtos;
```


### AVG

Calcular a media dos precos dos produtos

```sql
SELECT AVG(preco) AS "Média dos Preços" FROM produtos;
```

### MIN

Retornar o menor preço existente

```sql
SELECT MIN(preco) AS menor_preco FROM produtos;
```

### MAX

Retornar o maior preço existente

```sql
SELECT MAX(preco) AS maior_preco FROM produtos;
```

### Combinando agregações

```sql
SELECT COUNT(*) AS quantidade_produtos,
       MIN(preco) AS menor_preco,
       MAX(preco) AS maior_preco,
       ROUND(AVG(preco), 2) AS preco_medio
FROM produtos;
```

## Recursos de agrupamento

`GROUP BY` reune registros que possuem um determinado valor me cumum.

### Contando produtos por fornecedor 

Exemplo: descobrir quantos produtos existem em cada fornecedor

```sql
SELECT fornecedor_id, COUNT(*) AS total_produtos
FROM produtos GROUP BY fornecedor_id;
```

### Determinando a media de precos por fornecedor

```sql
SELECT fornecedor_id, AVG(preco) AS preco_medio
FROM produtos GROUP BY fornecedor_id;
```

### HAVING

`HAVING` permite filtrar os grupos criados pelo `GROUP BY`.

**Obs:** para usar o HAVING **PRECISA TER GROUP BY**.

Exemplo: mostrar somente os fornecedores que possuem pelo menos dois produtos cadastrados.

```sql
SELECT fornecedor_id, COUNT(*) AS total_produtos
FROM produtos GROUP BY fornecedor_id
HAVING total_produtos >= 2;
```


### Combinando WHERE, GROUP BY, HAVING e ORDER BY

Objetivos:

1. Considera produtos com quantidade maior que zero
2. Agrupa por fornecedor
3. Calcula a quantidade e preço médio de cada grupo
4. Mantém apenas fornecedores com pelo menos dois produtos
5. Ordena os grupos pelo preço médio

```sql
SELECT 
    fornecedor_id, 
    COUNT(*) AS total_produtos,
    ROUND(AVG(preco), 2) AS preco_medio
FROM produtos
      WHERE quantidade > 0
      GROUP BY fornecedor_id
      HAVING total_produtos >= 2
      ORDER BY preco_medio DESC;
```

**Obs:** ao combinar estes recursos, a ordem deve ser:

1. WHERE
2. GROUP BY/ HAVING
3. ORDER BY