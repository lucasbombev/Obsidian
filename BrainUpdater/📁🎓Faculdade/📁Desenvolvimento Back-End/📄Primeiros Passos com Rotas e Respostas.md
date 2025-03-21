tags: #BackEnd #Faculdade 
___
## O que são rotas?
Em back-end, **rotas** (ou routes) são mecanismos que definem como uma aplicação responde a solicitações de clientes (como navegadores ou aplicativos) para um determinado **endpoint** (URL) e um método HTTP específico (GET, POST, PUT, DELETE, etc.). Elas são essenciais para criar APIs ou sistemas que processam e retornam dados conforme a requisição do usuário.

### Como funcionam as rotas?

1. **Requisição do cliente**: O cliente (front-end ou outro sistema) faz uma requisição para um endereço específico (URL) usando um método HTTP.
2. **Rota no back-end**: O back-end recebe a requisição e verifica se há uma rota configurada para aquela URL e método.
3. **Processamento**: A rota executa uma função (ou controller) que processa a requisição, como buscar dados no banco de dados, validar informações ou realizar cálculos.
4. **Resposta**: Após o processamento, o back-end retorna uma resposta ao cliente, geralmente em formato JSON, HTML ou outro.
___
## Aplicação no Django
No Django, as rotas são definidas principalmente no arquivo **`urls.py`**. Elas mapeiam URLs para **views** (funções ou classes que processam a requisição e retornam uma resposta).
___
## Estrutura do Projeto
Suponha que você tenha um projeto Django chamado `myproject` e um app chamado `users`. A estrutura de arquivos seria algo assim:
myproject/
├── myproject/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py  # Aqui definimos as rotas principais
│   └── wsgi.py
└── users/
    ├── migrations/
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── tests.py
    ├── views.py  # Aqui definimos as views (lógica das rotas)
    └── urls.py   # Rotas específicas do app "users"

No arquivo `myproject/urls.py`, definimos as rotas principais do projeto e incluímos as rotas do app `users`:
```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),  # Rota padrão do painel de administração
    path('api/', include('users.urls')),  # Inclui as rotas do app "users"
]
```
No arquivo `users/urls.py`, definimos as rotas específicas para o app `users`:
```python
from django.urls import path
from . import views

urlpatterns = [
    path('users/', views.user_list, name='user_list'),  # GET /api/users/
    path('users/<int:id>/', views.user_detail, name='user_detail'),  # GET /api/users/{id}
]
```
