tags: #AnaliseDeProjetos #Faculdade 
___
## Introdução a UML
A Unified Modeling Language (UML) é uma linguagem padronizada para modelagem de sistemas de software, amplamente utilizada na engenharia de software para descrever, visualizar, especificar e documentar os componentes de um sistema. Criada inicialmente na década de 1990 por Grady Booch, James Rumbaugh e Ivar Jacobson, a UML tornou-se uma norma internacional pela Object Management Group (OMG). A sua principal força reside na capacidade de representar de forma gráfica diferentes aspectos de um sistema, incluindo sua estrutura, comportamento e interações, permitindo que desenvolvedores, analistas e stakeholders comuniquem-se de maneira clara e compreensível.

A UML é composta por diversos tipos de diagramas, organizados em duas categorias principais: diagramas estruturais e diagramas comportamentais. Os diagramas estruturais, como o de classes, de componentes e de objetos, destacam a arquitetura estática do sistema. Já os diagramas comportamentais, como o de casos de uso, de sequência e de atividades, focam em ilustrar o comportamento dinâmico e as interações dos componentes ao longo do tempo. Essa flexibilidade faz da UML uma ferramenta essencial no desenvolvimento de sistemas complexos, auxiliando na redução de ambiguidades, na validação de requisitos e na implementação de soluções mais eficientes e robustas.
## Categorias de Diagramas UML
A UML organiza seus diagramas em categorias para facilitar a compreensão e a aplicação no desenvolvimento de sistemas. Essas categorias refletem as diferentes perspectivas que um sistema pode demandar: desde a estrutura estática até o comportamento dinâmico e as interações entre componentes. Divididos em diagramas estruturais e diagramas comportamentais, eles oferecem uma abordagem sistemática para representar tanto a arquitetura quanto as funcionalidades de um sistema. Essa divisão permite aos desenvolvedores escolherem o tipo de diagrama mais adequado às suas necessidades específicas durante o ciclo de vida do projeto, garantindo uma modelagem clara e consistente. A UML possui 14 tipos de diagramas divididos em:

- Diagramas Estruturais: Representam a organização estática de um sistema (ex.: Diagrama de Classes).
- Diagramas Comportamentais: Representam a dinâmica do sistema (ex.: Diagramas de Sequência e de Estados).
### Diagrama de classe
Definição:

- Mostra a estrutura estática do sistema, destacando classes, atributos, métodos e os relacionamentos entre elas.

Elementos-chave:

- Classes: Representadas como retângulos, com três divisões (nome, atributos, métodos).

Relacionamentos:

- Associação: Conexão entre classes.
- Herança: Relacionamento "é um".
- Agregação/Composição: Representa relações de "tem um".

**Exemplo Prático:**

Imagine um sistema de biblioteca:

- Classe Livro com atributos (título, autor) e métodos (emprestar(), devolver()).
- Classe Usuário que herda de Pessoa e possui métodos como consultarReserva().
![[Pasted image 20250329113616.png]]
## Diagrama de sequência
Definição:

Representa a interação entre objetos ao longo do tempo, detalhando a troca de mensagens em uma sequência temporal.

Elementos-chave:

- Objetos/Participantes: Representados por retângulos no topo;
- Lifelines: Linhas verticais que representam o tempo de vida dos objetos;
- Mensagens: Setas horizontais indicando chamadas de método, respostas, ou mensagens simples.

**Exemplo Prático:**

Um usuário solicita um livro no sistema da biblioteca:

- Usuário → Sistema: Envia solicitação.
- Sistema → Banco de Dados: Verifica disponibilidade.
- Sistema → Usuário: Confirma reserva.
![[Pasted image 20250329113907.png]]
## Diagrama de comunicação ou colaboração
Definição:

- Foca na interação entre objetos, destacando as mensagens trocadas e suas relações.

Elementos-chave:

- Objetos: Representados por retângulos com seus nomes;
- Mensagens: Indicadas por linhas numeradas que mostram a sequência da interação.

**Exemplo Prático:**

No processo de reservar um livro:

- Objeto Usuário envia a mensagem 1: reservarLivro() para Sistema.
- O Sistema envia 1.1: consultarDisponibilidade() para Banco de Dados.
![[Pasted image 20250329114233.png]]
## Diagrama de Estado

Definição:

- Mostra os estados pelos quais um objeto passa durante o seu ciclo de vida e as transições entre esses estados.

Elementos-chave:

- Estados: Representados como círculos ou retângulos arredondados;
- Transições: Setas indicando a mudança de um estado para outro;
- Eventos/Condições: Disparam as transições.

**Exemplo Prático:**

Ciclo de vida de um livro:

- Estado Disponível.
- Transição para Reservado após um evento reserva realizada.
- Transição para Emprestado após livro emprestado.
