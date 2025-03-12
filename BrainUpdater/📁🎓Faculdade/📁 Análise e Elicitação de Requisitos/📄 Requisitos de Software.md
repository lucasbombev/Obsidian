
tags: #Software #Faculdade 
___
## O que é um requisito de software?
Um **requisito de software** é uma descrição do que o sistema deve fazer, como deve se comportar  e quais regras específicas deve seguir . Eles são a base para o desenvolvimento de um software de qualidade, garantindo que ele atenda às necessidades dos usuários e do negócio.
**Requisitos de Usuário:** Expressa requisitos abstratos e de alto nível.
**Requisitos de Sistema/Software:** Expressa descrição detalhada do que o sistema deve fazer.

### Definição de requisitos de usuário e de software:
#### Requisitos de Usuário:
Os **[[requisitos de usuário]]** descrevem as necessidades, expectativas e objetivos dos usuários em relação ao software. Eles são escritos em uma linguagem mais natural e acessível, sem muitos detalhes técnico.
focam no **"o que"** o sistema deve fazer, não no **"como"** e são direcionados para pessoas que não tem conhecimento técnico pois são voltados para os stakeholders (usuários finais, clientes, etc.)

#### Requisitos de Software:
Os **[[requisitos de software]]** são uma especificação detalhada e técnica do que o sistema deve fazer. Eles são derivados dos requisitos de usuário, mas são mais precisos, claros e voltados para a equipe de desenvolvimento.
São de baixo nível e focam no **"como"** um sistema deve funcionar.
![[Pasted image 20250224235540.png]]Os requisitos precisam ser escritos em diferentes níveis de detalhamento para que diferentes leitores possam usá-los de diversas maneiras. A Figura a seguir mostra possíveis leitores dos requisitos de usuário e de sistema.
![[Pasted image 20250224235734.png]]
___
## Requisitos Funcionais e Não Funcionais
### Requisitos Funcionais 
[[Requisitos Funcionais]] são as funcionalidades que o sistema deve ter, ou seja, **o que o sistema deve fazer**. Eles descrevem as ações que o sistema precisa realizar para atender às necessidades dos usuários.
Em resumo, os requisitos funcionais são como as "tarefas" que o sistema precisa executar.
### Requisitos Não Funcionais
 [[Requisitos não funcionais]] são as características que definem **como o sistema deve funcionar.** restrições aos serviços ou funções, ou seja, a qualidade, desempenho, segurança e outras propriedades do sistema. Eles não descrevem funcionalidades, mas sim **como essas funcionalidades devem se comportar**.
#### Exemplos de requisitos não funcionais:

- **Desempenho**:
    - O sistema deve carregar uma página em menos de 3 segundos. 
    - O aplicativo deve suportar 1.000 usuários simultaneamente.
- **Segurança**:
	- O sistema deve criptografar todos os dados do usuário.
    - O login deve exigir autenticação de dois fatores.
Em resumo, os requisitos não funcionais são como as "regras de qualidade" que o sistema precisa seguir.

%%Na realidade, a distinção entre diferentes tipos de requisitos não é tão clara como sugerem essas definições simples. Um requisito de usuário relacionado com a proteção, tal como uma declaração de limitação de acesso a usuários autorizados, pode parecer um requisito não funcional. No entanto, quando desenvolvido em mais detalhes, esse requisito pode gerar outros requisitos, claramente funcionais, como a necessidade de incluir recursos de autenticação de usuário no sistema.
Isso mostra que os requisitos não são independentes e que muitas vezes geram ou restringem outros requisitos.%%


Sempre que possível, os requisitos não funcionais devem ser escritos quantitativamente, para que possam ser objetivamente testados.![[Pasted image 20250225025245.png]]
