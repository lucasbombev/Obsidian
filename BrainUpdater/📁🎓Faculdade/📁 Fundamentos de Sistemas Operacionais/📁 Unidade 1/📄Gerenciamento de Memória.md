tags: #Faculdade #Vestibulares 
___
   O uso ideal para qualquer sistema operacional, deveria ser uma memória ram grande, rápida e não volátil, mas atualmente essa tecnologia não está disponível. Devido a isso, os sistemas operacionais classificam seus tipos de memória em uma hierarquia, considerando a memória cache, memória principal e armazenamento em disco. Logo, os sistemas operacionais devem deve gerenciar (alocando e liberando) os espaços da memória que são utilizados durante a execução de um processo, ou seja, deve gerenciar cuidadosamente a memória do computador.
## Abstração de Memória Física
A abstração de memória física refere-se à técnica utilizada pelos sistemas operacionais para esconder dos programas as complexidades do gerenciamento direto da memória RAM (Random Access Memory). Em vez de os programas acessarem diretamente os endereços físicos da memória, o sistema operacional fornece uma camada de abstração que gerencia como a memória é alocada, utilizada e liberada.
## Espaço de Endereçamento Virtual
Uma das principais formas de abstração de memória é o uso de **espaço de endereçamento virtual**. Cada processo em execução no sistema acredita que tem acesso a um espaço de memória contíguo e exclusivo, que vai do endereço 0 até um endereço máximo (dependendo da arquitetura do sistema, como 32 bits ou 64 bits). No entanto, esse espaço de endereçamento virtual não corresponde diretamente à memória física. Em vez disso, o sistema operacional mapeia os endereços virtuais para endereços físicos reais na RAM.
![[Pasted image 20250319192538.png]]
## Troca de processos (Swapping)
Quando a memória física de um computador não é grande o suficiente para armazenar todos os processos, surge a necessidade de técnicas para lidar com essa limitação. Uma abordagem é o **swapping (troca de processos ver Figura 2)** onde cada processo é trazido para a memória, executado por um período e depois devolvido ao disco. A memória física é insuficiente para armazenar todos os dados necessários, o sistema operacional utiliza uma técnica chamada **memória virtual**. Parte dos dados é movida para o disco (em uma área chamada **swap** ou **arquivo de paginação**), liberando espaço na RAM. Quando esses dados são necessários novamente, eles são trazidos de volta para a memória física. Isso dá a ilusão de que o sistema possui mais memória RAM do que realmente tem.
![[Pasted image 20250319192839.png]]
## Gerenciamento de Memória Livre
Quando a memória é alocada dinamicamente, o sistema operacional precisa gerenciá-la. Existem duas abordagens principais para **rastrear o uso de memória**: **mapas de bits e listas encadeadas.** Com mapas de bits, a memória é dividida em unidades de alocação, e um bit é usado para indicar se uma unidade está livre ou ocupada. Embora isso forneça um controle simples, a busca por blocos livres pode ser lenta. Outra técnica é manter listas encadeadas de espaços livres e segmentos alocados, o que permite uma alocação mais eficiente.
![[Pasted image 20250319193251.png]]

## Paginação
A **paginação** é uma técnica de gerenciamento de memória utilizada pelos sistemas operacionais para implementar a abstração de memória virtual. Ela permite que a memória física (RAM) seja dividida em blocos de tamanho fixo chamados **quadros de página** (ou frames), enquanto a memória virtual (espaço de endereçamento de cada processo) é dividida em blocos do mesmo tamanho chamados **páginas**. O sistema operacional gerencia o mapeamento entre páginas virtuais e quadros de página físicos por meio de uma estrutura de dados chamada **tabela de páginas**.
### Divisão da memória em páginas e quadros
- **Memória virtual**: O espaço de endereçamento de um processo é dividido em páginas de tamanho fixo (por exemplo, 4 KB).
- **Memória física**: A RAM é dividida em quadros de página do mesmo tamanho das páginas virtuais (por exemplo, 4 KB).

Cada página virtual pode ser mapeada para qualquer quadro de página físico disponível na RAM. Isso permite que a memória física seja alocada de forma não contígua, ou seja, páginas virtuais sequenciais podem ser armazenadas em quadros de página físicos espalhados pela RAM.
___
### Tabela de páginas
A **tabela de páginas** é uma estrutura de dados mantida pelo sistema operacional para cada processo. Ela mapeia páginas virtuais para quadros de página físicos. Cada entrada na tabela de páginas contém:

- O número do quadro de página físico correspondente.
    
- Bits de controle, como:
    
    - **Bit de presente/ausente**: Indica se a página está na RAM ou foi movida para o disco (swap).
        
    - **Bit de leitura/escrita**: Define se a página pode ser escrita ou é somente leitura.
        
    - **Bit de acesso**: Indica se a página foi acessada recentemente (útil para algoritmos de substituição de páginas).
        
    - **Bit de modificação**: Indica se a página foi modificada (útil para saber se precisa ser salva no disco antes de ser substituída).

## Vantagens da Paginação
- **Fragmentação interna**: Como as páginas têm tamanho fixo, não há fragmentação externa (espaço livre entre alocações), mas pode haver fragmentação interna (espaço não utilizado dentro de uma página).
- **Isolamento entre processos**: Cada processo tem sua própria tabela de páginas, o que impede que um processo acesse a memória de outro.
- **Alocação não contígua**: As páginas de um processo podem ser armazenadas em qualquer lugar da RAM, sem necessidade de serem contíguas.
- **Facilita a memória virtual**: Permite que partes da memória sejam movidas para o disco quando necessário.
## Algoritmo de Substituição de Páginas
Os algoritmos de substituição de páginas são essenciais para lidar com **faltas de página na memória virtual**. Quando uma página precisa ser removida para dar lugar a uma nova, é crucial escolher uma que não esteja intensamente em uso para otimizar o desempenho do sistema. Diversos algoritmos foram desenvolvidos para esse fim. A escolha da página a ser removida pode ser comparada ao problema de substituição de blocos em caches de memória ou na gestão de páginas da web em servidores. Esses algoritmos variam na maneira como decidem qual página remover, levando em consideração fatores como frequência de uso e se a página pertence ao processo atual ou a outro. Essa seleção impacta diretamente no comportamento e na eficiência do sistema operacional.
Os algoritmos de substituição de páginas são usados quando ocorre uma falta de página na memória virtual. Eles decidem qual página deve ser removida para dar lugar à nova.

- O **algoritmo ótimo** escolhe a página que não será referenciada por mais tempo, mas é impraticável na implementação real.
- O **NRU _(Not Recently Used_)** classifica páginas com base em referência e modificação, removendo uma página aleatória de uma classe específica.
- **FIFO** remove a página mais antiga, sem considerar seu uso atual.
- O algoritmo **segunda chance** é uma versão do FIFO que leva em conta o bit de referência. 
- O **algoritmo do relógio** mantém as páginas em uma lista circular, removendo a primeira página com bit de referência igual a 0.
- O **LRU (_Least Recently Used_)** remove a página menos usada recentemente, mas sua implementação completa é complexa.
- A simulação do LRU em software pode ser feita usando o algoritmo **NFU (_Not Frequently Used_)**, que conta as referências das páginas. Um resumo das técnicas podem ser encontradas na Tabela 1.
![[Pasted image 20250319204638.png]]
