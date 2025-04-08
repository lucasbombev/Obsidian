tags: #Faculdade #Forense 
___
# Políticas de Segurança da Informação em Organizações
## O que são?
Segundo a **ISO/IEC 27001:2022 e a ABNT NBR 27001**, a segurança da informação é o conjunto de práticas que visa proteger a **confidencialidade**, **integridade** e **disponibilidade** dos ativos de informação de uma organização. Para que isso seja alcançado, a norma destaca a necessidade de uma **política de segurança da informação**, que funciona como a base para o **Sistema de Gestão de Segurança da Informação (SGSI)**.
## Conceito pela norma
A política de segurança é um documento estratégico de alto nível que estabelece:

- O **compromisso** da organização com a segurança da informação.
- As **expectativas e responsabilidades** de colaboradores, fornecedores e demais partes interessadas.
- Diretrizes que servem como referência para a criação de controles e processos relacionados à proteção de informações.
### Importância da política de segurança - princípios da segurança da informação:

- **Confidencialidade:** Garante que a informação seja acessada apenas por pessoas autorizadas.
- **Integridade:** Protege a informação contra alterações não autorizadas ou acidentais.
- **Disponibilidade:** Assegura que a informação esteja acessível sempre que necessário.

**Exemplo prático:** Uma organização que gerencia sistemas de e-commerce sem uma política clara pode ter dificuldades em controlar acessos e monitorar incidentes, aumentando os riscos de fraudes e violações de privacidade.

## Etapas principais no desenvolvimento (baseadas na norma):

1. **Definição do escopo e contexto**
    
    - Identifique os ativos de informação a serem protegidos, considerando:
        - **Requisitos internos e externos.**
        - **Partes interessadas**, como clientes, fornecedores e órgãos regulatórios.
    - Exemplo: Um sistema web precisa atender à LGPD no Brasil e ao GDPR em países da UE.
2. **Identificação de requisitos legais e normativos**
    
    - Liste as leis, regulamentações e normas aplicáveis, como LGPD, GDPR e os controles da própria ISO 27001.
3. **Estabelecimento de objetivos e controles**
    
    - Defina objetivos claros para garantir a segurança.
    - Relacione esses objetivos aos **114 controles do Anexo A da ISO 27001**, como:
        - Controles de acesso (A.9.1).
        - Gestão de ativos (A.8).
4. **Criação e aprovação da política**
    
    - A política deve conter:
        - Princípios gerais.
        - Expectativas de conformidade.
        - Mecanismos de revisão e atualização.
    - **Dica:** Utilize uma linguagem acessível, mas alinhada aos objetivos estratégicos.
5. **Implementação e conscientização**
    
    - Treine os colaboradores para que compreendam e apliquem a política.
    - Implemente campanhas de **conscientização contínua**, utilizando exemplos práticos de segurança no dia a dia.
6. **Monitoramento e revisão contínua**
    

- Avalie regularmente a eficácia da política.
- Utilize auditorias internas e externas para verificar a conformidade com a ISO 27001.

## Aplicação Pŕatica dos controles da ISO/IEC 27001:2002
#### Controle A.9 - Controle de Acesso

**Descrição:** Restringir o acesso às informações com base na necessidade de conhecimento (principle of least privilege).

- **Exemplo prático em sistemas web:**
    - Desenvolvedores têm acesso apenas às áreas de código-fonte que estão diretamente envolvidos.
    - Administradores de banco de dados podem acessar os dados, mas não as credenciais de autenticação dos usuários finais.
- **Ferramentas para implementar:**
    - Utilização de autenticação multifator (MFA).
    - Logs de auditoria para monitorar quem acessa o quê e quando.

**Impacto positivo:** Redução do risco de acessos não autorizados ou vazamento de dados devido a permissões excessivas.

A Figura 1 ilustra o Controle A.9, aonde cada conta de usuário tem as permissões necessárias de acesso ao sistema, com regras bem definidas.  Para maiores detalhes, clique [aqui](https://www.cert.govt.nz/information-and-advice/critical-controls/principle-of-least-privilege/).
![[Pasted image 20250408171153.png]]
#### **Controle A.12.3 - Backup**
Fonte: Infosec Solutions.

**Descrição:** Assegurar que cópias de segurança sejam realizadas e protegidas contra acessos não autorizados.

- **Exemplo prático em sistemas web:**
    - Backups diários automáticos dos bancos de dados de usuários, armazenados em data centers geograficamente distintos.
    - Dados de backup criptografados com algoritmos robustos (ex.: AES-256) para evitar acessos indevidos.
- **Ferramentas para implementar:**
    - Soluções como AWS Backup, Azure Backup ou Veeam.
    - Testes regulares de restauração para garantir que os backups são funcionais.

**Impacto positivo:** Minimização do impacto de incidentes como ataques de ransomware, permitindo recuperação rápida.
