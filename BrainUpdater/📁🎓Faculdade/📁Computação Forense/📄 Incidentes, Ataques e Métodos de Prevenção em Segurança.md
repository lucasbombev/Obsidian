#Faculdade #Forense #Software 
___
## O que é um incidente de segurança?
Um incidente de segurança é qualquer evento ou ação que possa prejudicar a segurança de um sistema. esse evento não necessariamente é deliberado.

exemplo: uma falha crítica na biblioteca OpenSSL, que permitia a leitura de informações sensíveis da memória de servidores vulneráveis.
## O que é um ataque de segurança
Um ataque é uma ação deliberada, geralmente com a intenção de explorar vulnerabilidades em sistemas. Entre os ataques mais comuns estão os de negação de serviço (DDoS), phishing, malware, ransomware e roubo de dados.
## Classificação dos Principais Tipo de Ataques
### Phishing
Tentativas de enganar usuários para que revelem informações sensíveis, como senhas e números de cartões de crédito.
e-mail fake, site fake, sms, etc...
![[Pasted image 20250313194329.png]]
### Malware
Software malicioso projetado para causar danos ou obter acesso não autorizado a sistemas.
 -> Programas infectados, prendrives com autorun, keylogger, vírus, rootkit, cavalo de troia, backdoor, worm, spyware... o malware é o termo genérico.
### Ransomware
Um tipo específico de malware que criptografa os dados da vítima, exigindo pagamento para liberar o acesso.
### Ataques DDoS (Distributed Denial of Service)
Sobrecarregam um sistema ou rede com uma quantidade massiva de tráfego, tornando-o inacessível aos usuários legítimos.
![[Pasted image 20250313200006.png]]
Hoje dispositivos IOT como câmeras, aspiradores inteligentes, lâmpadas são muito usadas em BOTNET para ataques DDOS.

Cada um desses ataques explora vulnerabilidades específicas, sendo fundamental que os profissionais de segurança entendam os vetores de ataque e as formas de defesa adequadas.

 ___
## Métodos de Prevenção
Prevenir ataques cibernéticos exige a aplicação de múltiplas camadas de segurança. Listamos alguns dos métodos mais eficazes:

- **Criptografia:** Protege os dados em trânsito e em repouso, assegurando que apenas partes autorizadas possam acessá-los.
- **Políticas de Senhas Fortes:** Exigir senhas complexas e mudanças regulares pode reduzir significativamente o risco de ataques de força bruta.
- **Autenticação Multifator (MFA):** Adiciona uma camada extra de segurança, exigindo mais de um método de verificação para acessar sistemas críticos.
- **Firewalls e Sistemas de Detecção de Intrusão (IDS/IPS):** Monitoram o tráfego da rede em busca de atividades suspeitas, bloqueando ataques antes que possam causar danos.
- **Backup Regular de Dados:** Em casos de ataques de [[ransomware]], backups atualizados podem ser fundamentais para recuperar informações sem pagar o resgate. -> [[snapshots]]
O uso combinado dessas práticas pode reduzir a superfície de ataque e aumentar a resiliência dos sistemas contra tentativas de invasão.
## Respostas a Incidentes de Segurança
É inevitável que, em algum momento, incidentes de segurança ocorram. No entanto, a forma como uma organização responde a esses incidentes pode fazer toda a diferença. As etapas principais de uma resposta a incidentes incluem:

- **Detecção:** Identificar rapidamente o incidente e determinar sua gravidade.
- **Contenção:** Isolar o sistema afetado para evitar a propagação do ataque.
- **Erradicação:** Remover completamente o malware ou outra ameaça.
- **Recuperação:** Restaurar o sistema a um estado seguro e reavaliar as vulnerabilidades.
- **Revisão pós-incidente:** Documentar o incidente e implementar medidas para prevenir recorrências.
Uma resposta eficiente pode minimizar os danos e restaurar a confiança nos sistemas de informação.
___
## Conteúdo extra
lido no capítulo 1.3 do livro "criptografia e segurança de redes princípios e práticas"
## Ataques Passivos X Ataques Ativos
Uma maneira útil de classificar os ataques à segurança, usada tanto na X.800 quanto na RFC 4949, é em termos de ataques passivos e ataques ativos (Figura 1.1). Um ataque passivo tenta descobrir ou utilizar informações do sistema, mas não afeta os seus recursos. Um ataque ativo tenta alterar recursos do sistema ou afetar sua operação.
![[Pasted image 20250313202648.png]]
### Ataques passivos
#### Vazemento de Conteúdo (mais grave)
Os ataques passivos (Figura 1.1a) estão na natureza de monitorar transmissões. O objetivo do oponente é obter informações que estão sendo transmitidas. Dois tipos de ataques passivos são vazamento de conteúdo de mensagem e análise de tráfego.
O vazamento de conteúdo de mensagem é facilmente compreendido. Uma conversa telefônica, uma mensagem de correio eletrônico e um arquivo transferido podem conter informações, sensíveis ou confidenciais.

