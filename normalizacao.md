# Normalização

    Técnica no projeto de banco de dados que visa organizar tabelas relacionadas com o objetivo de reduzir a redundância de dados e manter a integridade destes.

    Ajuda a garantir que os sistemas de gerenciamento de banco de dados (SGBD) funcionem de maneira eficiente, economizando espaço de armazenamento e minimizando a chance de inconsistências nos dados.

## OBJETIVOS:

    1 - Eliminar Redundância
    
            Não ter dados repetidos

            Evitar a duplicação desnecessária de dados em tabelas.
            
            Objetivo:
                
                * economizar no espaço de armazenamento
                
                * garantir que as informações sejam atualizadas de forma consistente.

    2 - Minimizar Anomalias
    
            Reduzir a probabilidade de anomalias de dados, como inserções, atualizações ou exclusões incorretas, que podem ocorrer devido à duplicação de informações.

    3 - Manter a Integridade
    
            Garantir que os dados sejam precisos, confiáveis e estejam sempre em um estado consistente.


## Como fazer?

    * Separar os dados relacionados em tabelas diferentes.
    
    Obs.: Quanto menos redundância houver, menor será a probabilidade de erros nos dados.


## Benefícios

    Separação de dados relacionados em suas próprias tabelas (maior organização e clareza)

    Integridade dos dados (dados precisos, consistentes e confiáveis.)

    Economia de espaço

    Manutenção Simplificada


## Formas Normais

    A normalização é dividida em várias formas normais, cada uma com regras específicas para organizar as tabelas.
    
    As formas normais mais comuns incluem:

    Primeira Forma Normal (1NF)

        Colunas devem possuir valores atômicos, um único valor indivisível;

        Valores em uma coluna devem ser do mesmo tipo;

        Cada coluna deve possuir um nome exclusivo;

        A ordem dos dados registrados em uma tabela não deve afetar a integridade dos dados.

    Segunda Forma Normal (2NF)
        
        As tabelas devem estar na 1NF

        A tabela não deve possuir dependências parciais, ou seja, todos os atributos não chave devem depender completamente da chave primária.

        Devemos fazer a pergunta:

            É possível mover os valores de uma coluna para uma outra tabela exclusiva?

    Terceira Forma Normal (3NF)
    
        As tabelas devem estar na 1NF e na 2NF
        
        As tabelas não podem conter dependências transitivas, ou seja, uma coluna não chave não deve depender de outra coluna não chave.

        A tabela não deve conter atributos (colunas) que não sejam dependentes exclusivamente da PK (chave primária).

        Devemos fazer a pergunta:

            O atributo (coluna) é dependente de outra coluna que não seja PK ou que não seja dependente unicamente da PK?

    Forma Normal de Boyce-Codd (BCNF)
        
        Semelhante à 3NF, mas com regras mais rigorosas para garantir que cada dependência funcional seja uma dependência de chave.

    Quarta Forma Normal (4NF)
        
        Lida com dependências multivaloradas
        
            * um atributo não chave pode ter múltiplos valores associados a ele para uma única chave.

    Quinta Forma Normal (5NF)
    
        Lida com dependências de junção
            
            * surgem quando informações que poderiam estar em uma única tabela são divididas em várias tabelas.

    Forma Normal de Domínio/Elementar (DKNF)
        
        A forma mais rigorosa que trata todas as dependências possíveis, mas é raramente usada em prática devido à sua complexidade.


## Limitações da Normalização

    Complexidade de Consultas
    
        Pode exigir junções complexas em consultas, o que pode afetar o desempenho em bancos de dados muito grandes.

    Desnormalização Ocasional
    
        Em alguns casos, desnormalizar parte do banco de dados pode ser necessário para otimizar consultas específicas.

