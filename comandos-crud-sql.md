# Comandos para operações CRUD no Banco de Dados

## RESUMO

C -> CREATE (inserir dados usando comando `INSERT`)
R -> READ (ler dados usando o comando `SELECT`)
U -> UPDATE (atualizar dados usando o comando `UPDATE`)
D -> DELETE (excluir dados usando comando `DELETE`)

## CREATE
### INSERT
#### Fabricantes

```sql
INSERT INTO fabricantes (nome_do_fabricante) VALUES ('Asus');
INSERT INTO fabricantes (nome_do_fabricante) VALUES ('Dell');
INSERT INTO fabricantes (nome_do_fabricante) VALUES ('Apple');

INSERT INTO fabricantes (nome_do_fabricante)
VALUES ('LG'), ('Samsung'), ('Brastemp');

INSERT INTO fabricantes (nome_do_fabricante)
VALUES ('Positivo'), ('Microsoft');
```

#### PRODUTOS

``` sql
INSERT INTO produtos(nome, preco, descricao, quantidade, fabricante_id)
    VALUES (
        'Ultrabook', 
        3500,
        'Equipamento de última geração cheio de recursos, como processador Intel Core i9 do balacobaco.',
        7,
        2 -- id do fabricante Dell 
);

INSERT INTO produtos(nome, preco, descricao, quantidade, fabricante_id)
    VALUES (
        'Tablet Android',
        1500.99,
        'Tablet com a versão 14 do sistema operacional Android, possui tela de 10 polegadas e armazenamento de 128GB e 64GB de RAM.',
        5,
        5
    );

INSERT INTO produtos(nome, preco, descricao, quantidade, fabricante_id)
    VALUES ('Geladeira', 5000, 'Refrigerador frost-free com acesso à internet', 12, 6), 
           ('Iphone 18 Pro Max', 12667.65, 'Smartphone Apple cheio das frescuras e caro prao caramba. Coisa de playba.', 3, 3), 
           ('iPad mini', 4999.01, 'Tablet Apple com tela retina display e bla bla bla.', 5, 3);
```

``` SQL
INSERT INTO produtos(
    nome, descricao, preco, quantidade, fabricante_id
) VALUES(
    'Xbox Series S',
    'Velocidade e desempenho de última geração',
    1997,
    5,
    8
);

INSERT INTO produtos(
    nome, descricao, preco, quantidade, fabricante_id
) VALUES(
    'Notebook Motion',
    'Intel Dual Core 4GB de RAM, 128GB SSD e Tela 14,1 polegadas.',
    1213.65,
    8,
    7
);
```

## READ
### SELECT

#### Produtos

``` SQL
SELECT * FROM produtos;

SELECT nome, preco FROM produtos;

SELECT preco, nome FROM produtos;

SELECT nome, preco, quantidade FROM produtos
WHERE preco < 5000;

-- Mostre nome e descrição somente dos produtos da Apple
SELECT nome, descricao FROM produtos
WHERE fabricante_id = 3;
```


## OPERADORES LÓGICOS: "E", "OU" e "NÃO"

### E
```SQL 
SELECT nome, preco FROM produtos
WHERE preco >= 2000 AND preco <= 6000; 

-- A query abaixo não retorna registros
-- já que as condições não foram totalmente atendidas
SELECT nome, preco FROM produtos
WHERE preco > 5000 AND preco <= 6000; 
```

### OU
``` SQL

SELECT nome, preco FROM produtos
WHERE preco > 5000 OR preco <= 3000; 

-- Exiba nome e preço somente dos produtos
-- da Apple e da Samsung
SELECT nome, preco FROM produtos
WHERE fabricante_id = 3 OR fabricante_id = 5;

-- versão usando a função IN()
SELECT nome, preco FROM produtos
WHERE fabricante_id IN(3, 5);

SELECT nome, preco FROM produtos
WHERE fabricante_id NOT IN(3, 5);
```

### NÃO

``` SQL
SELECT nome, descricao, preco FROM produtos
WHERE NOT fabricante_id = 8;

-- versão usando operador relacional "diferença/diferente"
SELECT nome, descricao, preco FROM produtos
WHERE fabricante_id != 8;
```


## UPDATE
``` sql
UPDATE fabricantes SET nome = 'Asus do Brasil'
WHERE id = 1; -- ☠️ NÃO SE ESQUEÇA DO WHERE!! PRERIGO! ☠️

-- SE FOR FAZER, TROCA PRA TABELA ZUEIRA!!!
-- UPDATE fabricantes_zueira SET nome = 'Asus do Paraguai';

UPDATE produtos SET preco = 6549.74
WHERE id = 4;

-- Altere a quantidade dos produtos da Apple e da Samsung
-- para 20
UPDATE produtos SET quantidade = 20
-- WHERE fabricante_id = 3 OR fabricante_id = 5;
-- WHERE id = 2 OR id = 4 OR id = 5;
WHERE fabricante_id IN(3, 5);
```

## DELETE

```SQL
-- NÃO SE ESQUEÇA DO 'WHERE'!!!!!!!!
DELETE FROM fabricantes WHERE id = 1;
DELETE FROM fabricantes WHERE id = 4;

-- A QUERY abaixo NÃO FUNCIONA devido à restrição
-- de chave estrangeira/relacionamento, ou seja, 
-- existem produtos associados ao fabricante 3 (Apple)
-- DELETE FROM fabricantes WHERE id = 3;
```

---

## SELECT: outras formas de uso

``` SQL
SELECT nome, preco FROM produtos ORDER BY nome;
SELECT nome, preco FROM produtos ORDER BY preco;
SELECT nome, preco FROM produtos ORDER BY preco DESC;

-- DESC: Classificação em ordem decrescente
-- ASC (padrão): classificação em ordem crescente
```

``` SQL
SELECT nome, preco FROM produtos
WHERE quantidade = 20 ORDER BY nome;
```

### BUSCA DE DADOS
---
``` sql
SELECT nome, descricao FROM produtos
WHERE descricao LIKE '%tablet%';

-- Usamos o operador LIKE e o caractere coringa %
-- parar permitir uma busca da palavra indicada em 
-- qualquer posição dentro do texto. Neste contexto,
-- o % significa "qualquer texto" antes da palavra ou 
-- depois da palavra.
```
---
### OPERAÇÕES E FUNÇÕES DE AGREGAÇÃO
``` sql
SELECT SUM(preco) FROM produtos; -- SOMA
SELECT SUM(preco) as Total FROM produtos; -- alias/apelido

-- Exemplo de alias/apelido para outras colunas
SELECT nome as Produto, preco as "Preço" FROM produtos;
SELECT nome Produto, preco "Preço" FROM produtos;

-- MÉDIA

SELECT AVG(preco) as "Média dos Preços" FROM produtos;
SELECT ROUND(AVG(preco), 2) as "Média dos Preços" FROM produtos;

-- CONTAGEM
SELECT COUNT(id) as "Qtd de Produtos" FROM produtos;

SELECT COUNT(fabricante_id) as "Qtd de fabricante com produtos" FROM produtos;

-- DISTINCT é uma cláusula/flag que evita a duplicidade na contagem de registros.
```

---
### OPERAÇÕES MATEMÁTICAS
---
```SQL
SELECT nome, preco, quantidade, (preco * quantidade) as Total FROM produtos;
```
---
### SEGMENTAÇÃO/AGRUPAMENTO DE RESULTADOS
```SQL
-- UPDATE produtos SET fabricante_id = 2 WHERE id = 2;
SELECT fabricante_id, SUM(preco) as Total FROM produtos GROUP BY fabricante_id;
```




