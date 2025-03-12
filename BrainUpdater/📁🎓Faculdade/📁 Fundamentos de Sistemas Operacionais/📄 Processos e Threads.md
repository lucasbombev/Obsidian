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
Como processos são isolados uns dos outros (cada um tem seu próprio espaço de endereçamento), o sistema operacional fornece métodos para que eles possam se comunicar de forma segura e eficiente.
### Pipes

**Pipes** são canais de comunicação unidirecionais que permitem a transferência de dados entre processos. Eles são frequentemente usados para comunicação entre processos relacionados (por exemplo, processos pai e filho).

#### Tipos de Pipes:

1. **Pipes Anônimos**:
    - Criados com a chamada de sistema `pipe()`.
    - São unidirecionais e só podem ser usados por processos relacionados (com ancestral comum)        
2. **Pipes Nomeados (FIFOs)**:
    - São arquivos especiais no sistema de arquivos.
    - Podem ser usados por processos não relacionados
#### Vantagens:
- Simples e eficiente para comunicação unidirecional
#### Desvantagens:
- Limitado a comunicação unidirecional (para comunicação bidirecional, são necessários dois pipes).
#### Exemplo:
Um processo envia a saída de um comando para outro processo usando um pipe (por exemplo, `ls | grep arquivo`).

## Condições de Corrida
Uma condição de corrida ocorre quando dois ou mais processos/threads acessam um recurso compartilhado.
### Exemplo Clássico
Considere o seguinte cenário, onde dois processos (P1 e P2) tentam incrementar uma variável compartilhada `x` (inicialmente `x = 0`):

1. **Processo P1**:
    
    - Lê o valor de `x` (valor lido: 0).
    - Incrementa o valor lido (`0 + 1 = 1`).
    - Escreve o novo valor de `x` (agora `x = 1`).
2. **Processo P2**:
    - Lê o valor de `x` (valor lido: 0).
    - Incrementa o valor lido (`0 + 1 = 1`).
    - Escreve o novo valor de `x` (agora `x = 1`).
#### Resultado Esperado:

Se os processos fossem executados de forma sequencial, o valor final de `x` seria 2.
#### Resultado com Condição de Corrida:

Como P1 e P2 executam simultaneamente, ambos podem ler o valor de `x` antes que qualquer um deles escreva o novo valor. Nesse caso, o valor final de `x` será 1, o que é incorreto.
## Como evitar Condições de Corrida?
- Mutexes: Um mutex permite que apenas um processo/thread acesse um recurso por vez
- Semáforos: um semáforo controla um recurso compartilhado, permitindo que um número limitado de processos acesse o recurso por vez.
- Monitor
### Algoritmo de Peterson
O **Algoritmo de Peterson** é uma solução clássica para o problema da **exclusão mútua** em sistemas com dois processos ou threads. Ele permite que dois processos compartilhem um recurso crítico (como uma variável ou dispositivo) de forma segura, garantindo que apenas um processo por vez acesse o recurso. O algoritmo foi proposto por Gary L. Peterson em 1981 e é amplamente estudado como um exemplo de como resolver problemas de concorrência sem usar primitivas de hardware complexas.
 Ele é baseado em três ideias principais:

1. **Interesse**: Cada processo indica seu interesse em entrar na seção crítica.
2. **Vez**: Um processo "cede a vez" ao outro, garantindo que ambos não entrem na seção crítica ao mesmo tempo.
3. **Espera ocupada (busy-wait)**: O processo que não está na seção crítica fica em um loop verificando se pode entrar.
**Exemplo de Algoritimo de Peterson implantado em Python**
```python
import threading

# Variáveis compartilhadas
flag = [False, False]  # Indica o interesse de cada thread
turn = 0  # Indica de quem é a vez

def process0():
    while True:
        flag[0] = True  # Thread 0 quer entrar na seção crítica
        turn = 1  # Cede a vez à Thread 1
        while flag[1] and turn == 1:
            # Espera ocupada: Thread 1 está na seção crítica ou quer entrar
            pass
        # Seção crítica
        print("Thread 0 está na seção crítica.")
        # Fim da seção crítica
        flag[0] = False  # Thread 0 sai da seção crítica

def process1():
    while True:
        flag[1] = True  # Thread 1 quer entrar na seção crítica
        turn = 0  # Cede a vez à Thread 0
        while flag[0] and turn == 0:
            # Espera ocupada: Thread 0 está na seção crítica ou quer entrar
            pass
        # Seção crítica
        print("Thread 1 está na seção crítica.")
        # Fim da seção crítica
        flag[1] = False  # Thread 1 sai da seção crítica

# Cria as threads
thread0 = threading.Thread(target=process0)
thread1 = threading.Thread(target=process1)

# Inicia as threads
thread0.start()
thread1.start()

# Aguarda as threads terminarem (nunca acontecerá neste exemplo)
thread0.join()
```
___
## O que é um semáforo?
Um semáforo é uma ferramenta usada em sistemas operacionais para controlar o acesso a recursos compartilhados entre várias tarefas ou processos.
### Como Funciona?
Um semáforo é como um contador. Ele tem um valor numérico que indica quantos processos podem acessar o recurso ao mesmo tempo. Esse valor pode ser:

- **Maior que zero**: Indica que o recurso está disponível.
- **Igual a zero**: Indica que o recurso está sendo usado e outros processos precisam esperar.
- **Menor que zero**: Indica que há processos esperando para usar o recurso.
### Operações básicas:

