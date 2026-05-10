# 📖 Glossário — Banco de Dados

---

1 - **Banco de Dados:** Coleção organizada e estruturada de dados relacionados que representa algum aspecto do mundo real, armazenada e gerenciada eletronicamente.

2 - **SGBD (Sistema Gerenciador de Banco de Dados):** Software responsável por criar, manter, controlar o acesso e manipular bancos de dados. Exemplos: PostgreSQL, MySQL, Oracle, SQL Server.

3 - **Tabela (Relação):** Estrutura básica do modelo relacional, composta por linhas (tuplas/registros) e colunas (atributos/campos), que representa uma entidade ou relacionamento.

4 - **Chave Primária (Primary Key):** Atributo ou conjunto de atributos que identifica de forma única cada registro em uma tabela. Não pode ser nula nem repetida.

5 - **Chave Estrangeira (Foreign Key):** Atributo em uma tabela que referencia a chave primária de outra tabela, estabelecendo um relacionamento entre elas e garantindo integridade referencial.

6 - **SQL (Structured Query Language):** Linguagem padrão para definição, manipulação e consulta de dados em bancos relacionais. Divide-se em DDL, DML, DQL, DCL e TCL.

7 - **Normalização:** Processo de organizar as tabelas de um banco de dados para reduzir redundâncias e dependências indesejadas, aplicando as formas normais (1FN, 2FN, 3FN).

8 - **Transação:** Unidade lógica de trabalho que contém uma ou mais operações SQL, executadas de forma atômica — ou todas ocorrem (COMMIT) ou nenhuma ocorre (ROLLBACK).

9 - **JOIN:** Operação SQL que combina registros de duas ou mais tabelas com base em uma condição de relacionamento. Tipos: INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN.

10 - **Índice (Index):** Estrutura de dados auxiliar que acelera a recuperação de registros em uma tabela, similar ao índice de um livro. Melhora o desempenho de consultas, mas aumenta o custo de inserções e atualizações.

11 - **View (Visão):** Tabela virtual criada a partir de uma consulta SQL. Não armazena dados fisicamente, mas facilita o acesso a consultas complexas e adiciona uma camada de segurança.

12 - **ACID:** Conjunto de propriedades que garantem a confiabilidade de transações: Atomicidade, Consistência, Isolamento e Durabilidade.

13 - **NoSQL:** Categoria de bancos de dados que não utilizam o modelo relacional. Projetados para alta escalabilidade e flexibilidade com dados não estruturados ou semiestruturados.

14 - **Entidade:** No modelo ER, representa um objeto do mundo real com existência independente (ex: Cliente, Produto, Pedido).

15 - **Cardinalidade:** Define a quantidade de instâncias de uma entidade que podem se relacionar com instâncias de outra entidade (1:1, 1:N, N:M).
