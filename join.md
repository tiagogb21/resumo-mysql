# JOIN

    Operação que permite combinar registros de duas ou mais tabelas em uma única consulta.

    É utilizado quando temos informações distribuídas em várias tabelas e desejamos reunir essas informações em uma única consulta para análise ou apresentação.


* INNER JOIN --> tabela da esquerda precisa ter correspondente na direita (ida e volta)

* LEFT JOIN --> tabela da esquerda NÃO precisa ter correspondente na direita (SOMENTE id)

* RIGHT JOIN --> tabela da direita NÃO precisa ter correspondente na esquerda (SOMENTE volta)

## INNER JOIN:

    Retorna apenas os registros que têm correspondências em ambas as tabelas envolvidas na junção.
    
    Se não houver correspondência para um registro em uma das tabelas, esse registro não será incluído no resultado.

    Retorna todos os resultados SOMENTE se os da esquerda tiverem um correspondente na direita.

    Ex.: se quisermos saber quais são todos os produtos que possuem um fornecedor associado.
    
    Sintaxe:

        SELECT colunas
            FROM tabela1
            INNER JOIN tabela2 ON tabela1.coluna = tabela2.coluna;
    
    Ex.:

        SELECT orders.order_id, customers.customer_name
            FROM orders
            INNER JOIN customers ON orders.customer_id = customers.customer_id;

# LEFT JOIN (ou LEFT OUTER JOIN):

    Retorna todos os registros da tabela à esquerda (a primeira tabela mencionada) e os registros correspondentes da tabela à direita (a segunda tabela mencionada).
    
    Se não houver correspondência na tabela à direita, os campos da tabela à direita serão preenchidos com valores nulos.

    Retorna todos os resultados independente se ele bateu com algum resultado da direita.

    Ex.: se quisermos saber quais são todos os produtos, independente de um deles ter um fornecedor registrado ou não.
    
    Sintaxe:

        SELECT colunas
            FROM tabela1
            LEFT JOIN tabela2 ON tabela1.coluna = tabela2.coluna;
    
    Ex.:

        SELECT employees.employee_name, departments.department_name
            FROM employees
            LEFT JOIN departments ON employees.department_id = departments.department_id;

# RIGHT JOIN (ou RIGHT OUTER JOIN):

    Retorna todos os registros da tabela à direita (a segunda tabela mencionada) e os registros correspondentes da tabela à esquerda (a primeira tabela mencionada).
    
    Se não houver correspondência na tabela à esquerda, os campos da tabela à esquerda serão preenchidos com valores nulos.

    Retorna todos os resultados independente se ele bateu com algum resultado da esquerda.

    Ex.: se quisermos saber quais são todos os fornecedores, independente de um deles ter um produto registrado ou não.
    
    Sintaxe:

        SELECT colunas
            FROM tabela1
            RIGHT JOIN tabela2 ON tabela1.coluna = tabela2.coluna;
    
    Ex.:

        SELECT employees.employee_name, departments.department_name
            FROM employees
            RIGHT JOIN departments ON employees.department_id = departments.department_id;


# FULL JOIN (ou FULL OUTER JOIN):

    Retorna todos os registros de ambas as tabelas, independentemente de haver correspondências ou não.
     
    Se não houver correspondência em uma das tabelas, os campos dessa tabela serão preenchidos com valores nulos.

    Sintaxe:

        SELECT colunas
            FROM tabela1
            FULL JOIN tabela2 ON tabela1.coluna = tabela2.coluna;

    Ex.:

        SELECT students.student_name, enrollments.course_name
            FROM students
            FULL JOIN enrollments ON students.student_id = enrollments.student_id;


# CROSS JOIN:

    Combina cada linha da primeira tabela com cada linha da segunda tabela, criando um produto cartesiano.
    
    Obs.: Pode resultar em um grande número de registros, e normalmente usamos uma cláusula WHERE para filtrar os resultados, limitando o uso do CROSS JOIN.

    Sintaxe:

        SELECT colunas
            FROM tabela1
            CROSS JOIN tabela2;

    Ex.:

        SELECT products.product_name, categories.category_name
            FROM products
            CROSS JOIN categories;


# SELF JOIN:

    Quando uma tabela precisa ser combinada consigo mesma

    Um SELF JOIN é quando precisamos combinar registros dentro da mesma tabela.
    
    Fazemos isso atribuindo nomes de tabela diferentes para a mesma tabela e, em seguida, usando os nomes de tabela diferentes para estabelecer a relação.

    Sintaxe:

        SELECT e1.employee_name, e2.supervisor_name
            FROM employees e1
            LEFT JOIN employees e2 ON e1.supervisor_id = e2.employee_id;

