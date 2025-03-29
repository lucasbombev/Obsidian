tags: #Faculdade #Concurso #Software 
___
As expressões JOIN em SQL são fundamentais para realizar consultas que envolvem múltiplas tabelas em um banco de dados relacional. Elas permitem combinar dados de diferentes tabelas com base em uma condição comum, como uma chave primária e uma chave estrangeira. Neste texto, abordaremos os principais tipos de JOIN, suas aplicações e exemplos práticos.
## O que é ?
Um JOIN (ou junção) é uma operação em SQL que permite recuperar dados de duas ou mais tabelas que estão relacionadas. As junções são usadas para agregar dados, facilitando a análise e a visualização de informações que estão distribuídas em várias tabelas.
## Principais tipos de JOIN
![[Pasted image 20250327132626.png]]

### Inner JOIN
O INNER JOIN retorna apenas os registros que têm correspondência nas duas tabelas. É o tipo de JOIN mais comum. É como se fosse a interseção na teoria dos conjuntos, O **INNER JOIN** retorna apenas os registros que têm correspondências em ambas as tabelas.
Claro! Vou te dar um exemplo simples de como usar o **INNER JOIN** em SQL.

### Suponha que temos duas tabelas:

1. **Tabela `Clientes`**:
   | id  | nome      |
   |-----|-----------|
   | 1   | João      |
   | 2   | Maria     |
   | 3   | Pedro     |

2. **Tabela `Pedidos`**:
   | id  | cliente_id | produto     |
   |-----|------------|-------------|
   | 101 | 1          | Notebook    |
   | 102 | 2          | Smartphone  |
   | 103 | 1          | Tablet      |

### Objetivo:
Queremos listar os pedidos feitos pelos clientes, mostrando o nome do cliente e o produto comprado.

### Consulta com **INNER JOIN**:
```sql
SELECT Clientes.nome, Pedidos.produto
FROM Clientes
INNER JOIN Pedidos ON Clientes.id = Pedidos.cliente_id;
```

### Resultado:
| nome  | produto     |
|-------|-------------|
| João  | Notebook    |
| Maria | Smartphone  |
| João  | Tablet      |

### Explicação:
- O **INNER JOIN** combina as linhas das tabelas `Clientes` e `Pedidos` onde a condição `Clientes.id = Pedidos.cliente_id` é verdadeira.
- Apenas os registros que têm correspondência em ambas as tabelas são retornados. Por exemplo, o cliente "Pedro" não aparece no resultado porque não fez nenhum pedido.
___
### LEFT JOIN
Claro! Vou te dar um exemplo simples de como usar o **LEFT JOIN** em SQL.

### Suponha que temos as mesmas tabelas do exemplo anterior:

1. **Tabela `Clientes`**:
   | id  | nome      |
   |-----|-----------|
   | 1   | João      |
   | 2   | Maria     |
   | 3   | Pedro     |

2. **Tabela `Pedidos`**:
   | id  | cliente_id | produto     |
   |-----|------------|-------------|
   | 101 | 1          | Notebook    |
   | 102 | 2          | Smartphone  |
   | 103 | 1          | Tablet      |

### Objetivo:
Queremos listar todos os clientes, mesmo aqueles que não fizeram pedidos, e mostrar os pedidos feitos por eles (se houver).

### Consulta com **LEFT JOIN**:
```sql
SELECT Clientes.nome, Pedidos.produto
FROM Clientes
LEFT JOIN Pedidos ON Clientes.id = Pedidos.cliente_id;
```

### Resultado:
| nome  | produto     |
|-------|-------------|
| João  | Notebook    |
| João  | Tablet      |
| Maria | Smartphone  |
| Pedro | NULL        |

### Explicação:
- O **LEFT JOIN** retorna **todos os registros da tabela à esquerda (`Clientes`)**, mesmo que não haja correspondência na tabela à direita (`Pedidos`).
- Quando não há correspondência, os campos da tabela à direita são preenchidos com `NULL`.
- No exemplo, o cliente "Pedro" não fez nenhum pedido, então o campo `produto` aparece como `NULL` para ele.
___
### RIGTH JOIN
Claro! Vou te dar um exemplo simples de como usar o **RIGHT JOIN** em SQL.

### Suponha que temos as mesmas tabelas dos exemplos anteriores:

1. **Tabela `Clientes`**:
   | id  | nome      |
   |-----|-----------|
   | 1   | João      |
   | 2   | Maria     |
   | 3   | Pedro     |

2. **Tabela `Pedidos`**:
   | id  | cliente_id | produto     |
   |-----|------------|-------------|
   | 101 | 1          | Notebook    |
   | 102 | 2          | Smartphone  |
   | 103 | 1          | Tablet      |
   | 104 | 4          | Fone de Ouvido |  <!-- Novo pedido sem cliente correspondente -->

### Objetivo:
Queremos listar todos os pedidos, mesmo aqueles que não têm um cliente correspondente na tabela `Clientes`.

### Consulta com **RIGHT JOIN**:
```sql
SELECT Clientes.nome, Pedidos.produto
FROM Clientes
RIGHT JOIN Pedidos ON Clientes.id = Pedidos.cliente_id;
```

### Resultado:
| nome  | produto        |
|-------|----------------|
| João  | Notebook       |
| Maria | Smartphone     |
| João  | Tablet         |
| NULL  | Fone de Ouvido |  <!-- Pedido sem cliente correspondente -->

### Explicação:
- O **RIGHT JOIN** retorna **todos os registros da tabela à direita (`Pedidos`)**, mesmo que não haja correspondência na tabela à esquerda (`Clientes`).
- Quando não há correspondência, os campos da tabela à esquerda são preenchidos com `NULL`.
- No exemplo, o pedido "Fone de Ouvido" não tem um cliente correspondente na tabela `Clientes`, então o campo `nome` aparece como `NULL`.

Esse é um exemplo básico de como o **RIGHT JOIN** funciona! 😊
___
### FULL JOIN
Claro! Vou explicar o **FULL JOIN** (ou **FULL OUTER JOIN**) em SQL com um exemplo simples.

### O que é **FULL JOIN**?
O **FULL JOIN** retorna **todos os registros** das duas tabelas envolvidas na junção, combinando os registros que têm correspondência e incluindo os registros que não têm correspondência em uma das tabelas. Quando não há correspondência, os campos da tabela sem correspondência são preenchidos com `NULL`.

---

### Suponha que temos as mesmas tabelas dos exemplos anteriores:

1. **Tabela `Clientes`**:
   | id  | nome      |
   |-----|-----------|
   | 1   | João      |
   | 2   | Maria     |
   | 3   | Pedro     |

2. **Tabela `Pedidos`**:
   | id  | cliente_id | produto        |
   |-----|------------|----------------|
   | 101 | 1          | Notebook       |
   | 102 | 2          | Smartphone     |
   | 103 | 1          | Tablet         |
   | 104 | 4          | Fone de Ouvido |  <!-- Pedido sem cliente correspondente -->

---

### Objetivo:
Queremos listar **todos os clientes e todos os pedidos**, combinando os registros que têm correspondência e incluindo os registros que não têm correspondência em uma das tabelas.

---

### Consulta com **FULL JOIN**:
```sql
SELECT Clientes.nome, Pedidos.produto
FROM Clientes
FULL JOIN Pedidos ON Clientes.id = Pedidos.cliente_id;
```

---

### Resultado:
| nome  | produto        |
|-------|----------------|
| João  | Notebook       |
| Maria | Smartphone     |
| João  | Tablet         |
| Pedro | NULL           |  <!-- Cliente sem pedido correspondente -->
| NULL  | Fone de Ouvido |  <!-- Pedido sem cliente correspondente -->

---

### Explicação:
1. **Registros com correspondência**:
   - Os pedidos feitos por "João" e "Maria" são combinados com os clientes correspondentes.
   
2. **Registros sem correspondência na tabela `Clientes`**:
   - O pedido "Fone de Ouvido" não tem um cliente correspondente na tabela `Clientes`, então o campo `nome` aparece como `NULL`.

3. **Registros sem correspondência na tabela `Pedidos`**:
   - O cliente "Pedro" não fez nenhum pedido, então o campo `produto` aparece como `NULL`.

---

### Resumo:
O **FULL JOIN** é útil quando você quer ver todos os registros de ambas as tabelas, independentemente de haver correspondência ou não. Ele combina os resultados do **LEFT JOIN** e do **RIGHT JOIN**.

Esse é um exemplo básico de como o **FULL JOIN** funciona! 😊