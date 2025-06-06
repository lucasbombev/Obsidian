tags: #Faculdade #Concurso 
___
## O que é?
A virtualização de servidores é como transformar um computador físico (hardware) em vários "computadores virtuais" independentes. Cada um desses computadores virtuais (chamados de **máquinas virtuais**) pode rodar um sistema operacional e aplicações diferentes, como se fossem máquinas separadas.
## Vantagens
1. **Isolamento e tolerância a falhas:** Uma falha em uma máquina virtual não afeta as outras.
2. **Redução de custos:** Reduz custos sobre equipamentos, eletricidade e espaço físico. 
3. **Manutenção Facilitada:** Facilita a migração, testes de novas ideias e execução de softwares legados em sistemas operacionais não suportados.

A virtualização é destacada como uma tendência importante e a utilização dela, conceito de computação em nuvem, está em pleno uso atualmente. Na nuvem, os provedores oferecem recursos computacionais (Infraestrutura como Serviço), como, por exemplo, armazenamento, processamento, memória, conectividade, etc.
___
## Exigências Para Virtualização

Para que a virtualização funcione bem, as **máquinas virtuais (VMs)** devem se comportar como computadores reais, permitindo:  
- Inicializar como uma máquina física.  
- Instalar qualquer sistema operacional (Windows, Linux, etc.).  
- Rodar programas como se estivessem em hardware real.  

Quem torna isso possível é o **hipervisor** (também chamado de **Virtual Machine Monitor - VMM**), um software que gerencia as VMs.  

#### **O hipervisor precisa atender três critérios importantes:**  

1. **Segurança** → O hipervisor deve ter **controle total** sobre os recursos (CPU, memória, disco) para que uma VM não interfira em outra.  
2. **Fidelidade** → Os programas rodando em uma VM devem se comportar **exatamente igual** a como rodariam em um computador físico.  
3. **Eficiência** → A maior parte do código deve rodar **diretamente no hardware**, sem precisar do hipervisor interferindo o tempo todo (senão fica lento).  

#### **Resumo:**  
O hipervisor é como um **"chefe"** que cria e controla várias máquinas virtuais, garantindo que:  
✔️ Nenhuma VM atrapalhe a outra (**segurança**).  
✔️ Tudo funcione como se fosse um PC real (**fidelidade**).  
✔️ O desempenho seja bom, sem lentidão (**eficiência**).  

Isso permite que várias VMs rodem ao mesmo tempo, cada uma com seu sistema operacional, sem problemas. 🚀
___
## Tipos de Hipervisors
Para gerenciar máquinas virtuais, existem dois tipos de hipervisors como é apresentado na Figura 1. Temos o Tipo 1 (Figura 1a) que é como um sistema operacional, já que é o único programa executando no modo mais privilegiado. O seu trabalho é dar suporte a múltiplas cópias do hardware real, chamadas máquinas virtuais, similares aos processos que um sistema operacional normal executa. Já o Tipo 2 (Figura 1b) necessita de um sistema operacional com aplicações adicionais para gerenciar as máquinas virtuais. Em outras palavras, o Tipo 2 não está diretamente instalado na máquina física e sim sobre o sistema operacional, o qual hospeda. O sistema operacional instalado na máquina física é chamado de sistema hospedeiro. 
![[Pasted image 20250606000640.png]]
Exemplos de Hipervisor conforme o tipo:
1. **Tipo 1** : VMware ESXi, Microsoft Hyper-V server, KVM.  
2. **Tipo 2** : Oracle VM VirtualBox, VMware Workstation, Microsoft Virtual PC.
___
## Virtualização Real e Paravirtualização
### **Virtualização Real vs. Paravirtualização**  

Para entender como a virtualização funciona, é importante conhecer duas abordagens principais:  

#### **1. Virtualização Real (Full Virtualization)**  
- **Como funciona?**  
  - O **hipervisor** (como VMware ESXi, Hyper-V, KVM) **emula completamente o hardware**, criando máquinas virtuais (VMs) que se comportam como computadores físicos reais.  
  - O **sistema operacional convidado (guest OS)** roda **sem saber que está virtualizado** – ele acredita que está em um hardware real.  
  - O hipervisor **intercepta e traduz** todas as instruções sensíveis (como acesso a disco, rede e memória).  

