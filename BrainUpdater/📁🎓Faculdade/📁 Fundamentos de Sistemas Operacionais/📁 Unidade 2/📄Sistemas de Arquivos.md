tags: #Faculdade #Concurso 
___
## O que é?
Um **sistema de arquivos** (File System) é um componente essencial de um sistema operacional, responsável por organizar, armazenar, gerenciar e recuperar dados em dispositivos de armazenamento (HDDs, SSDs, pendrives, etc.). Ele define como os dados são estruturados e como o sistema operacional interage com eles.
## Conceito de arquivos: Abastração para Armazenamento Persistente
Os arquivos, sendo registros pertinentes aos sistemas operacionais, refletem um unidade lógica de informação criada por processos. Ele permite o armazenamento persistente de dados, não sendo afetado pelo ciclo de vida dos processos.

## Características dos arquivos
Considerando que os arquivos são independentes entre si, onde os mesmos podem ser acessados por inúmeros processos, os mesmos, devem ser persistentes mesmo após a execução e término processo que os criou. Eles podem ser lidos, escritos, excluídos pelo sistema operacional através de outros processos. O nome dos arquivos, é um dos atributos atribuídos pelos processos. Alguns exemplos a seguir:
**Exemplo:**  
- Nomeação: documento.txt, relatorio.docx
- Extensões: .txt, .docx, .pdf
___
## Estrutura e Acesso aos Arquivos
![[Pasted image 20250418103245.png]]
**Em resumo, a imagem mostra:**

- A unidade fundamental de armazenamento (**byte**).
- Como bytes podem ser agrupados para formar unidades maiores de informação (**registro**).
- Uma analogia de como esses registros (representados pelos nomes dos animais) podem ser organizados em uma estrutura hierárquica, similar à organização de arquivos e pastas em um sistema de arquivos real.

## Atributos == Metadados
Informações sobre os arquivos, como:

- **Nome do arquivo**
- **Tamanho**
- **Localização no disco**
- **Permissões**
- **Timestamps** (data de criação, modificação, acesso)
os quatro primeiros atributos de um arquivo comum, estão relacionados à proteção do arquivo (proteção, senha, criação e proprietário), indicando quem tem permissão para acessá-lo e quem não tem.
![[Pasted image 20250418103458.png]]

