___
# Resposta do DeepSeek
Aqui está um passo a passo detalhado para configurar um projeto Django com SQLite e operações básicas de ORM:

### 1. Pré-requisitos e Ambiente Virtual
```bash
# Verifique a instalação do Python (3.6+)
python --version

# Instale o Django
pip install django

# Crie e ative um ambiente virtual (opcional mas recomendado)
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate    # Windows
```

### 2. Criar Projeto e Aplicativo
```bash
# Crie novo projeto
django-admin startproject myproject
cd myproject

# Crie um novo aplicativo
python manage.py startapp myapp
```

### 3. Configurar Aplicativo
Edite `myproject/settings.py`:
```python
INSTALLED_APPS = [
    ...
    'myapp',  # Adicione seu aplicativo aqui
]
```

### 4. Definir Modelo de Dados
Em `myapp/models.py`:
```python
from django.db import models

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.CharField(max_length=100)
    published_date = models.DateField()
    price = models.DecimalField(max_digits=5, decimal_places=2)

    def __str__(self):
        return self.title
```

### 5. Criar e Aplicar Migrações
```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Configurar Admin (Opcional)
Em `myapp/admin.py`:
```python
from django.contrib import admin
from .models import Book

admin.site.register(Book)
```

Crie superusuário:
```bash
python manage.py createsuperuser
```

### 7. Operações Básicas com ORM
Acesse o shell interativo:
```bash
python manage.py shell
```

Exemplos de operações:
```python
# Importar modelo
from myapp.models import Book
from datetime import date

# Criar registro
Book.objects.create(
    title="O Senhor dos Anéis",
    author="J.R.R. Tolkien",
    published_date=date(1954, 7, 29),
    price=49.90
)

# Consultar todos os registros
all_books = Book.objects.all()

# Filtrar registros
tolkien_books = Book.objects.filter(author__contains='Tolkien')
cheap_books = Book.objects.filter(price__lt=30)

# Atualizar registro
book = Book.objects.get(title="O Senhor dos Anéis")
book.price = 54.90
book.save()

# Excluir registro
book = Book.objects.get(title="Livro Indesejado")
book.delete()
```

### 8. Executar Servidor
```bash
python manage.py runserver
```

Acesse:
- Aplicação: http://localhost:8000
- Admin: http://localhost:8000/admin

### 9. Estrutura do Projeto
```
myproject/
├── myproject/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── myapp/
│   ├── migrations/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
└── db.sqlite3
```

### Dicas Importantes:
1. O SQLite é configurado por padrão no Django
2. O arquivo de banco de dados `db.sqlite3` é criado automaticamente
3. Sempre execute `makemigrations` e `migrate` após alterar modelos
4. Use `python manage.py shell` para testar consultas ORM
5. Para produção, considere migrar para PostgreSQL ou MySQL

Este setup permite que você comece rapidamente a desenvolver aplicações Django com todas as vantagens do ORM para manipulação de banco de dados, enquanto usa o SQLite para desenvolvimento local simplificado.
___
# Resultados
ao executar o passo a passo, tudo funcionou como deveria, aprendi a fazer consultas ORM com o shell que não sabia que existia.
![[Pasted image 20250411114241.png]]
![[Pasted image 20250411114333.png]]
