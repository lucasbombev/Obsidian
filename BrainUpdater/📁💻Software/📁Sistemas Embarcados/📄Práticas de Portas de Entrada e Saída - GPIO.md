Tags: #Software #IOT #SistemasEmbarcados #IFRN 
___
Os GPIOs são fundamentais para conectar o mundo digital ao mundo físico.Eles permitem que o microcontrolador interaja com diversos dispositivos e sensores, como LEDs, botões, teclados matriciais, motores e muitos outros componentes..
## Bounce
### O que é o "Bounce?"
Imagine que você tem um botão físico, como aquele de ligar e desligar uma lâmpada. Quando você aperta o botão, ele faz um contato elétrico que envia um sinal para o sistema embarcado (um pequeno computador, como um Arduino ou um microcontrolador). Esse sinal diz ao sistema que o botão foi pressionado.

Agora, aqui está o problema: quando você aperta ou solta o botão, ele não faz um contato perfeito de uma vez só. Em vez disso, ele "trepida" rapidamente por um instante antes de se estabilizar. Essa trepidação é o que chamamos de **efeito bounce**.
![[Pasted image 20250217182618.png]]
### Por que isso acontece?
Isso acontece porque os botões físicos não são perfeitos. Eles são feitos de partes mecânicas que, quando pressionadas, não se conectam imediatamente de forma suave. Em vez disso, há um pequeno período de instabilidade onde o contato elétrico oscila entre ligado e desligado várias vezes em milissegundos.
### O que isso causa em um sistema embarcado?
Se o sistema embarcado estiver monitorando o botão, ele pode interpretar essa trepidação como várias pressões rápidas do botão, em vez de uma única pressão. Por exemplo, se você apertar o botão uma vez, o sistema pode pensar que você apertou várias vezes seguidas, o que pode causar comportamentos indesejados no seu programa.
### Soluções
Para evitar esse tipo de problemas podemos chegar a soluções por hardware ou por software (essas soluções são chamadas de "debouncing"), vejamos:

**Debounce por software**: Aqui, você programa o sistema embarcado para ignorar as oscilações iniciais do botão. Por exemplo, você pode configurar o sistema para esperar alguns milissegundos após a primeira detecção do botão ser pressionado, antes de considerar que o botão foi realmente pressionado. Isso dá tempo para o botão parar de trepidar.

**Debounce por hardware**: Aqui, você adiciona componentes eletrônicos de alta qualidade e  resistores e capacitores ao circuito do botão para "suavizar" o sinal e reduzir a trepidação antes que ele chegue ao sistema embarcado.
___
