Tags: #Faculdade #Lógica 
___
## O que é um Processo?
Um Processo é a instância de um programa em execução. Ele inclui:
- Código do programa
- Memória alocada -> Cada processo tem sua própria área de memória, isolada de outros processos.
- Recursos alocados -> O sistema operacional gerencia recursos como CPU, Arquivos e dispositivos de I/O
- Estado de execução -> Pronto, Em Execução, Bloqueado
**Exemplo**
Quando você abre um navegador e um editor de texto, cada um é um processo separado. Eles não compartilham memória diretamente e são gerenciados independentemente pelo sistema operacional.

## Criação de Processos
Existem quatro eventos principais que desencadeiam a criação de processos:A inicialização do sistema, a execução de uma chamada de sistema, a solicitação de um usuário para criar um novo processo e o início de uma tarefa em lote.
## Término de Processos
Saída normal, erro fatal, saída por erro, terminação por outro processo.
## Hierarquia de Processos
Em muitos sistemas operacionais, como Unix, Linux e Windows, os processos são organizados em uma estrutura hierárquica, onde um processo pode criar outros processos, formando uma relação "pai-filho".
A hierarquia de processo funciona exatamente como uma árvore HTML ou de Banco de Dados.
A hierarquia de processos é uma árvore onde:

- Um processo **pai** cria um ou mais processos **filhos**.
- Cada processo filho pode, por sua vez, criar seus próprios processos filhos, formando uma estrutura em árvore.
- O processo no topo da hierarquia é chamado de **processo raiz** (geralmente o primeiro processo iniciado pelo sistema operacional, como o `init` ou `systemd` em sistemas Unix-like).

___
## O que é uma Thread
Uma **thread** (ou linha de execução) é uma unidade básica de utilização da CPU dentro de um processo. Um processo pode ter uma ou mais threads, que compartilham o mesmo espaço de endereçamento e recursos do processo ao qual pertencem.
Criar e gerenciar uma thread é mais leve do que um processo, pois elas compartilhas o mesmo espaço de endereçamento.
## Threads Podem ser Implementadas no Espaço de Usuário
Threads podem ser implementadas no **espaço do usuário**, sem a necessidade de intervenção do núcleo do sistema operacional. Essa abordagem possibilita a criação de threads em sistemas que não suportam nativamente threads. Por exemplo, uma biblioteca de threads no espaço do usuário pode ser utilizada para implementar threads em um sistema operacional legado.

**Exemplo**
Em um navegador, uma thread pode ser responsável por renderizar a interface gráfica, enquanto outra thread carrega dados da internet. Ambas trabalham juntas para melhorar a responsividade do aplicativo.
![[Pasted image 20250310184223.png]]
**Conclusão**
- **Processo** → Programa em execução, com seu próprio espaço de memória.
- **Thread** → Unidade menor dentro de um processo, compartilhando memória e rodando tarefas em paralelo.
**Sistemas modernos** usam **multithreading** para melhorar o desempenho e a eficiência dos programas.
___
## Comunicação Entre Processos
