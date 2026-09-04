# Comandos CRUD para o banco de dados Fly By Night


# Fornecedores

```sql
-- INSERT de fornecedores
INSERT INTO fornecedores (nome) VALUES ('Eletrônicos Tabajara');

INSERT INTO fornecedores (nome) VALUES
  ('Games ABCD'),
  ('Supermecado Tem de Tudo'),
  ('Livraria Demais da Conta');
```

## INSERT na tabela de produtos
```sql
INSERT INTO produtos (nome, descricao, preco, quantidade, fornecedor_id)
VALUES (
         'Smartphone Galaxy S23',
         'Equipamento com sistema Android e câmera Full hd',
          1599.45,
          20,
          1 
);


INSERT INTO produtos (nome, descricao, preco, quantidade, fornecedor_id)
VALUES (
         'Senhor dos Anéis: As duas torres',
         'Volume 2 da série de livros criados pelo autor J.R.R Tolkien',
          80.99,
          100,
          4 
);
INSERT INTO produtos (nome, descricao, preco, quantidade, fornecedor_id)
VALUES (
         'TV led',
         'Tela de 50 polegadas, resolução 4k, 4 entradas HDMI',
          3420,
          12,
          1 
);
```

## INSERT na tabela de lojas

```sql
INSERT INTO lojas (nome) VALUES
  ('Casas Bahia'),
  ('Shopping Zona Leste'),
  ('Bazar das Coisas'),
  ('Americanas');
```

## INSERT na tabela de lojas-Produtos

esta é uma tabela intermediária (conhecida como **tabela pivot**),
ela se relaciona com outras duas tabelas: **produtos** e **lojas** através de chaves estrangeiras.

```sql
INSERT INTO lojas_produto(loja_id, produto_id, estoque) VALUES
(2, 1, 20);

INSERT INTO lojas_produto(loja_id, produto_id, estoque)VALUES
(4, 2, 3); -- senhor dos aneis

INSERT INTO lojas_produto(loja_id, produto_id, estoque)VALUES
(2, 3, 10 ); -- tv led

INSERT INTO lojas_produto(loja_id, produto_id, estoque)VALUES
(1, 1, 5 ); -- smartphone

INSERT INTO lojas_produto(loja_id, produto_id, estoque)VALUES
(4, 1, 2 ); -- smartphone


```