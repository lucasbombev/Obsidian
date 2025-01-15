Tags: #Software #IOT #SistemasEmbarcados #IFRN

Uidade 6 | Capítulo 6.1
___
## Conceitos Importantes
Essencialmente, um microcontrolador integra em um único chip um sistema de computação compacto, que inclui um ou mais processadores, memória de programa, memória de dados e diversos periféricos dedicados a tarefas de controle e comunicação.

Uma das principais dificuldades reside nas limitações computacionais e de memória desses dispositivos. Ao contrário dos computadores de propósito geral, os microcontroladores possuem poder de processamento e capacidade de memória restritos

Outro ponto importante é que a depuração desses sistemas é frequentemente complexa, pois depende de sua interação com o ambiente físico ou com outros componentes, como motores e conversores de energia.

## BitDogLab: uma ferramenta educacional

A placa possui 40 pinos, incluindo pinos de alimentação, depuração e outros dedicados aos periféricos, como GPIO, UART, SPI, I2C, ADC e PIO.
![[Pasted image 20250114175154.png]]
## RP2040: Um microcontrolador da Raspberry Pi

O RP2040 é um Microcontrolador de baixo custo e alta flexibilidade.
Ele é equipado com dois processador ARM Cortex-M0+ que operam em até 133mhz, além de 256kB de memória RAM.
![[Pasted image 20250114175622.png]]
O RP2040 é equipado com uma ampla gama de periféricos que o tornam altamente atrativo para aplicações embarcadas. Ele inclui interfaces de comunicação serial, como UART, I2C e SPI, que permitem sua integração com outros processadores, sensores e atuadores. A interface PWM é ideal para o controle de motores e outros dispositivos que requerem modulação de largura de pulso.

## O SDK da Raspberry Pi Pico W.
O SDK oferece recursos para que programadores possam criar aplicações em C, C++ e Assembly.
As bibliotecas de alto nível começam com ‘pico_xxx’, onde ‘xxx’ representa o nome da biblioteca.
As bibliotecas de baixo nível, que lidam diretamente com os periféricos e seus registradores, são nomeadas como ‘hardware_xxx’.