- **Vantagens:**  
  - **Compatibilidade total**: Qualquer sistema operacional não modificado pode rodar.  
  - **Isolamento seguro**: Falhas em uma VM não afetam outras.  

- **Desvantagens:**  
  - **Overhead (sobrecarga) maior**, pois o hipervisor precisa traduzir muitas operações.  

- **Exemplos:**  
  - VMware ESXi, Microsoft Hyper-V (modo padrão), VirtualBox.  

---

#### **2. Paravirtualização**  
- **Como funciona?**  
  - O **sistema operacional convidado (guest OS) é modificado** para saber que está rodando em uma VM.  
  - Em vez de emular tudo, ele **"conversa" diretamente com o hipervisor** usando chamadas otimizadas (**hypercalls**).  
  - Isso **reduz a sobrecarga**, especialmente em operações de **E/S (entrada/saída, como disco e rede)**.  

- **Vantagens:**  
  - **Melhor desempenho** (menos overhead).  
  - **Mais eficiente** para operações de rede e armazenamento.  

- **Desvantagens:**  
  - Requer **modificação do SO convidado** (não funciona com Windows ou sistemas fechados sem suporte).  

- **Exemplos:**  
  - Xen (em modo paravirtualizado), KVM com drivers VirtIO (para Linux).  

---

### **Comparação Direta**  

| **Característica**       | **Virtualização Real**            | **Paravirtualização**               |  
|--------------------------|-----------------------------------|-------------------------------------|  
| **Modificação do SO**    | Não precisa                       | Precisa (kernel modificado)         |  
| **Desempenho**           | Mais lento (overhead maior)       | Mais rápido (otimizado)             |  
| **Compatibilidade**      | Suporta qualquer SO               | Só funciona com SOs adaptados       |  
| **Segurança**            | Isolamento completo               | Bom, mas depende da implementação   |  
| **Uso típico**           | VMs genéricas (Windows, Linux)   | Servidores de alta performance      |  

---

### **Quando usar cada uma?**  
✔ **Virtualização Real** → Quando você precisa rodar **sistemas operacionais não modificados** (ex: Windows, Linux padrão).  
✔ **Paravirtualização** → Quando **desempenho é crítico** e o SO suporta (ex: servidores Linux com Xen/KVM).  

#### **Exemplo Prático:**  
- Se você criar uma **VM Ubuntu no VirtualBox**, está usando **virtualização real**.  
- Se usar **Xen ou KVM com drivers VirtIO**, pode estar usando **paravirtualização** para melhorar desempenho de disco/rede.  

### **Conclusão**  
A **virtualização real** é mais flexível, enquanto a **paravirtualização** é mais rápida, mas exige adaptação do SO. A escolha depende do seu uso! 🚀
![[Pasted image 20250606001802.png]]
___
## **Virtualização CPU, Memória, Armazenamento e Dispositivos de E/S** 
O sistema hospedeiro (modificado ou não), atuando como hipervisor, deve **compartilhar a memória** física aos múltiplos sistemas operacionais virtualizados, em conjunto com os aplicativos que rodam neles e no sistemas hospedeiros, de forma eficiente. Para que isso ocorra, o programa hipervisor,  deve garantir que cada máquina virtual possua sua própria memória virtual mapeada na memória física da máquina. Desta forma, as máquinas virtuais acessam "exclusivamente" à memória, garantindo isolamento e segurança.  

Em relação à **virtualização de unidades de processamento** existentes na máquina física. O hipervisor deve gerenciar, juntamente como sistema hospedeiro, o acesso das máquinas virtuais ao processador físico. Isso pode ser realizado por meio de técnicas já vistas nesta disciplina, onde o hipervisor irá alocar o tempo de CPU, dividindo o tempo de processamento do processador entre as máquinas virtuais de forma equitativa ou conforme a demanda. Da mesma forma, o hipervisor deve permitir que as máquinas virtuais acessem e compartilhem os **dispositivos de entrada e saída** (mouse, teclado, monitor, placas de rede, etc). Para que isso ocorrer, o hipervisor emula os dispositivos existentes e cria um mapeamento destes dispositivos emulados com os dispositivos reais.

