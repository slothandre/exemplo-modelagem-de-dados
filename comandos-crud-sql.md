# Comandos para operações CRUD no Banco de dados

## Resumo

- C -> CREATE (inserir dados, usando comando `INSERT`)
- R -> READ (ler dados usando comando `SELECT`)
- U -> UPDATE (atualizar dados usando comando `UPDATE`)
- D -> DELETE (excluir dados usando comando `DELETE`)

## INSERT

### Fabricantes

```sql
INSERT INTO fabricantes (nome) VALUES('Asus');

INSERT INTO fabricantes (nome) VALUES('Dell');
INSERT INTO fabricantes (nome) VALUES('Apple');

INSERT INTO fabricantes (nome)
VALUES("LG"), ("Samsung"), ("Brastemp");

INSERT INTO fabricantes (nome)
VALUES("Positivo"), ("Microsoft");
```

### Produtos

```sql
INSERT INTO produtos(
    nome, descricao, preco, quantidade, fabricante_id)
    VALUES(
        "Ultrabook",
        "Equipamento de última geração cheio de recursos, com processador Intel Core i9 do balacobaco",
        3500,
        7,
        2 -- id do fabricante DELL
    );

INSERT INTO produtos(
    nome, descricao, preco, quantidade, fabricante_id)
    VALUES(
        "Tablet Android",
        "Tablet com a versão 14 do sistema operacional Android, possui tela de 10 polegadas e armazenamento de 128 GB, e 64 GB de RAM porque o Eliel perguntou.",
        1500.99,
        5,
        5
    );

INSERT INTO produtos(
    nome, descricao, preco, quantidade, fabricante_id
) VALUES(
    "Geladeira",
    "Geladeira que gela",
    5000,
    12,
    6
),
(
    "iPhone 18 Pro Max",
    "Smartphone Apple cheio das frescuras e caro pra caramba. Coisa de rico...",
    12666.66,
    3,
    3
),
(
    "iPad Mini",
    "Tablet Apple com tela retina display e bla bla bla.",
    4999.01,
    5,
    3
);
```

---

## SELECT

```sql
SELECT * FROM produtos;

SELECT nome, preco FROM produtos;

SELECT preco, nome FROM produtos;

SELECT nome, preco, quantidade FROM produtos WHERE preco < 5000;

-- Mostre nome e descricao somente dos produtos da Apple

SELECT nome, descricao FROM produtos WHERE fabricante_id = 3;
```

### Operadores Lógicos: E, OU, NÃO

#### E

```sql
SELECT nome, preco FROM produtos
WHERE preco >= 2000 AND preco <= 6000;

-- A query abaixo não retorna registros
-- já que as condições não foram totalmente atendidas
SELECT nome, preco FROM produtos
WHERE preco > 5000 AND preco <= 6000;
```

#### OU

```sql
SELECT nome, preco FROM produtos
WHERE preco > 5000 OR preco <= 6000;

-- Exiba nome e preço somente dos produtos da Apple e da Samsung
SELECT nome, preco FROM produtos
WHERE fabricante_id = 3 OR fabricante_id = 5;

SELECT nome, preco FROM produtos
WHERE fabricante_id IN(3, 5);

SELECT nome, preco FROM produtos
WHERE fabricante_id NOT IN(3, 5);
```

#### NÃO

```sql
SELECT nome, descricao, preco FROM produtos
WHERE NOT fabricante_id = 8;

SELECT nome, descricao, preco FROM produtos
WHERE fabricante_id != 8;
```

---

## UPDATE

```sql
UPDATE fabricantes SET nome = "Asus do Brasil"
WHERE id = 1; -- NÃO SE ESQUEÇA DO WHERE!! PERIGO!

UPDATE produtos SET preco = 6549.74
WHERE id = 4;

-- Altere a quantidade dos produtos da Apple e da Samsung
-- para 20
UPDATE produtos SET quantidade = 20
WHERE fabricante_id IN(3, 5);
```

## DELETE

```sql
-- NÃO SE ESQUEÇA DO WHERE!! PERIGO!
DELETE FROM fabricantes WHERE id = 1;
DELETE FROM fabricantes WHERE id = 4;

-- A query abaixo NÃO FUNCIONA devido à restrição
-- de chave estrangeira/relacionamento, ou seja,
-- existem produtos associados ao fabricante 3 (apple)
```

---

## SELECT: outras formas de uso

```sql
SELECT nome, preco FROM produtos ORDER BY nome;
SELECT nome, preco FROM produtos ORDER BY preco;
SELECT nome, preco FROM produtos ORDER BY preco DESC;

-- DESC: classificação em ordem decrescente
-- ASC (padrão): classificação em ordem crescente

SELECT nome, preco FROM produtos
WHERE quantidade = 20 ORDER BY nome;
```

### Busca de dados

```sql
SELECT nome, descricao FROM produtos
WHERE descricao LIKE "%tela%" OR nome LIKE "%tela%";

-- usamos o operador LIKE e o caractere coringa %
-- para permitir uma busca da palavra indicada em
-- qualquer posição dentro do texto. Neste contexto,
-- o % significa "qualquer texto" antes da palavra ou
-- depois da palavra
```