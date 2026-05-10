# 📝 Resumos — Banco de Dados

---

## 1. Fundamentos de Banco de Dados

Um **banco de dados** é uma coleção organizada de dados relacionados que representa algum aspecto do mundo real. Um **SGBD (Sistema Gerenciador de Banco de Dados)** é o software que gerencia o armazenamento, recuperação e segurança dos dados, como PostgreSQL, MySQL, Oracle e SQL Server. A diferença entre dados e informação é fundamental: dados são fatos brutos, enquanto informação é o resultado do processamento desses dados com significado e contexto.

A **arquitetura de três esquemas** separa o banco de dados em três níveis: o esquema externo (visão do usuário), o esquema conceitual (estrutura lógica global) e o esquema interno (armazenamento físico). Essa separação garante **independência de dados**, permitindo alterar um nível sem impactar os outros. Os principais modelos de dados são o hierárquico (dados em árvore), o relacional (tabelas e relacionamentos) e o orientado a objetos.

---

## 2. Modelagem de Dados

O **Modelo Entidade-Relacionamento (ER)** é uma técnica de modelagem conceitual que representa os dados por meio de **entidades** (objetos do mundo real), **atributos** (propriedades das entidades) e **relacionamentos** (associações entre entidades). A cardinalidade define quantas instâncias de uma entidade se associam com outra: **1:1** (um para um), **1:N** (um para muitos) e **N:M** (muitos para muitos).

A **normalização** é o processo de organizar as tabelas para reduzir redundância e dependências indesejadas. A **1ª Forma Normal (1FN)** elimina grupos repetitivos e garante atomicidade dos atributos. A **2FN** elimina dependências parciais da chave primária. A **3FN** elimina dependências transitivas, garantindo que todos os atributos não-chave dependam exclusivamente da chave primária.

---

## 3. SQL — Structured Query Language

SQL é a linguagem padrão para comunicação com bancos de dados relacionais, dividida em subconjuntos por função. O **DDL** (Data Definition Language) cria e altera estruturas: `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`. O **DML** (Data Manipulation Language) manipula os dados: `INSERT INTO`, `UPDATE ... SET`, `DELETE FROM`. O **DQL** realiza consultas com `SELECT`, podendo filtrar com `WHERE`, ordenar com `ORDER BY`, agrupar com `GROUP BY` e filtrar grupos com `HAVING`.

Os **JOINs** são usados para combinar dados de múltiplas tabelas. O `INNER JOIN` retorna apenas registros que têm correspondência em ambas as tabelas. O `LEFT JOIN` retorna todos os registros da tabela esquerda e os correspondentes da direita. O `RIGHT JOIN` faz o inverso. O `FULL JOIN` retorna todos os registros de ambas as tabelas, com `NULL` onde não há correspondência.

---

## 4. Transações e Controle de Concorrência

Uma **transação** é uma unidade lógica de trabalho composta por uma ou mais operações que devem ser executadas completamente ou não executadas. As propriedades **ACID** garantem a confiabilidade: **Atomicidade** (tudo ou nada), **Consistência** (o banco sempre vai de um estado válido para outro), **Isolamento** (transações concorrentes não interferem entre si) e **Durabilidade** (dados persistem após commit).

O controle de concorrência evita problemas como leitura suja, leitura não-repetível e leituras fantasmas. Os **bloqueios (locks)** são o mecanismo mais comum, podendo ser compartilhados (leitura) ou exclusivos (escrita). Um **deadlock** ocorre quando duas transações ficam esperando indefinidamente pela liberação de recursos uma da outra, sendo resolvido pelo SGBD abortando uma das transações.

---

## 5. Banco de Dados NoSQL

O **NoSQL** (Not Only SQL) surgiu para superar as limitações do modelo relacional em cenários de alta escalabilidade e grandes volumes de dados não estruturados. Os principais tipos são: **chave-valor** (Redis — alta performance para cache), **documentos** (MongoDB — armazena JSONs flexíveis), **colunar** (Cassandra — grandes volumes de escrita distribuída) e **grafos** (Neo4j — modelagem de relacionamentos complexos).

Enquanto bancos relacionais seguem ACID, sistemas NoSQL frequentemente adotam o modelo **BASE** (Basically Available, Soft state, Eventually consistent), priorizando disponibilidade e tolerância a partições sobre consistência imediata. A escolha entre SQL e NoSQL depende das necessidades do sistema: estrutura rígida x flexibilidade, consistência forte x escalabilidade horizontal.
