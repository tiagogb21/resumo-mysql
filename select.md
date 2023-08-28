# SELECT

É usado para recuperar dados de uma ou mais tabelas em um banco de dados.

Ex.:

    Para recuperar todos os dados de uma tabela:
        SELECT * FROM 'nome_da_tabela';

    Para recuperar dados específicos de uma tabela:
        SELECT coluna1, coluna2 FROM 'nome_da_tabela';

    Para filtrar os dados com base em uma condição específica
        SELECT coluna1, coluna2 FROM tabela WHERE condição;

## OPERADORES:

=   IGUAL
>   MAIOR QUE
<   MENOR QUE
>=  MAIOR QUE OU IGUAL
<=  MENOR QUE OU IGUAL
<>  DIFERENTE DE
AND OPERADOR LÓGICO E
OR  OPERADOR LÓGICO OU
NOT NEGAÇÃO
IS  COMPARA COM VALORES BOOLEANOS (TRUE, FALSE, NULL)

ordem: () --> * ou / --> + ou - --> NOT --> AND --> OR

## CONCAT

Permite combinar colunas e literais de texto.

    SELECT CONCAT(info1, ..., infoN) FROM table_name;

## DISTINCT

Permite recuperar valores únicos de uma coluna ou conjunto de colunas em uma consulta.

    SELECT DISTINCT column1, ..., columnN FROM table_name;

obs.: Quando utilizamos mais de uma coluna na query, irá retorna apenas as combinações únicas da "columnX" e da "columnY" juntas. Se houver duas linhas com o mesmo "columnX" e o mesmo "columnY", apenas uma delas será retornada, pois a combinação completa é considerada repetida.

## COUNT

Permite contar o número de linhas ou valores em uma coluna de uma tabela.

SELECT COUNT(*) FROM 'nome_da_tabela'

ainda:

SELECT COUNT(DISTINCT *) FROM 'nome_da_tabela'

se quisermos agrupar por quantidade de resultados:

SELECT column_name, COUNT(*) as result FROM 'nome_da_tabela' GROUP BY column_name;

## SUM

É usada para calcular a soma dos valores em uma coluna numérica.

SELECT SUM(*) as result FROM 'nome_da_tabela';

## DIV

    Retorna o resultado inteiro de uma divisão, ignorando as casas decimais de um número.

    SELECT 10 DIV 3; -- 3

## MOD

    Retorna o resto de uma divisão

    SELECT 10 DIV 3; -- 1

## ROUND

    Arredonda os números de acordo com sua parte decimal.

    SELECT ROUND(10.1234); -- 10

## CEIL

    Arredondamento sempre para cima:

        SELECT CEIL(10.12); -- 10

## FLOOR

    Arredondamento sempre para baixo:

        SELECT FLOOR(10.89);

## AVG

É usada para calcular a média dos valores em uma coluna numérica.

SELECT AVG(*) as result FROM 'nome_da_tabela';

## MAX

É usada para encontrar o valor máximo em uma coluna.

SELECT MAX(*) as result FROM 'nome_da_tabela';

## MIN

É usada para encontrar o valor mínimo em uma coluna.

SELECT MIN(*) as result FROM 'nome_da_tabela';

## POW

    Permite elevando um número X à potência Y

        SELECT POW(X, Y);

        SELECT POW(2, 2); --4

## SQRT

    Permite encontrar a raiz quadrada de um valor

        SELECT POW(X);

        SELECT POW(4); --2

## RAND

    Permite gerar valores aleatórios entre 0 e 1

        SELECT RAND();
    
    Para gerar um valor entre 0 e 10:

        SELECT ROUND(RAND() * 10);

## GROUP BY

    É usada para agrupar linhas de uma tabela com base em valores de uma ou mais colunas.
    Permite realizar cálculos em grupos de dados em vez de em toda a tabela.

    funcao_de_agregacao --> SUM, AVG, MAX ou MIN

    sintaxe:

    SELECT coluna1, coluna2, funcao_de_agregacao(coluna_numerica)
        FROM tabela
        GROUP BY coluna1, coluna2
        HAVING condicao;

    I - Agrupamento por Coluna ou Colunas: Devemos especificar uma ou mais colunas pelas quais desejamos agrupar os dados da tabela.
    
     Todas as linhas com o mesmo valor ou combinação de valores nessas colunas serão agrupadas juntas.

    II - Aplicação de Funções de Agregação: Após agrupar os dados, podemos aplicar funções de agregação às colunas numéricas do grupo para calcular estatísticas, como soma, média, máximo ou mínimo.

    III - Filtragem com HAVING: Pode adicionar uma cláusula HAVING para filtrar os grupos com base em uma condição. Isso é semelhante a usar a cláusula WHERE, mas é aplicado aos grupos, não às linhas individuais.


