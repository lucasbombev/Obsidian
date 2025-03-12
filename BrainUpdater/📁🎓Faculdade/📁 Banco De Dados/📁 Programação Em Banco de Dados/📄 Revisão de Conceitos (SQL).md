tags: #BancoDeDados #Concurso #Faculdade #Software 
___
Aqui estão os comandos básicos mais comuns em SQL, com exemplos:

### **1. SELECT** (Selecionar dados)

Usado para recuperar dados de uma tabela.

```sql
SELECT * FROM clientes; -- Seleciona todos os registros da tabela "clientes"
SELECT nome, idade FROM clientes; -- Seleciona apenas as colunas "nome" e "idade"
SELECT * FROM clientes WHERE idade > 18; -- Filtra clientes com idade maior que 18
```

---

### **2. INSERT INTO** (Inserir dados)

Usado para adicionar novos registros a uma tabela.

```sql
INSERT INTO clientes (id, nome, idade) VALUES (1, 'Maria', 25);
INSERT INTO clientes (id, nome, idade) VALUES (2, 'João', 30);
```

---

### **3. UPDATE** (Atualizar dados)

Altera valores já existentes em uma tabela.

```sql
UPDATE clientes SET idade = 26 WHERE nome = 'Maria';
```

---

### **4. DELETE** (Excluir dados)

Remove registros de uma tabela.

```sql
DELETE FROM clientes WHERE nome = 'João';
```

---

### **5. CREATE TABLE** (Criar uma tabela)

Cria uma nova tabela no banco de dados.

```sql
CREATE TABLE clientes (
    id INT PRIMARY KEY,
    nome VARCHAR(100),
    idade INT
);
```

---

### **6. ALTER TABLE** (Modificar uma tabela)

Altera a estrutura de uma tabela.

```sql
ALTER TABLE clientes ADD COLUMN email VARCHAR(150); -- Adiciona uma nova coluna "email"
ALTER TABLE clientes DROP COLUMN idade; -- Remove a coluna "idade"
```

---

### **7. DROP TABLE** (Excluir uma tabela)

Remove uma tabela do banco de dados.

```sql
DROP TABLE clientes;
```

---

### **8. CREATE DATABASE** (Criar um banco de dados)

Cria um novo banco de dados.

```sql
CREATE DATABASE meu_banco;
```

---

### **9. DROP DATABASE** (Excluir um banco de dados)

Remove um banco de dados do sistema.

```sql
DROP DATABASE meu_banco;
```

---

### **10. JOIN** (Unir tabelas)

Une dados de duas ou mais tabelas.

```sql
SELECT pedidos.id, clientes.nome, pedidos.valor
FROM pedidos
INNER JOIN clientes ON pedidos.cliente_id = clientes.id;
```

---

### **11. GROUP BY e HAVING** (Agrupar resultados)

Agrupa registros e aplica condições em agregações.

```sql
SELECT idade, COUNT(*) AS total
FROM clientes
GROUP BY idade
HAVING COUNT(*) > 1;
```

---

### **12. ORDER BY** (Ordenar resultados)

Ordena os registros retornados.

```sql
SELECT * FROM clientes ORDER BY idade DESC; -- Ordena por idade em ordem decrescente
```

---

### **13. LIMIT** (Limitar resultados)

Restringe a quantidade de registros retornados.

```sql
SELECT * FROM clientes LIMIT 5; -- Retorna apenas os 5 primeiros registros
```

Esses são os comandos mais básicos e essenciais do SQL. Quer mais detalhes sobre algum deles?
___
Claro! Vamos falar sobre **funções de agregação no SQL**, que são usadas para realizar cálculos em conjuntos de dados e retornar um único valor. Elas são essenciais para análise de dados e resumos estatísticos. Vou explicar as principais funções de agregação, como usá-las e dar exemplos práticos.

---

### **Principais Funções de Agregação**

1. **COUNT()**:
   - Conta o número de linhas que atendem a uma condição.
   - Exemplo:
     ```sql
     SELECT COUNT(*) FROM Produtos;
     ```
     Retorna o número total de produtos na tabela `Produtos`.

2. **SUM()**:
   - Soma os valores de uma coluna numérica.
   - Exemplo:
     ```sql
     SELECT SUM(preco) FROM Produtos;
     ```
     Retorna a soma de todos os preços na tabela `Produtos`.

3. **AVG()**:
   - Calcula a média dos valores de uma coluna numérica.
   - Exemplo:
     ```sql
     SELECT AVG(preco) FROM Produtos;
     ```
     Retorna a média dos preços na tabela `Produtos`.

