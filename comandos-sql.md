# Comandos SQL - Referências

## Modelagem Física com comandos DDL

### Criar banco de dados

`CREATE DATABASE vendas CHARACTER SET utf8mb4;`

### Criar tabela de fabricantes

```SQL
CREATE TABLE fabricantes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL
);
```

### Visualizar detalhes estruturais da tabela

```sql
DESC fabricantes;
```

### Criar tabela de produtos

```sql
CREATE TABLE produtos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    descricao TEXT(500) NULL,
    preco DECIMAL(6,2) NOT NULL,
    fabricante_id INT NOT NULL
);
```

### Criação do relacionamento entre as tabelas (chave estrangeira)

```sql
ALTER TABLE produtos
    -- CONSTRAINT/RESTRIÇÃO indicam o nome do relacionamento
    ADD CONSTRAINT fk_produtos_fabricantes

    -- Criando a chave-estrangeira (fabricante_id) que
    -- aponta para a chave-primaria (id) de outra tabela (fabricantes)
    FOREIGN KEY (fabricante_id) REFERENCES fabricantes(id);
```

### Exemplos de alterações estruturais na tabela

#### Renomear tabela

```sql
ALTER TABLE fabricantes RENAME TO fornecedores;
```

#### Modificar colunas

```sql
ALTER TABLE produtos
    MODIFY COLUMN preco INT;
```

#### Renomear colunas

```sql
ALTER TABLE fabricantes
    CHANGE nome_antigo nome_novo;
```

#### Adicionar coluna

```sql
ALTER TABLE produtos
    ADD quantidade INT NULL AFTER preco;
```