## HAVING

    Permite filtrar os resultados de uma consulta agregada com base em uma condição

    É usado para restringir grupos resultantes com base em critérios de agregação.

    SELECT produto_id, SUM(valor_venda) AS total_vendas
        FROM vendas
        GROUP BY produto_id
        HAVING SUM(valor_venda) > 1000;


## LIMIT

Permite especificar a quantidade de resultados

SELECT column FROM 'nome_da_tabela' LIMIT X;

## OFFSET

Permite pular uma certa quantidade de linhas

SELECT column FROM 'nome_da_tabela' LIMIT X OFFSET Y;

## ORDER BY

SELECT column1, ..., columnN FROM 'nome_da_tabela' ORDER BY column1 ASC, column2 DESC;

## WHERE

SELECT column1, ..., columnN FROM 'nome_da_tabela' WHERE x = y;

SELECT column1, ..., columnN FROM 'nome_da_tabela' WHERE (a = b OR a = c) AND x = y;

Para filtrar por valores não nulos:

    SELECT column1, ..., columnN FROM 'nome_da_tabela' WHERE x IS NOT NULL;


## EXISTS

É usada para verificar a existência de registros em uma subconsulta.

É frequentemente usada em conjunto com uma consulta principal para determinar se pelo menos um registro atende a uma condição específica em uma tabela ou subconjunto de dados.

SELECT colunas
    FROM tabela_principal
    WHERE EXISTS (subconsulta);

    obs.: Retorna verdadeiro (TRUE) se a subconsulta retornar pelo menos um registro e falso (FALSE) se a subconsulta não retornar nenhum registro.

    ex.: Suponha que temos uma tabela chamada "pedidos" e outra tabela chamada "itens_do_pedido". Queremos encontrar todos os pedidos que possuem pelo menos um item com um preço acima de $100:

        SELECT numero_do_pedido, data_do_pedido
        FROM pedidos p
        WHERE EXISTS (
            SELECT 1
            FROM itens_do_pedido i
            WHERE i.numero_do_pedido = p.numero_do_pedido
            AND i.preco > 100
        );


## ANY

Compara um valor com todos os valores retornados pela subconsulta e retorna verdadeiro (TRUE) se a condição especificada for verdadeira para pelo menos um dos valores. 

    ex.: desejamos encontrar todos os produtos que tenham um preço maior do que o preço mais alto em uma determinada categoria

    SELECT nome_do_produto
    FROM produtos
    WHERE preço > ANY (
        SELECT preço
        FROM produtos
        WHERE categoria = 'Eletrônicos'
    );

## ALL

Compara um valor com todos os valores retornados pela subconsulta e retorna verdadeiro (TRUE) somente se a condição especificada for verdadeira para todos os valores.

    ex.: desejamos encontrar todos os produtos que tenham um preço maior do que o preço mais alto em todas as categorias

    SELECT nome_do_produto
    FROM produtos
    WHERE preço > ALL (
        SELECT preço
        FROM produtos
    );

## LIKE

Permite buscar por meio de uma sequência específica de caracteres.

    Curingas:

        % (percentual) --> zero, um ou múltiplos caracteres
        _ (underscore) --> um único carácter

Sabemos quantos caracteres possui?

    Não --> %
    Sim --> _


Se quisermos saber, porém não sabemos quantos caracteres possui:

    1 - como começa:
    
    SELECT column1, ..., columnN FROM 'nome_da_tabela' WHERE column LIKE '%XYZ';

    2 - como termina:

    SELECT column1, ..., columnN FROM 'nome_da_tabela' WHERE column LIKE 'XYZ%';

    3 - intermediário:

    SELECT column1, ..., columnN FROM 'nome_da_tabela' WHERE column LIKE '%XYZ%';

Se quisermos saber, e sabemos quantos caracteres possui:

    1 - começa com N caracteres:

    SELECT column1, ..., columnN FROM 'nome_da_tabela' WHERE column LIKE '___XYZ';

    2 - termina com N caracteres:

    SELECT column1, ..., columnN FROM 'nome_da_tabela' WHERE column LIKE 'XYZ___';

    3 - começa com M caracteres e termina com N caracteres:

    SELECT column1, ..., columnN FROM 'nome_da_tabela' WHERE column LIKE '___XYZ___';