**Wait (ou P)**: Quando um processo quer usar o recurso, ele "espera" no semáforo. Se o valor do semáforo for maior que zero, ele diminui o valor e acessa o recurso. Se for zero, o processo fica bloqueado até que o recurso seja liberado.
**Signal (ou V)**: Quando um processo termina de usar o recurso, ele "sinaliza" o semáforo, aumentando seu valor. Isso libera o recurso para outros processos.

## Mutexes
### O que é um mutex?
Um **mutex** (abreviação de *mutual exclusion*, ou exclusão mútua) é uma ferramenta usada em sistemas operacionais para garantir que apenas um processo ou thread (uma parte de um programa) acesse um recurso compartilhado por vez. Ele é como um "cadeado" que protege um recurso para evitar conflitos.

### Como funciona?
O mutex tem dois estados:
1. **Travado (locked)**: Significa que um processo ou thread está usando o recurso. Ninguém mais pode acessá-lo até que ele seja liberado.
	Aconteceu comigo quanto tentei usar DPKG, o linux travou meu DPKG porque provavelmente estava fazendo alguma operação e fez isso para evitar erro.
2. **Destravado (unlocked)**: Significa que o recurso está livre e pode ser usado por outro processo ou thread.

Quando um processo ou thread quer usar o recurso, ele tenta "travar" o mutex. Se o mutex já estiver travado, o processo ou thread precisa esperar até que ele seja liberado.
### Operações básicas:
1. **Lock (travar)**: Quando um processo ou thread quer acessar o recurso, ele tenta travar o mutex. Se o mutex já estiver travado, ele espera.
2. **Unlock (destravar)**: Quando o processo ou thread termina de usar o recurso, ele libera o mutex, permitindo que outros processos ou threads o usem.
### Exemplo prático:
Imagine um banheiro público com uma única porta e uma chave:
- A chave é o **mutex**.
- Se alguém está usando o banheiro, ela pega a chave e trava a porta (lock).
- Enquanto a chave estiver com essa pessoa, ninguém mais pode entrar.
- Quando a pessoa termina, ela devolve a chave (unlock), e outra pessoa pode usar o banheiro.
### Diferença entre mutex e semáforo:
- **Mutex**: É como um cadeado que permite que apenas um processo ou thread acesse o recurso por vez.
- **Semáforo**: É como um contador que permite que um número limitado de processos ou threads acessem o recurso ao mesmo tempo.
___
## Escalonamento
Claro! Vou explicar o conceito de **escalonamento** em sistemas operacionais de forma simples e direta, para que você possa entender sem dificuldade.

---

### O que é escalonamento?
Escalonamento é o processo que o sistema operacional usa para decidir **qual tarefa (processo ou thread)** deve ser executada pelo processador em um determinado momento. Como o processador (CPU) geralmente é único, mas há muitos programas querendo rodar ao mesmo tempo, o sistema operacional precisa gerenciar isso de forma justa e eficiente.

---

### Para que serve?
Imagine que você tem várias tarefas para fazer, como estudar, assistir TV e cozinhar. Você não pode fazer tudo ao mesmo tempo, então precisa decidir o que fazer primeiro, o que deixar para depois e quanto tempo dedicar a cada tarefa. O escalonamento faz isso no computador: ele decide **qual processo deve rodar**, **por quanto tempo** e **em que ordem**.

---

### Como funciona?
O sistema operacional usa um **algoritmo de escalonamento** para tomar essas decisões. Existem vários tipos de algoritmos, mas todos têm o mesmo objetivo: usar o processador da melhor forma possível, garantindo que todos os processos tenham uma chance de rodar.

---

### Tipos comuns de escalonamento:
1. **Escalonamento de processos**:
   - Decide qual processo deve usar a CPU.
   - Exemplos de algoritmos:
     - **First-Come, First-Served (FCFS)**: O primeiro processo que chega é o primeiro a ser executado.
     - **Shortest Job First (SJF)**: O processo que leva menos tempo para ser executado vai primeiro.
     - **Round Robin (RR)**: Cada processo recebe um "tempo de CPU" (quantum) e, quando acaba, passa para o próximo.
     %%Duvida:  COMO O ESCALONADOR FAZ PARA ESCOLHER QUAL DESSES PROFESSOS VAI SER USADO?%%

2. **Escalonamento de threads**:
   - Decide qual thread de um processo deve usar a CPU.
   - É semelhante ao escalonamento de processos, mas focado em threads.

---

### Exemplo prático:
Imagine uma fila de pessoas querendo usar um único caixa eletrônico:
- O **escalonador** é como o segurança que organiza a fila.
- Ele pode decidir:
  - Quem chegou primeiro usa o caixa primeiro (FCFS).
  - Quem tem uma tarefa rápida (como só consultar o saldo) usa primeiro (SJF).
  - Cada pessoa usa o caixa por um tempo limitado e depois volta para o final da fila (Round Robin).

---

### Objetivos do escalonamento:
1. **Justiça**: Garantir que todos os processos tenham uma chance de usar a CPU.
2. **Eficiência**: Usar o processador ao máximo, sem deixá-lo ocioso.
3. **Tempo de resposta**: Garantir que os processos interativos (como um editor de texto) respondam rápido.
4. **Taxa de transferência**: Executar o maior número possível de processos em um determinado tempo.

---

### Resumindo:
Escalonamento é a técnica que o sistema operacional usa para gerenciar o uso da CPU entre vários processos ou threads. Ele decide quem roda, quando e por quanto tempo, garantindo que o sistema funcione de forma eficiente e justa.
