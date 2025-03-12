tags: #Software #Faculdade 
___

## O que é um Sistema Operacional?

Um **Sistema Operacional (SO)** é um software que atua como intermediário entre o hardware (parte física do computador) e o usuário (ou outros programas). Ele gerencia os recursos do computador, como processador, memória, armazenamento e dispositivos de entrada/saída, e fornece uma interface para que os usuários e aplicativos possam interagir com o sistema.
![[Pasted image 20250227195319.png]]
## Estrutura do Sistema Operacional
O S.O pode ser dividido em duas camadas principais:
- **Modo Kernel/Núcleo:** É a parte central do sistema operacional, tem acesso total ao hardware e controla as funções mais básicas do computador como gerenciamento de memória, processamento e dispositivos de E/S.
- **Modo Usuário:** O modo usuário é o ambiente em que os programas de aplicativos são executados. Ele tem acesso limitado ao hardware e depende do modo núcleo para realizar operações de E/S e outras funções privilegiadas.
### Como o  [[Modo Kernel]] e o [[ Modo Usuário]] se comunicam?
A comunicação entre o modo usuário e o modo kernel é feita através de [[chamadas de sistema]] (system calls). Quando um programa precisa realizar uma operação privilegiada (como ler um arquivo ou acessar a rede), ele faz uma chamada ao kernel, que executa a operação e retorna o resultado.

#### **Exemplo de Chamada de Sistema:**

> [!Exemplo de SysCall]
> 1. Um programa em modo usuário tenta abrir um arquivo.  
> 2. Ele faz uma chamada de sistema (ex: `open()`).
> 3. O kernel, em modo supervisor, acessa o disco e abre o arquivo.
> 4. O resultado é retornado ao programa em modo usuário.

## O sistema Operacional como Gerenciador de Recursos
### Multiplexação no tempo e espaço
Multiplexação é uma técnica usada pelo sistema operacional para compartilhar recursos de hardware (como CPU, memória e dispositivos) entre vários processos ou usuários. Existem duas formas principais de multiplexação: **no tempo** e **no espaço**.
%% Multiplexação é como "dividir" um recurso limitado (ex: CPU, memória) entre vários processos ou usuários, de forma que todos possam usá-lo de maneira eficiente. É como se fosse uma festa onde várias pessoas precisam usar o mesmo brinquedo: o sistema operacional organiza quem usa, quando usa e por quanto tempo. %%
#### Multiplexação no Tempo
Na [[multiplexação no tempo]], o recurso é compartilhado **alternando seu uso** entre os processos. Ou seja, cada processo usa o recurso por um período de tempo e depois "passa a vez" para outro processo.

#### **Exemplo Prático:**

Imagine que você tem uma única CPU e três processos (A, B e C) querendo executar tarefas. Como a CPU só pode executar um processo por vez, o sistema operacional divide o tempo da CPU em pequenos intervalos (chamados de **[[time slices]]** ou fatias de tempo) e alterna entre os processos.

- **Processo A** usa a CPU por 10 ms.
- **Processo B** usa a CPU por 10 ms.
- **Processo C** usa a CPU por 10 ms.
- Depois, volta para o **Processo A**, e assim por diante.
#### Multiplexação no Espaço
Na [[multiplexação no espaço]], o recurso é **dividido em partes**, e cada processo recebe uma parte para usar ao mesmo tempo. Ou seja, o recurso é compartilhado "fisicamente".

#### **Exemplo Prático:**

Imagine que você tem uma memória RAM de 8 GB e três processos (A, B e C) que precisam de memória. O sistema operacional divide a memória em partes e aloca uma parte para cada processo:

- **Processo A** recebe 3 GB.
- **Processo B** recebe 2 GB.
- **Processo C** recebe 3 GB.
Todos os processos usam a memória ao mesmo tempo, mas cada um só acessa a parte que foi alocada para ele.
___
___

## Hardware
### Processadores
 CPU (Central Processing Unit) é responsável por buscar instruções da memória e executá-las. O ciclo básico da CPU é:

> [!CicloCPU]
>  **Busca (Fetch):**  
>     A CPU busca a próxima instrução na memória.
> **Decodificação (Decode):**  
>     A CPU interpreta a instrução para saber o que precisa fazer.
>  **Execução (Execute):**  
>     A CPU realiza a operação indicada pela instrução.
> 

Esse ciclo é repetido indefinidamente, permitindo que a CPU execute uma instrução após a outra.
### Registradores
Registradores são pequenas unidades de memória **ultrarrápidas** localizadas diretamente dentro da CPU. para armazenar variáveis e resultados temporários. O conjunto de instruções geralmente inclui instruções para carregar e armazenar dados entre a memória e os registradores. Como estão dentro da CPU, o acesso a eles é muito mais rápido do que à memória RAM.
#### Registradores Especiais
Além dos registradores gerais, a maioria dos computadores possui registradores especiais que são visíveis ao programador. Entre eles estão:

