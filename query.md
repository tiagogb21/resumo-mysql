# SQL

Structure Query Language --> Linguagem de Consulta Estruturada

conceito: É uma linguagem de consulta padronizada usada em SGBDs relacionais

## SGBD

Sistema de Gerenciamento de Banco de Dados.

 e.x: MySQL, PostgreSQL, Oracle, SQL Server

## query

Instrução ou comando usado para interagir com bancos de dados.

É composta por uma série de palavras-chave, cláusulas e expressões que instruem o banco de dados sobre qual ação deve ser executada. 


## Tipos de Queries:

I - DDL: Data Definition Language (Linguagem de Definição de Dados)

    Comandos que lidam com a organização de um banco de dados.

    1 - CREATE: Usado para criar:
        
        - bancos de dados,
        - tabelas,
        - índices,
        - views,
        - procedures,
        - functions e
        - triggers;

    2 - ALTER: Usado para fazer mudanças na estrutura de objetos existentes;

    3 - DROP: Usado para excluir objetos;

    4 - TRUNCATE: Usado para esvaziar os dados uma tabela, mantendo-a no banco de dados.

II - DML: Data Manipulation Language (Linguagem de Manipulação de Dados)

    Comandos que são usados para manipular dados. (CRUD)

    1 - SELECT: Usado para buscar dados em um banco de dados;

    2 - INSERT: Usado para inserir dados em uma tabela;

    3 - UPDATE: Usado para alterar dados dentro de uma tabela;

    4 - DELETE: Usado para excluir dados de uma tabela.

III - DCL: Data Control Language (Linguagem de Controle de Dados)

     Comandos que concedem direitos, permissões e outros tipos de controle ao sistema de banco de dados.

    1 - GRANT: Usado para dar a um usuário o acesso a determinadas partes do banco de dados;

    2 - REVOKE: Usado para remover os acessos concedidos pelo comando 'GRANT'.

IV - TCL: Transactional Control Language

    Comandos que lidam com as transações dentro de suas pesquisas.

    1 - COMMIT: Usado para tornar as alterações em um banco de dados permanentes.

    2 - ROLLBACK: Usado para desfazer as alterações feitas por um comando;

    3 - SAVEPOINT: Usado para definir pontos onde uma transação pode ser revertida para um estado anterior;

    4 - TRANSACTION: Usados para definir como as transações são executadas, onde e em que escopo.