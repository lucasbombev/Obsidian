tags: #BancoDeDados #Software #Faculdade #BackEnd 
___
## O que é um modelo de dados?
Um **[[modelo de dados]]** é uma estrutura que define como os dados são organizados, armazenados, manipulados e acessados em um sistema de banco de dados.
## Modelo Relacional
- Usa **tabelas** para organizar os dados. Cada tabela tem **linhas (registros)** e **colunas (atributos)**.
- Exemplo: Um banco de dados de clientes, onde temos uma tabela "Clientes" com colunas como "Nome", "CPF" e "Endereço".
- Banco de Dados: MySQL, PostgreSQL, SQL Server, Oracle.
___
## Modelo Entidade - Relacionamento (MER)
Ele foi proposto por Peter Chen em 1976 e é amplamente utilizado para projetar bancos de dados de forma clara e organizada, antes da implementação em um SGBD (Sistema de Gerenciamento de Banco de Dados).
### Representação gráfica
![[Pasted image 20250306182013.png]]
#### Entidades 
Objetos do mundo real que possuem existência independente e sobre os quais queremos armazenar informações.
Exemplo: Funcionários, Departamentos, Empresa, Clientes, Fornecedores,
Alunos
#### Atributos
São características ou propriedades das identidades.
Exemplo: CPF, RG, Nome, Endereço do fornecedor, Estado Civil do funcionário, Nome do aluno, Número da turma, etc.
#### Relacionamento
Representa a relação entre as identidades
**Exemplo de Representação de ER**
![[Pasted image 20250306182312.png]]
