# Banco de Dados

## Conceito:

    É uma coleção organizada de dados que são armazenados e gerenciados de forma eficiente para atender às necessidades de uma aplicação.

    Um banco de dados é como uma biblioteca organizada, mas para informações digitais. Ele é projetado para armazenar, gerenciar e recuperar dados de maneira eficiente, atendendo às necessidades de várias aplicações e sistemas.

## SQL (Structured Query Language)
    
    É uma linguagem de programação usada para gerenciar bancos de dados relacionais. 

## Normalização:

    É o processo de organizar os dados em uma tabela de forma a eliminar redundâncias e dependências funcionais, garantindo assim a integridade dos dados.

### Dados:

    Dados são os blocos de construção do conhecimento digital. 

    Representam informações sobre objetos, eventos ou entidades. 

### Informações:

    São dados com significado e utilidade. (informação = dado + significado + utilidade)

### Tabelas:

    São estruturas de dados que funcionam como as estantes da nossa biblioteca de dados.

    Consistem em linhas (registros ou tuplas) e colunas (campos).

    Função: armazenam dados de maneira organizada.

### Registro (Linha):

    São como livros na estante. Cada registro Representa uma entidade ou um objeto específico.

### Campos (Coluna):

    São as categorias dos livros. Representam atributos ou características dos registros.



### Transações:

    São ações executadas no banco de dados.
    
    Garantem a consistência dos dados, seguindo o princípio ACID.

## ACID:

### ATOMICIDADE

    A atomicidade garante que ou a operação é concluída inteiramente ou não ocorre. (NUNCA pela metade)

    É como um átomo que nunca pode ser dividido ao meio.

### CONSISTÊNCIA

    Protege a integridade dos dados.
    Todas as operações legítimas devem passar por verificações rigorosas no banco de dados.

### ISOLAMENTO

    Permite que várias transações ocorram simultaneamente sem interferir umas nas outras.

### DURABILIDADE

    Os dados DEVEM ser preservados mesmo após as operações terem sido concluídas.



## Constraints (Restrições):

### Chave Primária (PRIMARY KEY):
     
     É como o número de identificação de um livro. 

     É um campo ou conjunto de campos que identifica exclusivamente cada registro em uma tabela.
     
     Função: garantir a integridade dos dados e facilitar a pesquisa rápida.

### Chave Estrangeira (FOREIGN KEY):

     É como um link para outra estante.
    
     É um campo em uma tabela que se relaciona com a chave primária de outra tabela.

### NOT NULL:

    Garante que um campo não pode ficar vazio.

### UNIQUE:

    Garante que os valores em uma coluna sejam exclusivos,

### DEFAULT:

    Define um valor padrão para um campo se nenhum valor for especificado.

### CHECK:

    Permite definir condições para os valores que podem ser inseridos em um campo.

    CREATE TABLE Persons (
        ID int NOT NULL,
        LastName varchar(255) NOT NULL,
        FirstName varchar(255),
        Age int,
        CHECK (Age>=18)
    );

    ALTER TABLE Persons
        ADD CHECK (Age>=18);

    Para aplicar CHECK a várias colunas:

    CREATE TABLE Persons (
        ID int NOT NULL,
        LastName varchar(255) NOT NULL,
        FirstName varchar(255),
        Age int,
        City varchar(255),
        CONSTRAINT CHK_Person CHECK (Age >= 18 AND City = 'Sao Paulo')
    );

    ALTER TABLE Persons
        ADD CONSTRAINT CHK_PersonAge CHECK (Age>=18 AND City='Sandnes');

    CONSTRAINT é utilizado para nomear a restrição CHECK como "CHK_Person"

    Para eliminar restrição CHECK:

        ALTER TABLE Persons
            DROP CHECK CHK_PersonAge;

### CREATE_INDEX:

    Cria índices em campos específicos para acelerar a pesquisa.
