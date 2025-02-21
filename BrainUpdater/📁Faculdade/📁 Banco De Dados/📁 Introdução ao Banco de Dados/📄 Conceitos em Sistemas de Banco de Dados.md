Tags: #BancoDeDados #Software
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

- Identificação das entidades (objetos do mundo real) e seus atributos.
- Definição dos relacionamentos entre as entidades.
- Uso de ferramentas como diagramas **Entidade-Relacionamento (ER)** para representar a estrutura.

Imagine que você está planejando construir uma casa. Antes de começar a obra, você precisa de um **plano** que mostre como a casa será: quantos quartos terá, onde ficará a cozinha, a sala, os banheiros, etc. Esse plano é uma representação abstrata da casa, sem detalhes de como serão os tijolos, a fiação elétrica ou os canos.

No mundo dos bancos de dados, o **modelo conceitual** é como esse plano da casa. Ele é uma representação simples e de alto nível de como os dados serão organizados, sem se preocupar com detalhes técnicos de como serão armazenados no computador.

**Resultado:** Um modelo conceitual que descreve as entidades, atributos e relacionamentos.

### Modelo Lógico

Nesta etapa, o modelo conceitual é transformado em um esquema lógico que pode ser implementado em um SGBD (Sistema de Gerenciamento de Banco de Dados). Isso envolve:

- Mapeamento das entidades e relacionamentos para tabelas, colunas e chaves.
- Definição de tipos de dados, restrições e regras de integridade.
- Normalização do banco de dados para evitar redundâncias e inconsistências.

**Resultado:** Um esquema lógico detalhado, pronto para ser implementado.

Aqui é como se posse a planta da casa, com os tipos de tijolo, as medidas dos comodos, cores das paredes, etc. O nível de abstração é um pouco menor do que o modelo conceitual.

### Modelo Físico