Obs.: podemos juntar ambos os caracteres especiais.

## IN

É usado para filtrar resultados onde o valor de uma coluna está em uma lista específica de valores.

Ao invés de escrevermos:

SELECT column FROM 'nome_da_tabela'
    WHERE column1 = A
    OR column1 = B
    OR column1 = C
    OR column1 = D;

Podemos escrever:

SELECT column FROM 'nome_da_tabela' WHERE column1 IN (A, B, C, D);

sintaxe:

    SELECT * FROM 'nome_da_tabela'
        WHERE coluna IN (valor1, valor2, valor3, valor4, ..., valorN);

    ou

    SELECT * FROM 'nome_da_tabela'
        WHERE coluna IN (expressão);


## BETWEEN (ENTRE)

É usado para filtrar resultados onde o valor de uma coluna está dentro de um intervalo específico.

sintaxe:

    SELECT * FROM 'nome_da_tabela'
        WHERE coluna BETWEEN valor1 AND valor2;
    
    SELECT * FROM 'nome_da_tabela'
        WHERE coluna NOT BETWEEN valor1 AND valor2;


## TEMPO

Para um determinado tempo:

    DATE
        SELECT DATE(column) FROM 'nome_da_tabela'; -- YYYY-MM-DD

    YEAR
        SELECT YEAR(column) FROM 'nome_da_tabela'; -- Ano

    MONTH
        SELECT MONTH(column) FROM 'nome_da_tabela'; -- Mês

    DAY
        SELECT DAY(column) FROM 'nome_da_tabela'; -- Dia

    HOUR
        SELECT HOUR(column) FROM 'nome_da_tabela'; -- Hora

    MINUTE
        SELECT MINUTE(column) FROM 'nome_da_tabela'; -- Minuto

    SECOND
        SELECT SECOND(column) FROM 'nome_da_tabela';


    Obs.: Diferença entre CURRENT_DATE() e NOW()

        SELECT CURRENT_DATE(); -- YYYY-MM-DD
        SELECT NOW(); -- YYYY-MM-DD HH:MM:SS
    
    Para retornar o ano atual:

        SELECT YEAR(CURRENT_DATE()); OU SELECT YEAR(NOW());
    
    Para retornar a hora atual:

        SELECT HOUR(NOW());
    

    Para calcular a diferença em dias entre duas datas:

        SELECT DATEDIFF('2023-04-30', '2022-03-04');
    
    Para calcular a diferença em horas:

        SELECT TIMEDIFF('23:30:10', '00:30:10');


ano-mês-dia horas:minutos:segundos

    SELECT * FROM 'nome_da_tabela'
        WHERE DATE(column) = 'yyyy-mm-dd';

usando BETWEEN

    SELECT *
        FROM 'nome_da_tabela'
        WHERE column BETWEEN 'yyyy-mm-dd hh' AND 'yyyy-mm-dd hh';

obs.: Para valores aproximados

    Encontra todos os pagamentos deste dia, ignorando horas, minutos e segundos

        SELECT * FROM 'nome_da_tabela'
            WHERE column LIKE 'yyyy-mm-dd%';


## UNION

É usada para combinar o resultado de duas ou mais consultas em uma única lista de resultados.

     Atenção! Para que a operação de união funcione as consultas devem ter a mesma estrutura de colunas (mesmo número de colunas e tipos de dados correspondentes)

    
    SELECT coluna1, coluna2, ...
        FROM tabela1
    UNION
        SELECT coluna1, coluna2, ...
        FROM tabela2;

    Obs.: por padrão, o UNION remove automaticamente duplicatas dos resultados. Se você desejar incluir duplicatas, pode usar UNION ALL em vez de UNION.


    Ex.: queremos combinar as vendas de 2022 e 2023 em uma única lista:

        SELECT mês, produto, valor
            FROM vendas_2022
        UNION
            SELECT mês, produto, valor
            FROM vendas_2023;
    
    ATENÇÃO! o UNION remove automaticamente duplicatas, enquanto o UNION ALL não o faz.


## IMPORTANTE

    Para saber se uma coluna possui FK e qual a relação entre as tabelas:

        SELECT table_name, column_name, referenced_table_name
            FROM information_schema.key_column_usage
            WHERE referenced_table_name IS NOT NULL
            AND table_schema = 'nome_do_banco';
