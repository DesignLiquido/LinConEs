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

Aqui é apenas o repositório da especificação comum da linguagem. Implementações ficam em outros repositórios da Design Líquido, e demais especificidades de cada tecnologia também.

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

## Implementações

- https://github.com/DesignLiquido/lincones-mysql
- https://github.com/DesignLiquido/lincones-postgresql
- https://github.com/DesignLiquido/lincones-sqlite
