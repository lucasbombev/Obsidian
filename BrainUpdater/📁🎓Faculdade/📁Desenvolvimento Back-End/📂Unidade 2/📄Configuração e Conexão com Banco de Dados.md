tags: #Faculdade #Software #BackEnd #Python 
___
O banco de dados é o armazenamento de centralizado das informações, permitindo que os dados sejam acessados, processados e gerenciados facilmente.
## Vantagens
**Persistência:** Os dados são armazenados permanentemente, mesmo após o sistema ser desligado.
**Organização e estruturação**
**Consulta eficiente**: utilizando linguagens como SQL é possível manipular de maneira eficiente.

## Desvantagens
**Complexidade Inicial:** 
**Custo de manutenção**: Bancos de dados avançados podem exigir servidores dedicados e administradores de banco de dados
**Risco de falhas**: Falta de boas práticas como replicação dos dados podem causar perdas de informações importantes.

# Organização de Banco de Dados
Bancos de dados podem ser organizados em bancos relacionais e não relacionais(NoSQL).
## Bancos de Dados Relacionais
Utilizam tabelas para organizar os dados em linhas e colunas, seguindo o modelo relacional e usando SQL para manipulação dos dados.
## Bancos de Dados Não Relacionais
Projetados para armazenar dados de forma flexível e escalável, fora do modelo relacional. Utilizados em sistemas que demandam alta disponibilidade, escalabilidade horizontal e dados sem estrutura fixa.

A princípio vou usar SQLite, mas MongoDB me interessou bastante.

# Biblioteca ORM (Mapeamento Objeto-Relacional)
# Biblioteca ORM Explicada de Forma Simples

ORM significa **Object-Relational Mapping** (Mapeamento Objeto-Relacional). É uma biblioteca que faz uma "ponte" entre o mundo dos bancos de dados relacionais (como MySQL, PostgreSQL) e o mundo da programação orientada a objetos.

## Como funciona?

Imagine que você tem uma tabela no banco de dados chamada `Clientes`. Com ORM:

1. A tabela vira uma **classe** no seu código (ex: `Cliente`)
2. Cada linha da tabela vira um **objeto** dessa classe
3. Cada coluna vira um **atributo** do objeto

## Exemplo prático

Sem ORM (usando SQL direto):
```python
cursor.execute("SELECT * FROM clientes WHERE id = 1")
dados = cursor.fetchone()
cliente = {"nome": dados[1], "email": dados[2]}
```

Com ORM:
```python
cliente = Cliente.objects.get(id=1)  # Retorna um objeto Cliente
print(cliente.nome)  # Acessa como atributo normal
```

## Vantagens do ORM:
- ✨ **Menos código SQL** - Trabalha com objetos ao invés de queries
- 🔄 **Banco independente** - Troca de MySQL para PostgreSQL com menos esforço
- 🛡 **Segurança** - Protege contra SQL injection automaticamente
- ⚡ **Produtividade** - Operações comuns ficam mais rápidas de escrever

## ORMs populares:
- Python: Django ORM, SQLAlchemy
- PHP: Eloquent (Laravel), Doctrine
- Java: Hibernate
- JavaScript/TypeScript: TypeORM, Sequelize

ORM é como um tradutor que converte dados do banco em objetos do seu programa e vice-versa, simplificando muito o trabalho com bancos de dados!
___
# CRUD Explicado de Forma Simples

CRUD é um acrônimo que representa as **4 operações básicas** que fazemos com dados em qualquer sistema:

## C - Create (Criar)
- Adicionar novos registros/dados
- Exemplo: Cadastrar um novo usuário no sistema
- Em SQL: `INSERT INTO tabela (colunas) VALUES (valores)`
- Com ORM: `novo_item = Modelo.create(dados)`

## R - Read (Ler)
- Consultar/visualizar dados existentes
- Exemplo: Listar todos os produtos de uma loja
- Em SQL: `SELECT * FROM tabela`
- Com ORM: `itens = Modelo.objects.all()`

## U - Update (Atualizar)
- Modificar dados existentes
- Exemplo: Alterar o preço de um produto
- Em SQL: `UPDATE tabela SET coluna=valor WHERE condição`
- Com ORM: `item = Modelo.get(id); item.campo=valor; item.save()`

## D - Delete (Excluir)
- Remover dados permanentemente
- Exemplo: Apagar um comentário
- Em SQL: `DELETE FROM tabela WHERE condição`
- Com ORM: `item = Modelo.get(id); item.delete()`

## Por que CRUD é importante?

1. **Base de qualquer aplicação**: Quase todo sistema precisa dessas operações
2. **Padronização**: Cria uma linguagem comum entre desenvolvedores
3. **Simplicidade**: Divide operações complexas em ações básicas

## Exemplo Prático (Redes Sociais):

- **Create**: Postar uma nova foto
- **Read**: Ver o feed de notícias
- **Update**: Editar a legenda de uma foto
- **Delete**: Remover um post

CRUD é o ABC da programação com bancos de dados - quase tudo que fazemos se resume a essas quatro operações!