4. **MIN()**:
   - Retorna o menor valor de uma coluna.
   - Exemplo:
     ```sql
     SELECT MIN(preco) FROM Produtos;
     ```
     Retorna o preço mais baixo na tabela `Produtos`.

5. **MAX()**:
   - Retorna o maior valor de uma coluna.
   - Exemplo:
     ```sql
     SELECT MAX(preco) FROM Produtos;
     ```
     Retorna o preço mais alto na tabela `Produtos`.

---

### **Como Usar Funções de Agregação**

#### 1. **Básico**
Você pode usar funções de agregação diretamente em uma consulta para obter um único valor:

```sql
SELECT AVG(preco) AS media_preco FROM Produtos;
```

#### 2. **Com `GROUP BY`**
Funções de agregação são frequentemente usadas com `GROUP BY` para agrupar resultados com base em uma ou mais colunas:

```sql
SELECT id_marca, AVG(preco) AS media_preco
FROM Produtos
GROUP BY id_marca;
```

Isso retorna a média de preços dos produtos agrupados por `id_marca`.

#### 3. **Com `HAVING`**
O `HAVING` é usado para filtrar resultados após a agregação. Diferente do `WHERE`, que filtra antes da agregação:

```sql
SELECT id_marca, AVG(preco) AS media_preco
FROM Produtos
GROUP BY id_marca
HAVING AVG(preco) > 100;
```

Retorna apenas as marcas cuja média de preços é maior que 100.

---

### **Exemplos Práticos**

#### Tabela de Exemplo: `Produtos`

| id  | produto      | preco  | id_marca |
|-----|--------------|--------|----------|
| 1   | Camiseta     | 50.00  | 1        |
| 2   | Sapato       | 120.00 | 2        |
| 3   | Calça        | 80.00  | 1        |
| 4   | Boné         | 30.00  | 3        |
| 5   | Meia         | 10.00  | 1        |

#### Exemplo 1: Contar o número de produtos
```sql
SELECT COUNT(*) AS total_produtos FROM Produtos;
```

**Output:**
| total_produtos |
|----------------|
| 5              |

#### Exemplo 2: Soma dos preços
```sql
SELECT SUM(preco) AS total_precos FROM Produtos;
```

**Output:**
| total_precos |
|--------------|
| 290.00       |

#### Exemplo 3: Média de preços por marca
```sql
SELECT id_marca, AVG(preco) AS media_preco
FROM Produtos
GROUP BY id_marca;
```

**Output:**
| id_marca | media_preco |
|----------|-------------|
| 1        | 46.67       |
| 2        | 120.00      |
| 3        | 30.00       |

#### Exemplo 4: Maior preço
```sql
SELECT MAX(preco) AS maior_preco FROM Produtos;
```

**Output:**
| maior_preco |
|-------------|
| 120.00      |

#### Exemplo 5: Menor preço por marca
```sql
SELECT id_marca, MIN(preco) AS menor_preco
FROM Produtos
GROUP BY id_marca;
```

**Output:**
| id_marca | menor_preco |
|----------|-------------|
| 1        | 10.00       |
| 2        | 120.00      |
| 3        | 30.00       |

---

### **Dicas Importantes**
1. **`NULL` em Funções de Agregação**:
   - Funções como `COUNT(column)` ignoram valores `NULL`.
   - `COUNT(*)` conta todas as linhas, independentemente de valores `NULL`.

2. **`DISTINCT` com Funções de Agregação**:
   - Você pode usar `DISTINCT` para considerar apenas valores únicos:
     ```sql
     SELECT COUNT(DISTINCT id_marca) FROM Produtos;
     ```

3. **Combinação de Funções**:
   - Você pode combinar várias funções em uma única consulta:
     ```sql
     SELECT AVG(preco), MAX(preco), MIN(preco) FROM Produtos;
     ```

---

### **Resumo**
Funções de agregação são poderosas para resumir e analisar dados em SQL. Aqui está um resumo das principais:

| Função   | Descrição                          |
|----------|------------------------------------|
| COUNT()  | Conta o número de linhas.          |
| SUM()    | Soma os valores de uma coluna.     |
| AVG()    | Calcula a média dos valores.       |
| MIN()    | Retorna o menor valor.             |
| MAX()    | Retorna o maior valor.             |

Se precisar de mais exemplos ou tiver dúvidas, é só perguntar! 😊