- **Contador de programa:** Contém o endereço de memória da próxima instrução a ser buscada.
- **Ponteiro de pilha:** Aponta para o topo da pilha atual na memória.
- **PSW (Program Status Word):** Contém os bits do código de condições, prioridade da CPU, modo de execução (usuário ou núcleo) e outros bits de controle.
### Multithreading
O **multithreading** (ou multitarefa com threads) é uma técnica que permite que um **único núcleo de processador** execute **várias threads** simultaneamente. Uma **thread** é uma unidade básica de execução de um programa, como uma "linha de execução" que realiza tarefas específicas.

#### Como Funciona?

- O processador alterna rapidamente entre as threads, dando a impressão de que estão sendo executadas ao mesmo tempo.
- Isso é possível porque o sistema operacional e a CPU gerenciam o tempo de execução de cada thread.
### Multinúcleo
O **multinúcleo** é uma técnica que coloca **vários núcleos de processamento** em um único chip. Cada núcleo é como uma CPU independente, capaz de executar instruções simultaneamente.
#### Como Funciona?

- Cada núcleo pode executar uma thread diferente ao mesmo tempo.
- Se um processador tem 4 núcleos, ele pode executar 4 threads simultaneamente, sem precisar alternar entre elas.
## Hierarquia de Camadas de Memória
Os diferentes tipos de memória em um sistema computacional, ordenados por **velocidade**, **custo** e **capacidade**. Ela existe porque não é possível ter uma memória que seja ao mesmo tempo rápida, barata e com grande capacidade. Por isso, os sistemas usam vários níveis de memória, cada um com suas características, para equilibrar desempenho e custo.
### Níveis de Hierarquia de Memória
A hierarquia de memória é organizada em camadas, da mais rápida (e cara) para a mais lenta (e barata):

1. **[[Registradores]]**
2. **[[Cache (L1, L2, L3)]]**
3. **[[Memória Principal (RAM)]]**
4. **[[Memória Secundária (HD, SSD)]]**
5. **[[Memória Terciária (Fitas, Armazenamento em Nuvem)]]**
**Dados Frequentemente Usados:**
    
- Ficam nos registradores e no cache, para acesso rápido.  
1. **Dados em Uso Ativo:**
    - Ficam na memória RAM.
2. **Dados Permanentes:**
    - Ficam na memória secundária (HD ou SSD).
3. **Dados de Backup:**
    - Ficam na memória terciária (fitas ou nuvem).

## Dispositivos de E/S
Os dispositivos de entrada capturam dados, esses dados são enviados para o computador onde serão processados. Já os dispositivos de saída recebe os dados do computador e apresenta os dados para o usuário.
![[Pasted image 20250228141442.png]]
___
___
### Sistemas Operacionais Monolíticos
Um sistema operacional monolítico é um tipo de arquitetura onde **todo o sistema operacional** é implementado como um único programa executando no modo kernel. Isso significa que todas as funcionalidades do sistema (gerenciamento de memória, processos, arquivos, dispositivos, etc.) estão agrupadas em um único bloco de código.
1. **Código Único:**  
    Todas as funcionalidades do sistema operacional estão no mesmo espaço de memória e são executadas no modo kernel.
2. **Comunicação Direta:**  
    As diferentes partes do sistema operacional se comunicam diretamente, sem camadas intermediárias.
3. **Desempenho:**  
    Como não há overhead (custo adicional) de comunicação entre módulos, o desempenho tende a ser alto.
4. **Complexidade:**  
    O código é grande e complexo, o que pode dificultar a manutenção e a depuração.
5. **Falta de Isolamento:**  
    Um erro em uma parte do sistema pode afetar todo o sistema operacional.

## Sistemas Operacionais de Micronúcleo
Um sistema operacional micronúcleo é uma arquitetura onde o **kernel** (núcleo do sistema) é mantido o menor possível, contendo apenas as funcionalidades essenciais. As demais funcionalidades do sistema operacional (como gerenciamento de memória, processos, arquivos e dispositivos) são implementadas como **serviços independentes** que rodam no **modo usuário**, fora do kernel.
1. **Kernel Mínimo:**  
    O kernel contém apenas as funcionalidades essenciais, como gerenciamento de processos básico, comunicação entre processos e gerenciamento de memória mínima.
2. **Serviços em Modo Usuário:**  
    Funcionalidades como gerenciamento de arquivos, drivers de dispositivos e protocolos de rede são implementadas como serviços independentes que rodam no modo usuário.
3. **Comunicação entre Processos (IPC):**  
    Os serviços se comunicam entre si e com o kernel através de **mecanismos de IPC** (Inter-Process Communication).
4. **Modularidade:**  
    Cada serviço é um módulo independente, o que facilita a manutenção, atualização e substituição.
5. **Segurança:**  
    Como a maioria dos serviços roda no modo usuário, um erro ou falha em um serviço não afeta o kernel ou outros serviços.
