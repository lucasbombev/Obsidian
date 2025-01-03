Tags: #Software #IOT #SistemasEmbarcados #IFRN

Uidade 5 | Capítulo 1
___
## O que são as IOT?
A Internet das Coisas pode ser entendida como uma rede de objetos físicos, as “coisas”, que interagem com o ambiente e trocam informações pela Internet
Algumas “coisas” já nascem IoT, como os relógios inteligentes usados por muitas pessoas no dia a dia. Outras “coisas” se tornam IoT quando equipadas com sensores e conectividade sem fio, como um sistema de iluminação inteligente.
## Breve histórico das IOT
Não há consenso entre os historiadores mas se olharmos para trás, podemos compreender a história dos objetos conectados desde a criação do primeiro telégrafo em 1832.
o telégrafo marcou o início da comunicação à distância.

Outro marco interessante foi a criação do Apollo Guidance Computer (AGC) em 1965. Este computador digital foi usado no pouso na lua e permitia realizar a computação necessária para controlar e navegar uma nave espacial. As ferramentas e conceitos criados nesse projeto tiveram repercussão em toda a indústria de tecnologia.

Na década de 1970, a criação da telefonia celular e das etiquetas inteligentes RFID revolucionaram a comunicação e o rastreamento de objetos.

Um marco significativo foi a criação do primeiro objeto conectado: uma máquina de refrigerantes na Universidade de Carnegie Mellon.

![[Pasted image 20250102181248.png]]
Na década de 1990, surgiram impressoras, câmeras e sistemas de diagnóstico para automóveis conectados à rede.

## Conceitos e Definições da Internet das Coisas
### O que é um objeto conectado?
Vamos estabelecer alguns requisitos para um objeto conectado. Vamos nos concentrar naquelas “coisas” que uma pessoa comum não imaginaria que possuem conectividade, como seu guarda-chuva, as lâmpadas de sua casa, a porta da sua garagem.

esses objetos terão pouca conectividade e pouquíssimo poder computacional, apenas o suficiente para realizar uma comunicação sem fio de curta distância e compartilhar seus dados.

Provavelmente, eles serão alimentados por baterias e não poderão emitir calor. Claro que haverá exceções.

Embora limitados, eles devem ser capazes de executar uma [[pilha de protocolos]] IP ou, pelo menos, uma pilha de algum protocolo não-IP e usar um dispositivo edge (computador de borda) para se comunicar

#### Exemplo de IOT que usa protocolo não-IP
etiquetas inteligentes que medem o nível de açúcar no sangue.
![[Pasted image 20250102215930.png]]

Esses sensores são muito limitados e não comunicam diretamente com a Internet, normalmente possuem interface Bluetooth e usam um celular como [[dispositivo edge == Computador de Borda]] para enviar os dados para a nuvem.
___
