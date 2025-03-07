Tags: #Faculdade #Matemática #Concurso 
___
## Estrutura Básica do SQL
A **linguagem SQL (Structured Query Language)** é a linguagem padrão para gerenciar e manipular bancos de dados relacionais. Ela é usada para criar, consultar, atualizar e excluir dados em um banco de dados. A estrutura básica do SQL é composta por **comandos** e **cláusulas** que permitem realizar operações específicas. Vamos explorar a estrutura básica do SQL de forma simples e didática.
O SQL é dividido em várias categorias, mas as mais comuns incluem:

1. **DDL (Data Definition Language)**: Comandos para definir e modificar a estrutura do banco de dados.

   - **CREATE**: Cria novas tabelas ou bancos de dados.

   - **ALTER**: Modifica a estrutura de tabelas existentes.

   - **DROP**: Remove tabelas ou bancos de dados.

2. **DML (Data Manipulation Language)**: Comandos para manipular os dados dentro das tabelas.

   - **INSERT**: Insere novos dados.

   - **UPDATE**: Atualiza dados existentes.

   - **DELETE**: Remove dados.

3. **DCL (Data Control Language)**: Comandos para controlar o acesso aos dados.

   - **GRANT**: Concede permissões a usuários.

   - **REVOKE**: Retira permissões.

4. **DTL (Data Transaction Language)**: 

    - **BEGIN TRANSACTION/WORK**: define uma transação no banco de dados.

   - **COMMIT**: salva a transação no banco de dados.

   - **ROLLBACK**: restaura o banco de dados para o último estado antes de um _commit_.

4. **DQL (Data Query Language)**: 

    - **SELECT**: permite a consulta a um banco de dados.
## Comandos Básicos SQL
A **linguagem SQL (Structured Query Language)** é a linguagem padrão para gerenciar e manipular bancos de dados relacionais. Ela é usada para criar, consultar, atualizar e excluir dados em um banco de dados. A estrutura básica do SQL é composta por **comandos** e **cláusulas** que permitem realizar operações específicas. Vamos explorar a estrutura básica do SQL de forma simples e didática.

---

### **Estrutura Básica do SQL**
O SQL é dividido em **subconjuntos** de comandos, cada um com um propósito específico. Os principais são:

1. **DDL (Data Definition Language):**  
   - Comandos para definir a estrutura do banco de dados (ex: criar tabelas, alterar estruturas).
   - Exemplos: `CREATE`, `ALTER`, `DROP`.

2. **DML (Data Manipulation Language):**  
   - Comandos para manipular os dados armazenados (ex: inserir, consultar, atualizar, excluir).
   - Exemplos: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.

3. **DCL (Data Control Language):**  
   - Comandos para controlar o acesso aos dados (ex: permissões de usuários).
   - Exemplos: `GRANT`, `REVOKE`.

4. **TCL (Transaction Control Language):**  
   - Comandos para gerenciar transações no banco de dados (ex: confirmar ou desfazer operações).
   - Exemplos: `COMMIT`, `ROLLBACK`.

---

### **Comandos Básicos do SQL**
Aqui estão os comandos mais comuns e sua estrutura básica:

#### **1. CREATE (DDL)**
- **Função:** Cria uma nova tabela, banco de dados ou outro objeto no banco de dados.
- **Sintaxe:**
  ```sql
  CREATE TABLE nome_tabela (
      coluna1 tipo_dado [restrições],
      coluna2 tipo_dado [restrições],
      ...
  );
  ```
- **Exemplo:**
  ```sql
  CREATE TABLE Cliente (
      ID INT PRIMARY KEY,
      Nome VARCHAR(50) NOT NULL,
      Email VARCHAR(100) UNIQUE
  );
  ```

#### **2. SELECT (DML)**
- **Função:** Consulta dados de uma ou mais tabelas.
- **Sintaxe:**
  ```sql
  SELECT coluna1, coluna2, ...
  FROM nome_tabela
  [WHERE condição]
  [ORDER BY coluna [ASC|DESC]];
  ```
- **Exemplo:**
  ```sql
  SELECT Nome, Email
  FROM Cliente
  WHERE Cidade = 'São Paulo'
  ORDER BY Nome ASC;
  ```

#### **3. INSERT (DML)**
- **Função:** Insere novos registros em uma tabela.
- **Sintaxe:**
  ```sql
  INSERT INTO nome_tabela (coluna1, coluna2, ...)
  VALUES (valor1, valor2, ...);
  ```
- **Exemplo:**
  ```sql
  INSERT INTO Cliente (ID, Nome, Email)
  VALUES (1, 'João Silva', 'joao.silva@email.com');
  ```

#### **4. UPDATE (DML)**
- **Função:** Atualiza registros existentes em uma tabela.
- **Sintaxe:**
  ```sql
  UPDATE nome_tabela
  SET coluna1 = valor1, coluna2 = valor2, ...
  [WHERE condição];
  ```
