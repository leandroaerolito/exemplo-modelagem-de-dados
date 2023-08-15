
CREATE DATABASE catalogo_de_filmes CHARACTER SET utf8mb4;

## Comandas Exercíco

``` SQL
CREATE TABLE generos ( 
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL
    );
```

```SQL
CREATE TABLE filmes (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(45) NOT NULL,
    ano YEAR(4) NOT NULL,
    genero INT NOT NULL
);
```

```SQL
ALTER TABLE filmes
    CHANGE genero genero_id;
```

```SQL
ALTER TABLE filmes
    ADD CONSTRAINT fk_filmes_generos

    FOREIGN KEY
```
