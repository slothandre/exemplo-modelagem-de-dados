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

```sql
SELECT nome, preco FROM produtos
WHERE preco >= 2000 AND preco <= 6000;

-- A query abaixo não retorna registros
-- já que as condições não foram totalmente atendidas
SELECT nome, preco FROM produtos
WHERE preco > 5000 AND preco <= 6000;
```