# 📋 Prompts Testados — Banco de Dados

Coleção de prompts testados com suas respectivas respostas geradas por IA, organizados para referência e estudo.

🔗 **NotebookLM:** [https://notebooklm.google.com/notebook/75dc71aa-6168-446e-97fe-006809f324cf?authuser=1](https://notebooklm.google.com/notebook/75dc71aa-6168-446e-97fe-006809f324cf?authuser=1)

---

## Prompt 1 — Comandos SQL Fundamentais

### 🔹 Pergunta

> Como funcionam os comandos DDL, DML e DQL em SQL? Crie uma tabela resumo.

### 🔹 Resposta

O SQL é dividido em sublinguagens, cada uma com um propósito específico. O **DDL (Data Definition Language)** é responsável por **definir e alterar a estrutura** do banco de dados. Seus comandos principais são `CREATE` (criar tabelas, índices, views), `ALTER` (modificar estruturas existentes) e `DROP` (remover estruturas permanentemente). As alterações DDL geralmente têm efeito imediato e não podem ser desfeitas com `ROLLBACK` em muitos SGBDs.

O **DML (Data Manipulation Language)** lida com a **manipulação dos dados** dentro das estruturas já criadas. Os comandos são `INSERT INTO` (inserir novos registros), `UPDATE ... SET` (atualizar registros existentes) e `DELETE FROM` (remover registros). Operações DML fazem parte de transações e podem ser desfeitas com `ROLLBACK` antes do `COMMIT`.

O **DQL (Data Query Language)**, composto principalmente pelo comando `SELECT`, é usado para **consultar e recuperar dados**. Pode ser combinado com cláusulas poderosas: `WHERE` filtra registros, `JOIN` combina tabelas, `GROUP BY` agrupa resultados, `HAVING` filtra grupos e `ORDER BY` ordena o resultado final.

### Tabela Resumo das Sublinguagens SQL

| Sublinguagem | Sigla | Comandos Principais | Propósito |
| :--- | :---: | :--- | :--- |
| Data Definition Language | **DDL** | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` | Define e altera estruturas do banco |
| Data Manipulation Language | **DML** | `INSERT`, `UPDATE`, `DELETE` | Manipula os dados nas tabelas |
| Data Query Language | **DQL** | `SELECT` | Consulta e recupera dados |
| Data Control Language | **DCL** | `GRANT`, `REVOKE` | Controla permissões de acesso |
| Transaction Control Language | **TCL** | `COMMIT`, `ROLLBACK`, `SAVEPOINT` | Gerencia transações |

---

## Prompt 2 — JOINs em SQL

### 🔹 Pergunta

> Explique os tipos de JOIN em SQL com exemplos práticos.

### 🔹 Resposta

Os **JOINs** são operações que combinam registros de duas ou mais tabelas com base em uma condição de relacionamento. Eles são essenciais para trabalhar com bancos de dados normalizados, onde os dados são distribuídos em múltiplas tabelas relacionadas.

O **`INNER JOIN`** é o tipo mais comum: retorna apenas os registros que possuem correspondência em **ambas as tabelas**. Se um registro de uma tabela não tem par na outra, ele é excluído do resultado. O **`LEFT JOIN`** (ou `LEFT OUTER JOIN`) retorna **todos os registros da tabela esquerda** e os registros correspondentes da tabela direita; onde não há correspondência, os campos da direita recebem `NULL`.

```sql
-- Exemplo: listar todos os clientes e seus pedidos (incluindo clientes sem pedidos)
SELECT 
    c.nome AS cliente,
    p.id AS pedido_id,
    p.total
FROM clientes c
LEFT JOIN pedidos p ON c.id = p.cliente_id
ORDER BY c.nome;
```

O **`RIGHT JOIN`** faz o oposto do `LEFT JOIN`: retorna todos os registros da tabela direita. Já o **`FULL JOIN`** (ou `FULL OUTER JOIN`) retorna **todos os registros de ambas as tabelas**, com `NULL` onde não há correspondência em nenhum dos lados.

---

## Prompt 3 — Normalização de Banco de Dados

### 🔹 Pergunta

> O que é normalização e quais são as três primeiras formas normais? Mostre um exemplo prático.

### 🔹 Resposta

A **normalização** é o processo de organizar as tabelas de um banco de dados relacional para eliminar redundâncias e dependências indesejadas, garantindo integridade dos dados e facilitando a manutenção. Ela é feita aplicando-se progressivamente as **formas normais**, cada uma resolvendo um tipo específico de problema.

A **1ª Forma Normal (1FN)** exige que todos os atributos de uma tabela sejam **atômicos** (indivisíveis) e que não existam grupos repetitivos. Uma tabela que armazena múltiplos telefones em uma única coluna como `"(62)9999-0000, (62)8888-1111"` viola a 1FN — a solução é criar uma tabela separada para telefones.

A **2FN** exige que a tabela já esteja na 1FN e que todos os atributos não-chave dependam **completamente** da chave primária (sem dependências parciais). Isso é relevante em tabelas com chave primária composta. A **3FN** exige que a tabela esteja na 2FN e que não existam **dependências transitivas** — um atributo não-chave não pode depender de outro atributo não-chave.

```sql
-- Exemplo de tabela não normalizada (viola 2FN e 3FN)
-- pedido_id | produto_id | produto_nome | categoria | cliente_nome | cliente_cidade

-- Após normalização:
CREATE TABLE produtos (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    categoria VARCHAR(50)
);

CREATE TABLE clientes (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    cidade VARCHAR(50)
);

CREATE TABLE pedidos (
    id SERIAL PRIMARY KEY,
    cliente_id INT REFERENCES clientes(id),
    produto_id INT REFERENCES produtos(id),
    quantidade INT,
    data_pedido DATE
);
```
