# LinConEs

<p align="center">
    <img src="./recursos/imagens/icone-lincones.png" width="auto" height="281" />
</p>

<p align="center">
    <a href="https://github.com/DesignLiquido/LinConEs/issues" target="_blank"><img src="https://img.shields.io/github/issues/Designliquido/LinConEs" /></a>
    <img src="https://img.shields.io/github/stars/Designliquido/LinConEs" />
    <img src="https://img.shields.io/github/forks/Designliquido/LinConEs" />
    <img src="https://img.shields.io/github/license/Designliquido/LinConEs" />
    <br />
</p>

<p align="center">
    Acompanhe a Design Líquido nas redes sociais:
</p>

<p align="center">
    <a href="https://twitter.com/designliquido" target="_blank"><img src="https://img.shields.io/static/v1?style=for-the-badge&message=Twitter&color=1DA1F2&logo=Twitter&logoColor=FFFFFF&label=" /></a>
    <a href="https://www.instagram.com/design.liquido" target="_blank"><img src="https://img.shields.io/static/v1?style=for-the-badge&message=Instagram&color=E4405F&logo=Instagram&logoColor=FFFFFF&label=" /></a>
    <a href="https://www.youtube.com/channel/UCJRn3B7r0aex6LCaOyrQtZQ" target="_blank"><img src="https://img.shields.io/static/v1?style=for-the-badge&message=YouTube&color=FF0000&logo=YouTube&logoColor=FFFFFF&label=" /></a>
    <a href="https://www.linkedin.com/company/design-liquido" target="_blank"><img src="https://img.shields.io/static/v1?style=for-the-badge&message=LinkedIn&color=0A66C2&logo=LinkedIn&logoColor=FFFFFF&label=" /></a>
    <a href="https://www.tiktok.com/@designliquido" target="_blank"><img src="https://img.shields.io/static/v1?style=for-the-badge&message=TikTok&color=000000&logo=TikTok&logoColor=FFFFFF&label=" /></a>
</p>

LinConEs = Linguagem de Consulta Estruturada, ou SQL em português (Structured Query Language).

Aqui é apenas o repositório da especificação comum da linguagem, bem como uma listagem de todos os recursos que envolvem a linguagem. Implementações ficam em outros repositórios da Design Líquido, e demais especificidades de cada tecnologia também.

## Motivação

A mesma das outras linguagens de programação em português da Design Líquido:

- Melhorar o acesso a leigos;
- Quebrar a barreira do inglês;

## Demonstração online

LinConEs tem uma demonstração online usando IndexedDB: https://designliquido.github.io/lincones-demo-web.

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

Com lista de colunas explícita:

```sql
INSERIR EM USUARIOS (NOME, EMAIL)
VALORES ("Irmão do Jorel", "irmao@jorel.com")
```

Sem lista de colunas (implícita, valores na ordem de criação da tabela):

```sql
INSERIR EM USUARIOS
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
EXCLUIR DE USUARIOS
ONDE ID = 2
```

Ou

```sql
EXCLUIR EM USUARIOS
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

### Alteração de Tabelas

O comando `ALTERAR TABELA` permite realizar diversas operações sobre colunas e restrições.

#### Adicionar Coluna

```sql
ALTERAR TABELA usuarios
ADICIONAR COLUNA email TEXTO(80);
```

Tradução:

```sql
ALTER TABLE usuarios
ADD COLUMN email VARCHAR(80);
```

#### Adicionar Coluna com restrição NOT NULL

```sql
ALTERAR TABELA produtos
ADICIONAR COLUNA categoria TEXTO NAO NULO;
```

Tradução:

```sql
ALTER TABLE produtos
ADD COLUMN categoria TEXT NOT NULL;
```

#### Alterar Coluna

```sql
ALTERAR TABELA produtos
ALTERAR COLUNA preco NUMERO;
```

Tradução:

```sql
ALTER TABLE produtos
ALTER COLUMN preco NUMERIC;
```

#### Remover Coluna

```sql
ALTERAR TABELA produtos
REMOVER COLUNA descricao;
```

Tradução:

```sql
ALTER TABLE produtos
DROP COLUMN descricao;
```

#### Renomear Coluna

```sql
ALTERAR TABELA usuarios
RENOMEAR COLUNA email PARA correio_eletronico;
```

Tradução:

```sql
ALTER TABLE usuarios
RENAME COLUMN email TO correio_eletronico;
```

> Importante: a implementação de renomear colunas varia conforme o banco de dados.

#### Adicionar Restrição

```sql
ALTERAR TABELA pedidos
ADICIONAR RESTRIÇÃO chave_estrang
CHAVE ESTRANGEIRA (cliente_id)
REFERENCIA clientes (id);
```

Tradução:

```sql
ALTER TABLE pedidos
ADD CONSTRAINT chave_estrang
FOREIGN KEY (cliente_id)
REFERENCES clientes (id);
```

#### Remover Restrição

```sql
ALTERAR TABELA fornecedores
REMOVER RESTRIÇÃO unique_nome;
```

Tradução:

```sql
ALTER TABLE fornecedores
DROP CONSTRAINT unique_nome;
```


## Implementações

- https://github.com/DesignLiquido/lincones-mysql
- https://github.com/DesignLiquido/lincones-postgresql
- https://github.com/DesignLiquido/lincones-sqlite
