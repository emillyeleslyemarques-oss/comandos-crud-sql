## SELECT consultar os dados dos usuarios

1. Consulte todos os dados de todos os usuários cadastrados.
```sql
SELECT * FROM usuarios;
```


```sql
SELECT nome, email, senha FROM usuarios;
```

## categorias
```sql
SELECT * FROM categorias;
```

## Noticias
```sql
SELECT titulo, data FROM noticias ;
```

## Faça uma consulta utilizando AS para alterar o nome de pelo menos duas colunas no resultado
```sql
SELECT
      nome AS nome_do_usuario,
      email AS contato_email 
FROM  usuarios;
```

### Consulte somente os usuários de um determinado tipo, de acordo com os dados existentes no seu banco.

```sql
SELECT  nome, email, tipo 
FROM usuarios 
WHERE tipo = 'editor';
```

```sql
SELECT  titulo, resumo, data, destaque
FROM noticias 
WHERE destaque = 'sim';
```

```sql
SELECT  titulo, resumo, data, categoria_id 
FROM noticias 
WHERE categoria_id = 2;
```

```sql
SELECT  nome, email, tipo 
FROM usuarios 
WHERE tipo <> 'editor';
```

```sql
SELECT nome, email, senha, tipo
FROM usuarios
WHERE nome = 'Daniela Rocha'
AND email = 'daniela@email.com';
```

```sql
SELECT nome, email, senha, tipo
FROM usuarios
WHERE nome = 'Eduardo Lima'
OR nome = 'Gabriel Santos';
```

```sql
SELECT nome, email, senha, tipo
FROM usuarios
WHERE tipo
LIKE '%editor%';
```

```sql
SELECT nome
FROM categorias
WHERE nome
LIKE '%d%'
```

```sql
SELECT COUNT(*) AS total_usuarios FROM usuarios;
```

```sql
SELECT COUNT(*) AS total_noticias FROM noticias;
```

```sql
SELECT 
    MIN(data) AS noticia_mais_antiga,
    MAX(data) AS noticia_mais_recente
FROM noticias;
```

# Desafio

```sql
SELECT titulo, resumo, texto, imagem, destaque, data, usuario_id
FROM noticias
WHERE titulo
LIKE '%tecnologia%'
AND destaque = 'sim'
ORDER BY data DESC;
```