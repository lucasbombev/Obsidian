tags: #Faculdade #Concurso 
___
## Dispositivos de Bloco e de caractere

Comumente os dispositivos de entrada e saída são divididos em dois grandes grupos [[dispositivos de bloco]] e [[dispositivos de caractere]] essa divisão diz respeito a forma como os dispositivos transferem dados.

### Dispositivos de Bloco
São dispositivos que transferem dados em **blocos de tamanho fixo** (geralmente múltiplos de 512 bytes, 1 KB, 4 KB, etc.). Eles permitem acesso aleatório (não sequencial) aos dados e são comumente usados para armazenamento.

 **Características:**

✅ **Acesso aleatório** – Os dados podem ser lidos/escritos em qualquer posição.  
✅ **Bufferização** – Usam cache para melhor desempenho.  
✅ **Operações em blocos** – Transferem vários bytes de uma vez.

**Exemplos:**

- **HDDs (Discos Rígidos)**
- **SSDs (Unidades de Estado Sólido)**
- **Pendrives (Memórias USB)**
- **CDs/DVDs/Blu-rays**

### Dispositivos de Caractere/Serial

São dispositivos que transferem dados **um caractere (byte) por vez**, em um fluxo contínuo (sequencial). Eles não suportam acesso aleatório e são usados para comunicação em tempo real.

 **Características:**

✅ **Acesso sequencial** – Os dados são lidos/escritos em ordem.  
✅ **Sem bufferização** (em muitos casos) – Dados são processados imediatamente.  
✅ **Baixa latência** – Ideais para interação em tempo real.

 **Exemplos:**

- **Teclados** (cada tecla pressionada envia um caractere)
- **Mouses** (movimentos são enviados como sequências de bytes)
- **Interfaces seriais (RS-232, UART)**
- **Impressoras matriciais** (antigas, que imprimem caractere por caractere)
- **Modems antigos** (transmissão serial)
**Funcionamento:**

- Um programa lê os dados conforme são recebidos (ex.: terminal de texto).
- Não é possível "pular" para uma posição específica (como em um arquivo em disco).

![[Pasted image 20250419083336.png]]
___
## Controladores de Dispositivos
Unidades de E/S consistem, em geral, de um componente mecânico e um componente eletrônico. É possível separar as duas porções para permitir um projeto mais modular e geral. O componente eletrônico é chamado de controlador do dispositivo ou adaptador. Já o componente mecânico é o dispositivo em si. A função do controlador é converter o fluxo serial de bits em um bloco de bytes, assim como realizar qualquer correção de erros necessária.

![[Pasted image 20250419083829.png]]

## Mapeamento de E/S na memória

Cada controlador tem alguns registradores que são usados para comunicar-se com a CPU. Ao escrever nesses registradores, o sistema operacional pode comandar o dispositivo a fornecer e aceitar dados, ligar-se e desligar-se, ou de outra maneira realizar alguma ação. Além dos registradores de controle, muitos dispositivos têm um buffer de dados a partir do qual o sistema. A questão que surge então é como a CPU se comunica com os registradores de controle e também com os buffers de dados do dispositivo operacional pode ler e escrever e para cada registrador de controle é designado um número de porta de E/S, um inteiro de 8 ou 16 bits. Dessa forma, as portas de E/S formam o espaço de E/S, que é protegido de maneira que programas de usuário comuns não consigam acessá-lo (apenas o sistema operacional). Outra possibilidade é mapear todos os registradores de controle no espaço da memória, como mostrado na Figura 5.2(b). Para cada registrador de controle é designado um endereço de memória único para o qual nenhuma memória é designada. Esse sistema é **chamado de E/S mapeada na memória como por ser visto da Figura**
![[Pasted image 20250419085831.png]]

A E/S mapeada na memória simplifica a comunicação entre a CPU e os dispositivos, fazendo com que os registradores de controle e buffers de dados dos aparelhos pareçam ser apenas mais alguns locais na memória do computador. Isso torna o processo de controle e troca de dados mais uniforme para o sistema operacional.

___
## Interrupções em Dispositivos E/S

Quando um dispositivo de **entrada/saída** (como um teclado, mouse ou disco rígido) precisa se comunicar com a CPU, ele não fica esperando eternamente por uma resposta. Em vez disso, ele **"interrompe"** a CPU para avisar que algo aconteceu. Isso é chamado de **interrupção de E/S**.

