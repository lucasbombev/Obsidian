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
## Hardware
### Processadores