- **Exemplo:**
  ```sql
  UPDATE Cliente
  SET Email = 'joao.novo@email.com'
  WHERE ID = 1;
  ```

#### **5. DELETE (DML)**
- **Função:** Exclui registros de uma tabela.
- **Sintaxe:**
  ```sql
  DELETE FROM nome_tabela
  [WHERE condição];
  ```
- **Exemplo:**
  ```sql
  DELETE FROM Cliente
  WHERE ID = 1;
  ```

#### **6. ALTER (DDL)**
- **Função:** Modifica a estrutura de uma tabela (ex: adicionar, modificar ou excluir colunas).
- **Sintaxe:**
  ```sql
  ALTER TABLE nome_tabela
  ADD coluna_nova tipo_dado;

  ALTER TABLE nome_tabela
  MODIFY coluna_existente novo_tipo_dado;

  ALTER TABLE nome_tabela
  DROP COLUMN coluna;
  ```
- **Exemplo:**
  ```sql
  ALTER TABLE Cliente
  ADD Telefone VARCHAR(15);
  ```

#### **7. DROP (DDL)**
- **Função:** Exclui uma tabela ou outro objeto do banco de dados.
- **Sintaxe:**
  ```sql
  DROP TABLE nome_tabela;
  ```
- **Exemplo:**
  ```sql
  DROP TABLE Cliente;
  ```

---

### **Cláusulas Comuns do SQL**
Além dos comandos, o SQL usa **cláusulas** para refinar as operações. Aqui estão as principais:

1. **WHERE:**  
   - Filtra os registros com base em uma condição.
   - Exemplo:
     ```sql
     SELECT * FROM Cliente
     WHERE Cidade = 'Rio de Janeiro';
     ```

2. **ORDER BY:**  
   - Ordena os resultados de uma consulta.
   - Exemplo:
     ```sql
     SELECT * FROM Cliente
     ORDER BY Nome ASC;
     ```

3. **GROUP BY:**  
   - Agrupa os resultados com base em uma ou mais colunas.
   - Exemplo:
     ```sql
     SELECT Cidade, COUNT(*) AS Total
     FROM Cliente
     GROUP BY Cidade;
     ```

4. **HAVING:**  
   - Filtra grupos resultantes de uma cláusula `GROUP BY`.
   - Exemplo:
     ```sql
     SELECT Cidade, COUNT(*) AS Total
     FROM Cliente
     GROUP BY Cidade
     HAVING COUNT(*) > 10;
     ```

5. **JOIN:**  
   - Combina dados de duas ou mais tabelas com base em uma condição.
   - Exemplo:
     ```sql
     SELECT Cliente.Nome, Pedido.Valor
     FROM Cliente
     INNER JOIN Pedido ON Cliente.ID = Pedido.Cliente_ID;
     ```

---

### **Exemplo Completo**
Aqui está um exemplo que combina vários comandos e cláusulas:

```sql
-- Criação da tabela Cliente
CREATE TABLE Cliente (
    ID INT PRIMARY KEY,
    Nome VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    Cidade VARCHAR(50)
);

-- Inserção de dados
INSERT INTO Cliente (ID, Nome, Email, Cidade)
VALUES (1, 'João Silva', 'joao.silva@email.com', 'São Paulo');

INSERT INTO Cliente (ID, Nome, Email, Cidade)
VALUES (2, 'Maria Oliveira', 'maria.oliveira@email.com', 'Rio de Janeiro');

-- Consulta de dados
SELECT Nome, Email
FROM Cliente
WHERE Cidade = 'São Paulo'
ORDER BY Nome ASC;

-- Atualização de dados
UPDATE Cliente
SET Email = 'joao.novo@email.com'
WHERE ID = 1;

-- Exclusão de dados
DELETE FROM Cliente
WHERE ID = 2;
```

---

### **Resumo**
A estrutura básica do SQL é composta por comandos e cláusulas que permitem:
- **Criar e modificar estruturas de banco de dados** (DDL).
- **Manipular dados** (DML): inserir, consultar, atualizar e excluir.
- **Controlar acesso e transações** (DCL e TCL).

Esses comandos e cláusulas são a base para trabalhar com bancos de dados relacionais, como MySQL, PostgreSQL, Oracle e SQL Server. 😊
___
## A importância das funções de agregação
As funções de agregação em bancos de dados são essenciais para a análise e manipulação de dados, permitindo realizar cálculos sobre conjuntos de valores e retornar um único resultado. Elas são amplamente utilizadas em consultas SQL para sumarizar, agregar ou extrair informações relevantes de grandes volumes de dados.
### Análise de Dados
Essas funções são fundamentais para análises estatísticas e relatórios, como calcular médias, totais, tendências. isso é crucial para tomada de decisão com base em dados.