O dispositivo de hardware envia um sinal para a CPU avisando que:
✔ Um dado está pronto para ser lido (ex.: tecla pressionada no teclado).  
✔ Uma operação terminou (ex.: impressora concluiu um trabalho).  
✔ Ocorreu um erro (ex.: disco não encontrado).

1️⃣ **Dispositivo envia um sinal de interrupção** para a CPU.  
2️⃣ **CPU pausa o programa atual** e salva seu estado (registradores).  
3️⃣ **CPU executa o tratador de interrupção** (rotina do SO ou driver).  
4️⃣ **Tratador lida com o dispositivo** (lê dados, verifica erros, etc.).  
5️⃣ **CPU retorna ao programa original** como se nada tivesse acontecido.

___
## Realização de E/S
Quando um dispositivo (teclado, disco, impressora, etc.) precisa se comunicar com a CPU, existem **três métodos principais**:

1. **E/S Programada (Polling)** → CPU fica perguntando: "Você terminou?"
2. **E/S Orientada a Interrupções** → Dispositivo avisa: "Terminei!"
3. **DMA (Acesso Direto à Memória)** → Dispositivo fala **diretamente** com a memória, sem incomodar a CPU.
### E/S Programada
- A CPU **fica verificando** o status do dispositivo em loop.
- pouco eficiente o CPU está sempre em uso
- lento, pois o CPU não faz nada util enquanto espera

### E/S orientada a interrupções

- O dispositivo **avisa a CPU** quando está pronto (via interrupção).
- A CPU pode fazer outras coisas enquanto espera.
- Exemplo:
- Você digita no teclado → gera uma interrupção → CPU trata o input.
**Prós e Contras**

✅ **Eficiente** (CPU não fica esperando).  
✅ **Melhor para multitarefa**.  
❌ **Ainda usa CPU** para transferir dados.

**Usado em:** Teclados, mouses, dispositivos que não transferem grandes volumes.

### DMA - Direct Memory Acess

- O dispositivo **acessa a memória RAM diretamente**, sem passar pela CPU.
- Só interrompe a CPU quando terminar.
- Exemplo:
    - Um SSD copia dados para a RAM via DMA → avisa a CPU depois. 

 **Prós e Contras**

✅ **Super rápido** (CPU não é envolvida na transferência).  
✅ **Libera a CPU** para outras tarefas.  
❌ **Mais complexo** (precisa de um controlador DMA).

**Usado em:** Discos, placas de rede, transferência de dados em alta velocidade.

___
## Camadas do Software E/S
Em relação a entrada e saída, o software de E/S pode ser organizado em quatro camadas, como mostrado na Figura 3. Cada camada tem uma função bem definida a desempenhar e uma interface bem definida para as camadas adjacentes. A funcionalidade e as interfaces diferem de sistema para sistema; portanto, a discussão que se segue, que examina todas as camadas começando de baixo, não é específica para uma máquina.

![[Pasted image 20250419144003.png]]

Os **tratadores de interrupção** são como sentinelas ágeis em um sistema operacional, prontos para responder a qualquer sinal de emergência dos dispositivos de E/S. Quando um dispositivo precisa de atenção imediata, ele envia um sinal de interrupção, e esses tratadores entram em ação. Sua missão é gerenciar esses eventos inesperados e informar ao sistema operacional que é hora de agir.

Por outro lado, os **drivers de dispositivo** são os tradutores poliglotas do mundo da computação. Eles pegam as desvantagens do sistema operacional - que fala uma língua geral de comandos - e as convertem em dialetos específicos que o hardware pode entender. Graças a eles, o sistema operacional pode se comunicar suavemente com uma variedade de dispositivos, desde impressoras até teclados, garantindo uma interação eficiente e harmoniosa. Quanto ao software do **sistema operacional independente do dispositivo (DID)**, pense nele como um camaleão. Ele se adapta a qualquer ambiente de hardware, fornecendo uma interface consistente para os drivers de dispositivo. Isso simplifica enormemente o desenvolvimento de novos drivers e permite que o mesmo software seja usado em diferentes tipos de hardware sem problemas.  

Finalmente, o **software de E/S no espaço do usuário** é uma ponte entre o usuário e o vasto oceano de hardware. Ele permite que aplicativos acessem dispositivos de E/S por meio de APIs fornecidas pelo sistema operacional, oferecendo uma interface amigável que torna a interação com o hardware uma brisa para qualquer usuário.