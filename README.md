# LinConEs

LinConEs = Linguagem de Consulta Estruturada, ou SQL em português (Structured Query Language). 

Aqui é apenas o repositório da especificação da linguagem. Implementações ficam em outros repositórios da Design Líquido.

## Motivação

A mesma das outras linguagens de programação em português da Design Líquido:

- Melhorar o acesso a leigos;
- Quebrar a barreira do inglês;

## Especificação

LinConEs segue o mesmo padrão de SQL, que é de consultar o banco de dados usando uma sintaxe muito parecida com a linguagem natural. Por exemplo:

```sql
SELECIONAR NOME, EMAIL
DE USUARIOS
ONDE ID = 1
```

O que traduz para SQL ANSI como:

```sql
SELECT NOME, EMAIL
FROM USUARIOS
WHERE ID = 1
```

### Seleção de dados

```sql
SELECIONAR NOME, EMAIL
DE USUARIOS
ONDE ID = 1
```

Tradução:

```sql
SELECT NOME, EMAIL
FROM USUARIOS
WHERE ID = 1
```

### Inserção de dados

```sql
INSERIR EM USUARIOS (NOME, EMAIL)
VALORES ("Irmão do Jorel", "irmao@jorel.com")
```

Tradução:

```sql
INSERT INTO USUARIOS (NOME, EMAIL)
VALUES ("Irmão do Jorel", "irmao@jorel.com")
```

### Atualização de dados

```sql
ATUALIZAR USUARIOS
DEFINIR EMAIL = "jorel@jorel.com"
ONDE ID = 2
```

Tradução:

```sql
UPDATE USUARIOS
SET EMAIL = "jorel@jorel.com"
WHERE ID = 2
```

### Exclusão de dados

```sql
EXCLUIR USUARIOS
ONDE ID = 2
```

Tradução:

```sql
DELETE FROM USUARIOS
WHERE ID = 2
```

### Criação de tabelas

```sql
CRIAR TABELA clientes(
    ID INTEIRO NAO NULO CHAVE PRIMARIA AUTO INCREMENTO, 
    NOME TEXTO(100) NAO NULO, 
    IDADE INTEIRO NAO NULO, 
    EMAIL TEXTO(255) NULO, 
    ATIVO LOGICO NAO NULO
);
```

Tradução:

```sql
CREATE TABLE clientes(
    ID INT NOT NULL PRIMARY KEY AUTOINCREMENT, 
    NOME VARCHAR(100) NOT NULL, 
    IDADE INT NOT NULL, 
    EMAIL VARCHAR(255) NULL, 
    ATIVO BOOLEAN NOT NULL
);
```