#### Análise de Trafego
a análise de tráfego, é mais sutil. Suponha que tivéssemos uma maneira de disfarçar o conteúdo das mensagens ou outro tráfego de informações, de modo que os oponentes, mesmo que capturassem a mensagem, não pudessem extrair as informações dela. A técnica comum para mascarar o conteúdo é a encriptação. Se tivéssemos proteção por encriptação, um oponente ainda poderia conseguir observar o padrão dessas mensagens. Ele teria meios para determinar o local e a identidade dos interlocutores em comunicação e poderia observar a frequência e o tamanho das mensagens trocadas. Essa informação seria útil para descobrir a natureza da comunicação que estivesse ocorrendo.

Ataques passivos são muito difíceis de se detectar, pois não envolvem qualquer alteração dos dados. Em geral, o tráfego de mensagens é enviado e recebido em um padrão aparentemente normal, e nem o emissor nem o receptor estão cientes de que um terceiro leu as mensagens ou observou o padrão de tráfego. Porém, é viável impedir o sucesso desses ataques, normalmente por meio da encriptação. Assim, a ênfase em lidar com ataques passivos está na prevenção, em vez de na detecção.
#### Técnicas Utilizadas para Detectar Invasores na Rede
#####  Análise de Comportamento de Usuários e Sistemas

- **UEBA (User and Entity Behavior Analytics)**: Use soluções de análise de comportamento para detectar atividades incomuns, como acesso a grandes volumes de dados ou conexões a servidores desconhecidos.
- **Logs de Auditoria**: Revise regularmente logs de acesso e atividades para identificar padrões suspeitos.
##### Monitoramento de Tráfego Anômalo

- **Análise de Padrões**: Ferramentas de monitoramento de rede, como IDS (Sistemas de Detecção de Intrusão) ou SIEM (Security Information and Event Management), podem identificar padrões incomuns de tráfego que possam indicar vazamento de dados ou análise de tráfego. 
- **Detecção de Vazamentos**: Monitore o tráfego de saída para identificar grandes volumes de dados sendo enviados para destinos desconhecidos ou suspeitos.

### Ataques Ativos
Ataques ativos (Figura 1.1b) envolvem alguma modificação do fluxo de dados ou a criação de um fluxo falso, e podem ser subdivididos em quatro categorias: disfarce, repasse, modificação de mensagens e negação de serviço.

#### Disfarce 
Um disfarce ocorre quando uma entidade finge ser outra diferente (o caminho 2 da Figura 1.1b é ativo). Um ataque de disfarce normalmente inclui uma das outras formas de ataque ativo. Por exemplo, sequências de autenticação podem ser capturadas e reproduzidas depois que houver uma delas, válida, permitindo assim que uma entidade autorizada com poucos privilégios obtenha alguns extras, personificando uma que os tenha.
#### Repasse
Repasse envolve a captura passiva de uma unidade de dados e sua subsequente retransmissão para produzir um efeito não autorizado
#### Modificação de Mensagens
Modificação de mensagens simplesmente significa que alguma parte de uma mensagem legítima é alterada, ou que as mensagens são adiadas ou reordenadas, para produzir um efeito não autorizado
Por exemplo, uma mensagem significando “Permitir que John Smith leia o arquivo confidencial contas” é modificada para “Permitir que Fred Brown leia o arquivo confidencial contas”
#### Negação de Serviços
A negação de serviço impede ou inibe o uso ou gerenciamento normal das instalações de comunicação (caminho 3 ativo). Esse ataque pode ter um alvo específico; por exemplo, uma entidade a suprimir todas as mensagens dirigidas para determinado destino (por exemplo, o serviço de auditoria de segurança). Outra forma de negação de serviço é a perturbação de uma rede inteira, seja desativando-a ou sobrecarregando-a com mensagens, a fim de prejudicar seu desempenho.
