## CHARACTER_LENGTH ou CHAR_LENGTH:

    Retorna o comprimento (número de caracteres) de uma string.

    SELECT CHAR_LENGTH('Hello, World!');


## CONCAT:

    Combina duas ou mais expressões (strings) em uma única string.


## FIELD:

	Retorna a posição de um índice de um valor em uma lista de valores

    ex.: Para selecionar todos os funcionários da tabela employees e classificar com base no departamento. 

    SELECT * FROM employees
        ORDER BY FIELD(department, 'HR', 'Finance', 'IT', 'Sales');


## INSTR:

    Retorna a posição da primeira ocorrência de uma string em outra string


## LCASE ou LOWER:

    Converte uma string para letras minúsculas.

    SELECT LCASE('Hello, world!');


## UCASE ou UPPER:

    Converte uma string para letras maiúsculas.

    SELECT UCASE('Hello, world!');


## LEFT:

    Extrai um número específico de caracteres de uma string (começando pela esquerda)

    SELECT LEFT('Hello, World!', 5);


## RIGHT:

    Extrai um número específico de caracteres de uma string (começando pela direita)

    SELECT RIGHT('Hello, World!', 6);


## SUBSTRING:

    Extrai uma certa quantidade de caracteres a partir de uma posição definida:

    I - Se a quantidade de caracteres a extrair não for definida, então a string será extraída do índice inicial definido, até o seu final

        SELECT SUBSTRING('Hello, World!', 5);

    II - Extrai parte de uma string de acordo com o índice de um caractere inicial e a quantidade de caracteres a extrair

        SELECT SUBSTRING('Hello, World!', 5, 2);


# LTRIM:

    Remove espaços em branco iniciais de uma string


# RTRIM:

    Remove espaços em branco finais de uma string


# MID:

    Extrai uma substring de uma string, começando em uma posição específica.


# POSITION:

    sintaxe: POSITION(substring IN string)

    Retorna a posição da primeira ocorrência de uma substring em uma string.

    SELECT 
        address,
        POSITION("90210" IN LOWER(address)) AS cep_position
    FROM addresses;


# REPEAT:

    Repete uma string quantas vezes for especificado


# REVERSE:

    Inverte uma string e retorna o resultado


# REPLACE:

    Substitui as ocorrências de uma substring em uma string

    SELECT REPLACE('Oi, eu sou uma string', 'string', 'cadeia de caracteres');

