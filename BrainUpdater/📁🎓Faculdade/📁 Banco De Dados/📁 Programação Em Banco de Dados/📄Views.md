tags: #BancoDeDados #Faculdade #Concurso 
___
## O que são views
Views são tabelas virtuais que não armazenam dados fisicamente, mas sim representam uma consulta SQL armazenada no banco de dados. Elas funcionam como "janelas" ou "perspectivas" sobre os dados reais das tabelas.
- Quando você cria uma view, está salvando uma query SQL com um nome
- Ao consultar a view, o SGBD executa a query subjacente e retorna os resultados
- Os dados sempre vêm das tabelas originais (chamadas de tabelas base)
## Características
1. **Virtual**: Não ocupam espaço físico (a menos que sejam materializadas)
2. **Dinâmicas**: Refletem sempre os dados atuais das tabelas base
3. **Segurança**: Podem restringir acesso a colunas sensíveis
4. **Simplificação**: Escondem complexidades de queries complicadas

exemplo:
```sql
CREATE VIEW vw_clientes_simples AS
SELECT id, nome, email, telefone FROM clientes WHERE ativo = 1;
```

## Vantagens das Views:

- **Segurança**: Restringir acesso a dados sensíveis
- **Simplicidade**: Esconder queries complexas
- **Consistência**: Padronizar a forma de acessar dados
- **Independência**: Permite mudar tabelas sem afetar aplicações que usam a view.