Em relação ao serviço de virtualização do armazenamento, o hipervisor deve garantir  o compartilhamento e alocação eficiente de recursos de armazenamento entre múltiplas máquinas virtuais. Para garantir essa eficiência, é fornecida uma camada de abstração para as máquinas virtuais, através da criação de _pool_ de armazenamento.
___
![[Pasted image 20250606004357.png]]
___
# Nuvens
### **Computação em Nuvem e Virtualização: Como Tudo Se Conecta**  

A **virtualização** é a tecnologia por trás do crescimento da **computação em nuvem**, permitindo que serviços como **Dropbox, Google Drive e AWS** funcionem de forma eficiente e escalável. Vamos entender como isso acontece e quais são as características essenciais da nuvem.  

---

## **1. Como a Nuvem Funciona com Virtualização?**  
Quando você salva um arquivo no **Dropbox** ou usa um serviço como **Google Docs**, seus dados não estão em um único computador físico, mas em **múltiplos servidores virtualizados**, gerenciados por um provedor de nuvem.  

- **A virtualização permite:**  
  - Criar **VMs (máquinas virtuais)** que rodam em servidores físicos compartilhados.  
  - Alocar recursos **dinamicamente** (CPU, memória, armazenamento) conforme a demanda.  
  - Oferecer **escalabilidade** (aumentar/reduzir capacidade automaticamente).  

---

## **2. As 5 Características Essenciais da Nuvem**  

Para ser considerado um **serviço de nuvem**, o provedor deve atender estes requisitos:  

| **Característica**                        | **Explicação**                                                                                                  | **Exemplo**                                                                 |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| **1. Serviço Automático (Self-Service)**  | O usuário pode provisionar recursos (armazenamento, VMs) **sem intervenção humana**.                            | AWS, Google Cloud, Azure permitem criar servidores com um clique.           |
| **2. Acesso Amplo pela Rede**             | Recursos disponíveis **via internet** para qualquer dispositivo (PC, celular, tablet).                          | Acessar arquivos do Google Drive de qualquer lugar.                         |
| **3. Pooling de Recursos (Multitenancy)** | Os provedores **compartilham** recursos físicos entre vários usuários, sem que eles saibam onde estão alocados. | Seus arquivos no Dropbox podem estar em servidores nos EUA, Europa ou Ásia. |
| **4. Elasticidade Rápida**                | Escala automaticamente conforme a demanda (aumenta capacidade quando necessário).                               | Netflix aumenta servidores em horários de pico.                             |
| **5. Serviço Mensurado (Pay-as-you-go)**  | Cobrança baseada no uso (armazenamento, tempo de CPU, tráfego de dados).                                        | AWS cobra por hora de uso de um servidor virtual.                           |

---

## **Tipos de Serviços em Nuvem**  

Existem três modelos principais de serviços em nuvem:  

### **IaaS (Infrastructure as a Service)**  
- **O que é?** Aluguel de **infraestrutura virtualizada** (servidores, redes, armazenamento).  
- **Para quem?** Empresas que querem controlar o SO e aplicações, mas não o hardware.  
- **Exemplos:**  
  - **Amazon EC2** (máquinas virtuais na AWS)  
  - **Microsoft Azure VMs**  
  - **Google Compute Engine**  

### **PaaS (Platform as a Service)**  
- **O que é?** Oferece um **ambiente pronto** para desenvolvimento (SO, banco de dados, ferramentas).  
- **Para quem?** Desenvolvedores que não querem gerenciar servidores.  
- **Exemplos:**  
  - **Google App Engine**  
  - **Microsoft Azure App Service**  
  - **Heroku**  

### **SaaS (Software as a Service)**  
- **O que é?** Software **pronto para uso**, acessado via navegador.  
- **Para quem?** Usuários finais que só precisam do aplicativo.  
- **Exemplos:**  
  - **Google Docs** (alternativa ao Office)  
  - **Dropbox** (armazenamento em nuvem)  
  - **Netflix** (streaming como serviço)  

---

### **Conclusão**  
A **virtualização** é a base da nuvem, permitindo que serviços como **IaaS, PaaS e SaaS** existam. Graças a ela, você pode:  
- Salvar arquivos no **Google Drive** (SaaS).  
- Hospedar um site na **AWS** (IaaS).  
- Desenvolver um app no **Heroku** (PaaS).  

Tudo isso com **elasticidade, segurança e baixo custo**! ☁️🚀