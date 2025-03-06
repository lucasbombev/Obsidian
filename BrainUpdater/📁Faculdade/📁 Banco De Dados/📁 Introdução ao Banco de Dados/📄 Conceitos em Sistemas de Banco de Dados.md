Tags: #BancoDeDados #Software #Faculdade 
___
## Introdução
Podemos dizer que um banco de dados é: 
- uma coleção de dados relacionados que tem informação sobre algo do mundo real.
- Possui coerência lógica entre de dados e significado
### O que é um SGBD?

Segundo DATE (2004), um Sistema Gerenciador de Banco de Dados (SGBD) é um software genérico para manipular Banco de Dados. Ele permite a definição, construção e manejo de um Banco de Dados para diversas aplicações. Um SGBD possui uma visão lógica (projeto do BD), uma linguagem de definição de dados, linguagem de manipulação de dados e utilitários importantes.

Os SGBDs também facilitam a conversão e a reorganização do Banco de Dados. Dessa forma podemos dizer que os SGBDs são programas de computador, que ajudam na:

- Definição e construção do Banco de Dados: que é o processo de criar uma estrutura inicial com tabelas e preenche-las com dados; 
- Manipulação dos dados do Banco de Dados: são as operações de consultas alteração, exclusão realizadas nos dados.

| Aplicações de Banco de Dados                                                    |
| ------------------------------------------------------------------------------- |
| Banco: para informações de cliente, contas, empréstimos e transações bancárias; |
| Universidades: informações de alunos, cursos e notas                            |
| Linhas Aéreas: reservas e informações de horários;                              |
| Indústria: controlar a produção de itens da fábrica, estoques e pedidos.        |
| Vendas: informações de cliente, produto e compras                               |
| Biblioteca: informações de livros, nome dos alunos e solicitações.              |
___
## Visões do Banco de Dados

É função do Administrador de Banco de Dados - DataBase Administrator (DBA) garantir que os dados estejam seguros e com desempenho satisfatório. Esse profissional é responsável por garantir:
- Segurança
- Recuperação
- Disponibilidade
- Suporte a equipe de desenvolvimento
- Implementação do banco de dados
### Níveis de Abstração

#### **Nível Físico (Internal Level)**

É o nível mais baixo de abstração, onde os dados são realmente armazenados no sistema. Ele descreve **como os dados são armazenados fisicamente** no banco de dados, incluindo detalhes como:

- Estruturas de armazenamento (arquivos, tabelas, índices).
- Métodos de acesso (hashing, árvores B, etc.).
- Alocação de espaço em disco.
- Técnicas de compressão e criptografia.
#### **Nível Conceitual (Conceptual Level)**

É o nível intermediário de abstração, que descreve **o que o banco de dados contém** e como os dados estão organizados logicamente. Ele fornece uma visão global do banco de dados, independente de como os dados são armazenados fisicamente. Inclui:

- A estrutura lógica do banco de dados (entidades, atributos, relacionamentos).
- Regras de integridade e consistência dos dados.
- Definição de esquemas (tabelas, chaves primárias, chaves estrangeiras).
### **Nível de Visão (External Level)**

É o nível mais alto de abstração, que descreve **como os usuários finais veem os dados**. Ele oferece uma visão personalizada do banco de dados para diferentes grupos de usuários, ocultando detalhes desnecessários. Cada visão pode mostrar apenas uma parte dos dados, adaptada às necessidades específicas de um usuário ou aplicação. Inclui:

- Subconjuntos de tabelas e atributos.
- Consultas personalizadas.
- Dados agregados ou transformados.
___
## Projeto de Banco de Dados
É um projeto estruturado que visa garantir alguns requisitos para que o banco de dados atenda as necessidades da organização, a elaboração de um projeto passa por várias etapas para garantir sua eficiência.

### Modelo Conceitual
Aqui, o foco é criar uma visão abstrata e de alto nível do banco de dados, sem se preocupar com detalhes de implementação. Isso inclui:
🔹 _O que é?_  
O modelo conceitual é o rascunho inicial do banco de dados, feito sem se preocupar com detalhes técnicos. Ele mostra **o que será armazenado** e **como as informações se relacionam**, sem falar de tabelas, colunas ou chaves primárias.

🔹 _Como funciona?_  
É representado por um diagrama chamado **DER (Diagrama Entidade-Relacionamento)**, que contém:

- **Entidades** (_como "Aluno", "Curso", "Professor"_)
- **Atributos** (_como "Nome", "Data de Nascimento", "Matrícula"_)
- **Relacionamentos** (_como "Aluno se matricula em Curso"_)

🔹 _Exemplo (Casa 🏠)_  
Imagine que você quer construir uma casa. O modelo conceitual seria um **rascunho à mão** mostrando os cômodos principais e como eles se conectam (sala ligada à cozinha, quartos próximos ao banheiro, etc.). Não há detalhes sobre tamanho, materiais ou fiação elétrica.

### Modelo Lógico

Nesta etapa, o modelo conceitual é transformado em um esquema lógico que pode ser implementado em um SGBD (Sistema de Gerenciamento de Banco de Dados).
🔹 _O que é?_  
Aqui, transformamos o modelo conceitual em algo mais técnico, adaptando-o a um **banco de dados relacional** (como MySQL, PostgreSQL, SQL Server).

🔹 _Como funciona?_  
Agora falamos de **tabelas**, **atributos**, **tipos de dados** e **restrições**, como:

- Definir **chaves primárias** (para identificar registros)
- Criar **chaves estrangeiras** (para ligar tabelas)
- Escolher **tipos de dados** (texto, número, data)

🔹 _Exemplo (Casa 🏠)_  
Agora, em vez de um rascunho, temos um **projeto arquitetônico** com medidas exatas, tipos de materiais e estrutura detalhada. Ainda não construímos nada, mas já temos tudo bem planejado.

### Modelo Físico
🔹 _O que é?_  
O modelo físico é a implementação real do banco de dados em um sistema de gerenciamento (como MySQL, Oracle, SQL Server).
Agora, os dados podem ser **armazenados e consultados**.

🔹 _Exemplo (Casa 🏠)_  
É a **construção real da casa**! Pegamos o projeto detalhado e começamos a levantar paredes, instalar portas, janelas, fiação elétrica, etc.
![[Pasted image 20250305130019.png]]
