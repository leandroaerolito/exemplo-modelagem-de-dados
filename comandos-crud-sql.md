# Comandos para operações CRUD no Banco de Dados

## RESUMO

C -> CREATE (inserir dados usando comando `INSERT`)
R -> READ (ler dados usando o comando `SELECT`)
U -> UPDATE (atualizar dados usando o comando `UPDATE`)
D -> DELETE (excluir dados usando comando `DELETE`)

### Fabricantes

```sql
INSERT INTO fabricantes (nome_do_fabricante) VALUES ('Asus');
INSERT INTO fabricantes (nome_do_fabricante) VALUES ('Dell');
INSERT INTO fabricantes (nome_do_fabricante) VALUES ('Apple');

INSERT INTO fabricantes (nome_do_fabricante)
VALUES ('LG'), ('Samsung'), ('Brastemp');

INSERT INTO fabricantes (nome_do_fabricante)
VALUES ('Positivo'), ('Microsoft');
```

### PRODUTOS

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