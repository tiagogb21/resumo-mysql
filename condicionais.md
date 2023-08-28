## IF:

    Realiza uma ação com base em uma condição especificada.

    SELECT order_id, delivery_date,
        IF(delivery_date < CURDATE(), 'Atrasado', 'No Prazo') AS status
    FROM orders;

    Para verificar se a pessoa é menor de idade:

    SELECT IF(idade >= 18, 'Maior de idade', 'Menor de Idade') FROM pessoas;

    Para determinar os 10 primeiros clientes que estão ativos:

    SELECT first_name, IF(active, 'Cliente Ativo', 'Cliente Inativo') AS status
        FROM customer LIMIT 10;


## CASE:

    Realiza diferentes ações com base em diferentes condições. 

    SELECT employee_id, first_name, last_name, salary,
        CASE
            WHEN salary < 30000 THEN 'Baixa Faixa Salarial'
            WHEN salary >= 30000 AND salary < 60000 THEN 'Média Faixa Salarial'
            ELSE 'Alta Faixa Salarial'
        END AS faixa_salarial
    FROM employees;


## COALESCE:

    Retorna o primeiro valor não nulo em uma lista de expressões.

    Pode ser usado para fornecer um valor padrão quando um campo é nulo.

        SELECT product_name, COALESCE(sale_price, regular_price) AS price FROM products;


## NULLIF:

    É usada para comparar duas expressões e retorna NULL caso sejam iguais.

    Pode ser usado para tratar casos em que desejamos retornar NULL em vez de um valor específico.

        SELECT employee_id, NULLIF(salary, 0) AS adjusted_salary FROM employees;