### Principais Atributos de um arquivo
Os sistemas de arquivos permitem que os processos realizem determinadas ações durante a execução, dentre essas possibilidades, os processos podem criar, deletar, abrir, fechar, modificar os atributos durante a execução na CPU. Além disso, alguns exemplos dessas operações podem ser encontrados na Tabela
![[Pasted image 20250418103701.png]]
___
## Diretórios
Para controlar os arquivos, sistemas de arquivos normalmente têm diretórios ou pastas, que são em si arquivos. A forma mais simples de um sistema de diretório é ter um diretório contendo todos os arquivos. Às vezes ele é chamado de diretório-raiz.  Em consequência, é necessária uma maneira para agrupar arquivos relacionados em um mesmo local. Faz-se necessária uma hierarquia (isto é, uma árvore de diretórios, como pode ser visto na Figura
chamado de organização hierárquica/ em árvore
![[Pasted image 20250418103848.png]]

## Operações com Diretórios
No sistema operacional, o usuário pode utilizar chamadas de sistema para gerenciar (criação, exclusão, leitura, escrita) nos diretórios. A seguir, a Tabela 2 apresenta um resumo das principais chamadas.
![[Pasted image 20250418134450.png]]
## Implementação do sistema de arquivos
Caro cursista, ao utilizar um sistema operacional, o usuário está preocupado em como os arquivos serão nomeados, quais operações são permitidas neles, como é a árvore de diretórios e questões de interface similares. Neste sentido, para viabilizar essas operações, a maioria dos discos pode ser dividida em uma ou mais partições, com sistemas de arquivos independentes em cada partição. O Setor 0 do disco é chamado de MBR (Master Boot Record — registro mestre de inicialização) e é usado para inicializar o computador, conforme a Figura.
![[Pasted image 20250418134739.png]]

## Métodos de Alocação de Arquivos em Sistemas de Arquivos
### Método de Alocação Contigua

- O arquivo é armazenado em **blocos sequenciais (vizinhos) e contíguos** no disco.
- O sistema só precisa guardar o **endereço inicial** e o **tamanho** do arquivo. Esta técnica pode causar a fragmentação dos arquivos ao longo do tempo.
Se um arquivo ocupa 3 blocos, ele será armazenado assim:
Bloco 5 → Bloco 6 → Bloco 7  

**Vantagens:**
✅ **Acesso rápido** (leitura sequencial eficiente, ideal para discos magnéticos).  
✅ **Simplicidade** (fácil implementação).

**Desvantagens:**
❌ **Fragmentação externa** (espaço livre fica dividido em pequenos pedaços não contíguos).  
❌ **Dificuldade em expandir arquivos** (se não houver espaço contíguo disponível).

### Lista encadeada

- Cada bloco do arquivo contém **um ponteiro para o próximo bloco**.
- O diretório armazena apenas o **endereço do primeiro bloco**.
Um arquivo de 3 blocos pode estar espalhado no disco:
Bloco 3 → (aponta para) Bloco 10 → (aponta para) Bloco 7 → (FIM)  

**Vantagens**
✅ **Sem fragmentação externa** (qualquer bloco livre pode ser usado).  
✅ **Crescimento flexível** (arquivos podem aumentar dinamicamente).

**Desvantagens:**
❌ **Acesso lento** (para ler o bloco N, é necessário percorrer N ponteiros).  
❌ **Fragilidade** (se um ponteiro for corrompido, o arquivo pode ser perdido).

### Alocação por tabela de memória (FAT e inodes)

Imagine agora que você tem um índice para uma coleção de arquivos espalhados em diferentes gavetas. A tabela de alocação (ou tabela de índice) é uma estrutura de dados separada que contém informações sobre onde cada parte de um arquivo ou programa está armazenada na memória. Em vez de os blocos de dados se apontarem diretamente uns aos outros (como na lista encadeada), a tabela mantém o controle de todos os blocos alocados a um determinado arquivo e a sua ordem.

- **Como funciona?**
    - Uma **tabela central** (FAT) armazena os ponteiros de todos os blocos.
    - Cada entrada na FAT indica o **próximo bloco do arquivo**.
    - O diretório guarda o **primeiro bloco**, e a FAT faz o resto.

**Vantagens**
✅ **Acesso mais rápido que lista encadeada** (todos os ponteiros estão na RAM).  
✅ **Menos vulnerável a corrupção** (a FAT pode ser reconstruída).

 **Desvantagens:**
❌ **Tabela ocupa memória RAM** (em sistemas grandes, a FAT pode ser enorme).

![[Pasted image 20250418141749.png]]
### Inodes 
De forma simples, um **inode** é como um "cartão de identificação" para cada arquivo ou diretório. Esse cartão contém **metadados**, que são dados sobre os dados. Ele guarda informações cruciais, mas **não guarda o conteúdo real do arquivo**.

**Imagine a seguinte analogia:**

Pense em uma biblioteca.

- **O conteúdo do livro:** Seria o conteúdo real do seu arquivo (texto, imagem, vídeo, etc.), armazenado em algum lugar no disco.
- **A ficha catalográfica do livro:** Isso seria o **inode**. Ele contém informações importantes sobre o livro, como:
    - **Quem é o autor (proprietário do arquivo)**
    - **Quando o livro foi publicado (data de criação)**
    - **Quantas páginas ele tem (tamanho do arquivo)**
    - **Que tipo de livro é (permissões de acesso: quem pode ler, escrever, executar)**
    - **Onde as cópias do livro estão guardadas nas estantes (os blocos de dados no disco)**

**Em resumo, o inode armazena tudo o que o sistema operacional precisa saber sobre um arquivo ou diretório, exceto o seu conteúdo em si.**

___
## Consistência do Sistema de Arquivos
Caso o sistema falhe no meio do processo, o sistema de arquivos poderá se tornar inconsistente. Alguns programas especiais verificam a consistência do sistema de arquivos toda vez que você inicia o computador, na maioria das vezes, após uma falha ocorrida. Dessa forma, você pode salvar com segurança e saber que todas as informações estarão lá para você. Portanto, back-ups e sistemas de arquivos consistentes são fundamentais para uma abordagem completa de manutenção de dados.

## Sistemas de Arquivos
![[Pasted image 20250418143229.png]]

