Tags: #Faculdade  #Forense #Software 
Bibliografia: [Criptografia e Segurança de Redes ](https://plataforma.bvirtual.com.br/Leitor/Publicacao/22446/pdf/11?code=oyx/sKFPSSsCdNe8wEkg0O/UXVVOF5Mu2HabnhlUeY4yQDzB+XEU4cnEJikH8uMipVLyXXll6W95Y1cBEqE2CA==)

___
# Fundamentos de Criptografia
## O que é?
A **criptografia** é a ciência e a arte de proteger informações, transformando dados legíveis (texto puro) em um formato ilegível (texto cifrado) para que apenas pessoas ou sistemas autorizados possam acessá-los.
![[Pasted image 20250407145328.png]]
# Criptografia Simétrica e Assimétrica
## Criptografia Simétrica
### **Como Funciona?**

- Usa **uma única chave** (secreta) para **criptografar e descriptografar** os dados.
- O remetente e o destinatário **devem conhecer a mesma chave**.
### **Exemplo:**

- **Alice** quer enviar uma mensagem secreta para **Bob**.
- Ambos usam a **mesma chave** (ex.: `chave123`) para cifrar e decifrar.
- Se a mensagem for interceptada, só poderá ser lida com `chave123`.
### **Algoritmos Comuns:**

✅ **AES** (Advanced Encryption Standard) – Padrão usado pelo governo dos EUA.  
✅ **DES** (Data Encryption Standard) – Mais antigo e menos seguro.  
✅ **ChaCha20** – Usado em comunicações modernas (ex.: TLS).
### **Vantagens:**
🔹 **Rápida** – Ideal para criptografar grandes volumes de dados.  
🔹 **Eficiente** – Consome menos recursos computacionais.
### **Desvantagens:**
🔴 **Problema de Distribuição de Chaves** – Como compartilhar a chave de forma segura?  
🔴 **Risco de Interceptação** – Se a chave for roubada, a segurança é comprometida.

> [! Representação de criptografia simétrica]
![[Pasted image 20250407150434.png]]


> [!Principais Algoritmos]
![[Pasted image 20250407150536.png]]

## Algoritmos DES e AES
### O que são ?
**DES (Data Encryption Standard)** e **AES (Advanced Encryption Standard)** são algoritmos de **criptografia simétrica**, ou seja, **usam a mesma chave para criptografar e descriptografar** informações.
## [[APROFUNDAR DES E AES]]

---

## Criptografia Assimétrica
### **Como Funciona?**

- Usa **duas chaves**:
    - **Chave Pública** → Pode ser compartilhada com qualquer um (usada para **criptografar**).
    - **Chave Privada** → Mantida em segredo (usada para **descriptografar**).
1. **Bob** gera um par de chaves:
    - Chave pública: `pub_Bob` (qualquer um pode ver).
    - Chave privada: `priv_Bob` (só Bob conhece).
2. **Alice** usa `pub_Bob` para criptografar a mensagem.
3. Só **Bob** pode descriptografar usando `priv_Bob`.
### **Algoritmos Comuns:**

✅ **RSA** – Um dos mais usados (ex.: HTTPS, SSH).  
✅ **ECC** (Elliptic Curve Cryptography) – Mais eficiente que RSA (usado em Bitcoin).  
✅ **Diffie-Hellman** – Usado para troca segura de chaves.
### **Vantagens:**
🔹 **Mais Segura** – Não há problema de distribuição de chaves.  
🔹 **Autenticação e Assinaturas Digitais** – Permite verificar a identidade do remetente.
### **Desvantagens:**
🔴 **Mais Lenta** – Não é eficiente para grandes volumes de dados.  
🔴 **Complexidade** – Requer mais poder computacional.

### **Solução Híbrida (Usada na Prática)**
Muitos sistemas combinam ambas:
1. **Assimétrica** para trocar uma chave simétrica de forma segura.
2. **Simétrica** para criptografar os dados (mais eficiente).
Exemplo: **HTTPS** usa RSA (assimétrica) para negociar uma chave AES (simétrica).
---

### **Resumo Final**
- **Simétrica**: Uma chave, rápida, mas difícil de compartilhar com segurança.
- **Assimétrica**: Duas chaves (pública/privada), mais segura, mas mais lenta.    
- **Na prática**: Sistemas modernos usam **ambas** para melhor eficiência e segurança.

___
**Outros pontos chaves** 

- **Chaves assimétricas :** duas chaves relacionadas, uma pública e uma privada, que são usadas para realizar operações complementares, como encriptação e decriptação ou geração e verificação de assinatura.
- **Certificado de chave pública** : um documento emitido e assinado digitalmente pela chave privada de uma autoridade de Certificação, que vincula o nome de um assinante a uma chave pública. o certificado indica que o assinante identificado tem o único controle e acesso à chave privada correspondente.
- **Algoritmo criptográfico de chave pública (assimétrica)** : um algoritmo criptográfico que usa duas chaves relacionadas, uma pública e uma privada. as duas têm a propriedade de ser computacionalmente inviável derivar a chave privada a partir da pública.
- **Infraestrutura de chave pública (pKi)**  : um conjunto de políticas, processos, plataformas de servidor, software e estações de trabalho usadas para fins de administrar certificados e pares de chave pública­privada, incluindo a capacidade de emitir, manter e revogar certificados de chave pública.
    - Em um nível alto, a PKI inclui:
        - **Chaves PKI:** Um par de chaves que permite a criptografia - um processo de ocultação de dados para impedir que qualquer pessoa, exceto o destinatário pretendido, os leia. Na criptografia, cada chave pública é pareada com uma chave privada. A chave pública é distribuída livre e abertamente, enquanto a chave privada é secreta para o proprietário.
        - **Certificados digitais:** Credenciais eletrônicas que vinculam a identidade do titular do certificado a um par de chaves que pode ser usado para criptografar e assinar informações. 
        - **Certificate Authority (CA):** A CA é a entidade que emite certificados digitais. 
        - Autoridade de registro (AR): Responsável por aceitar solicitações de certificados e autenticar o indivíduo ou organização por trás delas.
        - **Repositório de certificados:** Locais seguros onde os certificados são armazenados e podem ser recuperados para validação.
        - **Software de gerenciamento centralizado:** Um painel onde as organizações podem gerenciar suas chaves criptográficas e certificados digitais.
        - **Módulo de Segurança de Hardware (HSM):** Dispositivos físicos que fornecem um ambiente seguro para executar operações criptográficas e armazenar/gerenciar chaves digitais.

> [!Esquema de cifra assimétrica]
> ![[Pasted image 20250407175032.png]]

> [!Principais Algoritmos de criptografia assimétrica]
> 
> 
> ![[Pasted image 20250407175204.png]]

___
# Funções Hash
As **funções hash** são algoritmos essenciais em criptografia e segurança da informação. Elas transformam **qualquer dado de entrada** (texto, arquivo, senha) em um **valor fixo de tamanho definido**, chamado **hash**.


#### **Principais Características:**

1. **Determinística** → A mesma entrada sempre gera o mesmo hash.
2. **Irreversível** → Não é possível recuperar o dado original a partir do hash.
3. **Resistente a colisões** → É extremamente difícil encontrar duas entradas diferentes que gerem o mesmo hash.
4. **Pequena mudança, grande diferença** → Alterar um bit na entrada muda completamente o hash.

> [!Funcionamento de hash]
> ![[Pasted image 20250407192052.png]]

### como uma Hash funciona?
Imagine uma função hash como uma **máquina de moer carne**:
- **Entrada**: Dados (ex.: `"senha123"`).
- **Processamento**: Algoritmo matemático (ex.: SHA-256).
- **Saída**: Hash (ex.: `"ef92b778..."`).
**Exemplo Prático:**

| Entrada | Hash (SHA-256) |                                  |
| ------- | -------------- | -------------------------------- |
| `"Olá"` | `d1e43e...`    |                                  |
| `"olá"` | `a4d55b...`    | _(Note que só mudou uma letra!)_ |
### **Principais Algoritmos de Hash**

| Algoritmo      | Tamanho do Hash | Uso Comum                                  |
| -------------- | --------------- | ------------------------------------------ |
| **MD5**        | 128 bits        | ❌ Obsoleto (vulnerável a colisões)         |
| **SHA-1**      | 160 bits        | ❌ Fraco (não recomendado)                  |
| **SHA-256**    | 256 bits        | ✅ Bitcoin, senhas, integridade de arquivos |
| **SHA-3**      | Variável        | ✅ Sucessor do SHA-2                        |
| **Bcrypt**     | -               | ✅ Hash de senhas (com "salt")              |
| **RIPEMD-160** | 160 bits        | ✅ Endereços Bitcoin                        |
As funções hash podem ser utilizadas em algumas aplicações, como por exemplo:

- **Verificação de integridade de arquivos**: usada para garantir que arquivos ou dados não foram alterados após serem gerados ou transmitidos. Calculando o hash original e comparando-o após a transmissão, é possível identificar qualquer alteração não autorizada​.
- **Armazenamento seguro de senhas**: ao invés de guardar as senhas em texto puro, muitos sistemas armazenam apenas o hash das senhas, aumentando a segurança caso ocorra uma invasão e os dados sejam comprometidos​
- **Assinaturas digitais**: as funções hash são usadas para criar um resumo criptográfico de dados, assegurando que o conteúdo assinado digitalmente não foi alterado. Esse resumo é fundamental para a autenticação e integridade dos dados em assinaturas digitais​

> [!Principais Algoritmos de Hash]
> - **Geração de identificadores únicos**: em sistemas de deduplicação de dados, hashes garantem que dados duplicados possam ser identificados e eliminados de forma eficiente, economizando armazenamento e melhorando o desempenho do sistema.
> ![[Pasted image 20250407192913.png]]

___
# Certificados / Assinaturas Digitais
 O desenvolvimento mais importante a partir do trabalho sobre criptografia de chave pública é a assinatura digital. Esta oferece um conjunto de capacidades de segurança que seria difícil de implementar de qualquer outra maneira.
 ## **Assinatura Digital (Como Funciona?)**

É como um **carimbo único** que prova:
1. **Quem enviou** (autenticidade).
2. **Que o conteúdo não foi alterado** (integridade).

#### **Passo a Passo**:

1. **Você cria um "resumo" (hash) do documento** (como um código único compacto).
2. **Criptografa esse resumo com sua chave privada** → Isso vira a **assinatura**.
3. **Envia o documento + assinatura** para alguém.
#### **Como o destinatário verifica?**

1. **Descriptografa a assinatura com sua chave pública** (se funcionar, prova que foi você quem assinou).
2. **Compara o resumo descriptografado com um novo hash do documento recebido** (se for igual, o documento não foi alterado).

✅ **Se tudo bater**: Documento é **válido e autêntico**.

---

### **3. Certificado Digital (O que é?)**

É como um **RG digital** que **vincula uma pessoa/empresa a uma chave pública**. Ele contém:

- Nome do dono.
    
- Chave pública.
    
- **Assinatura de uma Autoridade Certificadora (CA)** (como um "cartório digital").
    

#### **Como funciona?**

1. **Você gera um par de chaves (pública + privada)**.
    
2. **Envia sua chave pública + seus dados para uma CA** (ex.: Serasa, DigiCert).
    
3. **A CA verifica sua identidade e assina seu certificado** (usando a chave privada dela).
    
4. **Agora, quando você envia algo, inclui seu certificado**.
    

#### **Por que confiar no certificado?**

- Seu navegador/OS já tem as **chaves públicas das CAs confiáveis** (como uma lista de cartórios conhecidos).
    
- Ele **verifica a assinatura da CA no certificado** para confirmar que é legítimo.
 ![[Pasted image 20250408140421.png]]
 Os certificados digitais são como carteiras de identidade virtuais para pessoas ou empresas. Eles contêm informações como nome, CPF/CNPJ e chave pública, que é usada para criptografar dados. Essa chave pública é associada a uma chave privada, que só o proprietário do certificado conhece. As Autoridades Certificadoras (ACs) são responsáveis por emitir e gerenciar esses certificados, garantindo a sua autenticidade.  
 A assinaturas digitais, por sua vez, utilizam os certificados digitais para garantir a integridade e autenticidade de documentos eletrônicos. Ao assinar digitalmente um documento, o signatário utiliza sua chave privada para gerar uma assinatura digital única, que é anexada ao documento. Essa assinatura pode ser verificada por qualquer pessoa que possua a chave pública correspondente, garantindo que o documento não foi alterado desde que foi assinado e que o signatário é quem realmente afirma ser. 
 As assinaturas digitais oferecem um alto nível de segurança e são amplamente utilizadas em transações eletrônicas, contratos digitais e processos governamentais.

O algoritmo de assinatura digital deve repseitar os seguintes critérios:

- **Criação do par de chaves:**
    
    - **Chave pública:** Essa chave é distribuída livremente e serve como um tipo de "cadeado" para criptografar dados.
    - **Chave privada:** Essa chave é mantida em segredo pelo proprietário e é usada para "desbloquear" os dados criptografados com a chave pública.
- **Criação do hash:**
    - O documento a ser assinado é submetido a uma função hash, que gera uma representação única e curta desse documento (uma espécie de "impressão digital"). Essa representação é chamada de hash.
- **Assinatura:**
    - O proprietário utiliza sua chave privada para criptografar o hash. Essa assinatura digital é então anexada ao documento original.
- **Verificação:**
- Quem receber o documento pode utilizar a chave pública do proprietário para descriptografar a assinatura digital e obter o hash original.
- Em seguida, o receptor calcula o hash do documento recebido e compara com o hash obtido da assinatura.
- Se os hashes corresponderem, significa que o documento não foi alterado desde a assinatura e que a assinatura foi gerada pelo proprietário da chave privada correspondente à chave pública utilizada para a verificação.
## Principais Algoritmos
![[Pasted image 20250408140803.png]]
