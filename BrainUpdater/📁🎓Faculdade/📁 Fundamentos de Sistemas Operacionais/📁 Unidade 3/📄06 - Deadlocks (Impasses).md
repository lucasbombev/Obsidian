tags: #Faculdade #Concurso 
___
# O que é um Deadlock?
Um **deadlock** (ou **impasse**) é uma situação indesejável em sistemas operacionais onde dois ou mais processos ficam bloqueados permanentemente, cada um esperando por um recurso que está sendo mantido por outro processo no conjunto.

> Cada processo espera que outro libere um recurso, mas ninguém libera nada.

É um problema clássico em sistemas concorrentes e requer mecanismos para prevenção, detecção ou recuperação.
___
## Recursos
Os processos precisam ter acesso a determinados recursos, logo, uma classe importante de impasses envolve recursos para os quais algum processo teve acesso exclusivo concedido. Esses recursos incluem dispositivos, registros de dados, arquivos e assim por diante. Apesar de outros exemplos, vamos definir um recurso como um dispositivo de hardware ou software que precisa ser adquirido, usado e liberado com o passar do tempo.

Neste ponto, podemos classificar os recursos como preemptivas e não preemptivas
![[Pasted image 20250530105956.png]]


___
### Condições Necessárias para um Deadlock (Condições de Coffman)

Para que ocorra um deadlock, quatro condições devem ser satisfeitas simultaneamente:

1. **Exclusão Mútua(Mutex)**: Pelo menos um recurso deve ser mantido em modo não compartilhável (apenas um processo por vez pode usar o recurso).
    
2. **Hold and Wait(Posse e Espera)**: Um processo deve estar segurando pelo menos um recurso e esperando para adquirir outros recursos mantidos por outros processos.
    
3. **Não Preempção**: Recursos não podem ser retirados à força; só são liberados voluntariamente pelo processo.
    
4. **Espera Circular**: Deve existir um ciclo de processos onde cada um está esperando por um recurso mantido pelo próximo no ciclo.
    

Se qualquer uma dessas condições não for atendida, o deadlock não ocorre.
![[Pasted image 20250530165043.png]]

___

## Estratégias Para Lidar com Deadlocks

### Ignorar o problema
- Usado em sistemas onde deadlocks são raros.
- Filosofia do “deixa quieto” (Ex: maioria dos sistemas Unix/Linux).  <- segundo o GPT. Suspect...
### Detecção e Recuperação de Deadlocks

Nesta estratégia, o sistema não tenta evitar a ocorrência dos impasses. Em vez disso, ele os deixa ocorrer, tenta detectá-los quando acontecem e então toma alguma medida para recuperar-se após o fato.

