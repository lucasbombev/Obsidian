### 📦 DES (Data Encryption Standard)

#### 🔹 História e contexto

- Criado pela IBM nos anos 70, adotado pelo governo dos EUA em 1977.
    
- Foi muito usado durante décadas, mas hoje está obsoleto por causa da sua vulnerabilidade a ataques.
    

#### 🔹 Características principais:

| Característica   | Valor                     |
| ---------------- | ------------------------- |
| Tipo             | Criptografia simétrica    |
| Tamanho da chave | 56 bits                   |
| Tamanho do bloco | 64 bits                   |
| Rodadas (rounds) | 16                        |
| Método           | Substituição e permutação |

---

### 🔧 Como o DES funciona (resumido):

1. **Divisão do bloco**: Divide o texto em blocos de 64 bits.
    
2. **Permutação inicial** (IP): Mistura os bits com uma tabela pré-definida.
    
3. **Rodadas de Feistel (16 vezes)**:
    
    - Divide o bloco em duas metades (L e R).
        
    - R passa por uma função F com uma subchave.
        
    - O resultado de F é combinado com L.
        
    - Depois L e R trocam de lugar.
        
4. **Permutação final** (IP⁻¹): Reorganiza os bits no final.
    

#### 🔓 Por que o DES se tornou inseguro?

- A chave de 56 bits pode ser quebrada por força bruta em poucas horas com computadores modernos.
    

---

### 🔐 AES (Advanced Encryption Standard)

#### 🔹 História e contexto

- Criado para substituir o DES.
    
- Foi escolhido após uma competição internacional vencida pelo algoritmo **Rijndael**, criado por dois belgas.
    
- Tornou-se o novo padrão de criptografia em 2001.
    

### 🔹 Características principais:

| Característica   | Valor                                        |
| ---------------- | -------------------------------------------- |
| Tipo             | Criptografia simétrica                       |
| Tamanho do bloco | 128 bits                                     |
| Tamanho da chave | 128, 192 ou 256 bits                         |
| Rodadas (rounds) | 10 (128), 12 (192), 14 (256)                 |
| Método           | Substituição, permutação e álgebra de matriz |

---

#### 🔧 Como o AES funciona (resumido):

1. **Entrada**: Um bloco de 128 bits.
    
2. **Expansão de chave**: Gera uma subchave para cada rodada.
    
3. **Rodadas de criptografia**:
    
    - **SubBytes**: Substitui cada byte usando uma tabela S-box.
        
    - **ShiftRows**: Desloca linhas da matriz de dados.
        
    - **MixColumns**: Mistura colunas usando operações matemáticas.
        
    - **AddRoundKey**: Combina os dados com a subchave da rodada.
        
4. **Última rodada**: Como as anteriores, mas **sem o MixColumns**.
    

---

### 🥊 Comparação entre DES e AES

| Recurso          | DES                | AES                                |
| ---------------- | ------------------ | ---------------------------------- |
| Segurança        | Fraco (atualmente) | Muito forte                        |
| Tamanho da chave | 56 bits            | 128, 192 ou 256 bits               |
| Tamanho do bloco | 64 bits            | 128 bits                           |
| Velocidade       | Lento              | Rápido (especialmente em hardware) |
| Complexidade     | Menor              | Maior                              |

---

### 🧪 Exemplo prático (simplificado):

Imagina que você quer proteger a frase:

> "SENHA123"

1. Com DES, essa frase seria convertida para binário, tratada em blocos de 64 bits, e criptografada com uma chave de 56 bits.
    
2. Com AES, os dados seriam organizados numa matriz 4x4 de bytes, passariam pelas rodadas descritas, com uma chave de até 256 bits.
    

Na prática, AES gera uma saída **muito mais segura** e **difícil de quebrar**.

---

### 🧩 Onde são usados?

#### ✅ DES (hoje, raramente usado):

- Sistemas legados
    
- Estudos históricos de criptografia
    

#### ✅ AES:

- Comunicações seguras (HTTPS, VPNs)
    
- Criptografia de discos e arquivos (BitLocker, VeraCrypt)
    
- Aplicações bancárias e governamentais
    
- Dispositivos móveis e Wi-Fi (WPA2 usa AES)
    

---

### 🧠 Dica de ouro:

Se você está estudando segurança da informação, **concentre-se no AES**, que é o padrão moderno.  
Estude o DES como uma **base histórica** para entender a evolução da criptografia.

---

Se quiser, posso montar um **mapa mental**, uma **linha do tempo**, ou até uma **aula com slides** sobre o tema. Quer?
