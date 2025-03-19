tags: #Software #Python #Faculdade 
___
## Componentes Principais
- Arquivos de configuração
- Código-fonte do server
- Banco de dados
- Arquivos estáticos (se aplicável)
![[Pasted image 20250314092423.png]]
![[Pasted image 20250314092917.png]]
A princípio usaremos Django por causa que já temos algum conhecimento em Python.
## O que é um APP no Django?
No Django, um **app** é uma unidade modular que encapsula uma funcionalidade específica dentro de um projeto. Ele é projetado para ser reutilizável e independente, o que significa que você pode desenvolver um app para uma tarefa específica (como um sistema de autenticação, um blog, ou um fórum) e reutilizá-lo em outros projetos Django.
## Criação de Rotas
Rotas são caminhos definidos no servidor que correspondem a URLs específicas. Elas determinam como o servidor responde a diferentes solicitações HTTP (GET, POST, PUT, DELETE).

> [!Exemplos de Rotas] Exemplos de Rotas
> GET /users -> Retorna uma lista de usuários. 
> POST /users -> Cria um novo usuário. 
> GET /users/:id -> Retorna os detalhes de um usuário específico. 
> PUT /users/:id -> Atualiza as informações de um usuário específico. 
> DELETE /users/:id -> Remove um usuário específico.

## Conceitos de MVC (Model-View-Controller)
![[Pasted image 20250314184027.png]]
## O que é ?
O MVC é uma forma de organizar o código de uma aplicação dividindo-a em três partes principais:

1. **Model (Modelo)**: Gerencia os dados e a lógica de negócios.
2. **View (Visão)**: Mostra os dados para o usuário (a interface).
3. **Controller (Controlador)**: Faz a ligação entre o Model e a View, processando as requisições do usuário.
### Model
O model é responsável por tudo que envolve os dados
- Define como os dados são armazenados (por exemplo, em um banco de dados).
- Contém a lógica de negócios (como validar ou processar os dados).
**Exemplo**:  
No sistema de lista de tarefas, o Model define o que é uma "tarefa":

- Uma tarefa tem um título, uma descrição e um status (concluída ou não).    
- O Model também pode ter regras, como "uma tarefa não pode ser criada sem um título".
No Django, o Model é definido usando classes no arquivo `models.py`.
### View
A **View** é responsável por **mostrar os dados** para o usuário. Ela:

- Pega os dados do Model e os exibe de forma amigável (em uma página web, por exemplo).
- Não contém lógica de negócios; ela apenas mostra o que o Model fornece.

**Exemplo**:  
No sistema de lista de tarefas, a View pode:

- Mostrar uma lista de todas as tarefas.
- Exibir os detalhes de uma tarefa específica.
- Mostrar um formulário para adicionar uma nova tarefa.
No Django, a View é definida no arquivo `views.py`.
### **Controller (Controlador)**

O **Controller** é o "cérebro" da aplicação. Ele:

- Recebe as requisições do usuário (por exemplo, quando o usuário clica em um botão).
- Decide o que fazer com essa requisição (pedir dados ao Model, processar informações, etc.).
- Passa os dados para a View, que os exibe.

**Exemplo**:  
No sistema de lista de tarefas, o Controller pode:

- Receber uma requisição para adicionar uma nova tarefa.
- Validar os dados (usando o Model).
- Pedir ao Model para salvar a tarefa no banco de dados.
- Pedir à View para mostrar a lista atualizada de tarefas.
No Django, o Controller é representado principalmente pelo arquivo `urls.py` (que mapeia as requisições para as views) e pelas próprias views (que processam as requisições).

___

## MVC no Django
### **MVC no Django**

O Django usa uma variação do MVC chamada **Model-View-Template (MVT)**:

- **Model**: Igual ao MVC tradicional (gerencia os dados).
- **View**: No Django, a View faz o papel do Controller (processa as requisições e decide o que fazer).
- **Template**: Faz o papel da View no MVC tradicional (mostra os dados para o usuário).
