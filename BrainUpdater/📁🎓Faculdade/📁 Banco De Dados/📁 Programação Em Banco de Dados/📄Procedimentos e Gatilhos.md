tags: #BancoDeDados #Faculdade #Concurso 
___
# Procedimentos Armazenados e Gatilhos (Triggers) em Bancos de Dados

Vou explicar esses dois conceitos importantes do seu curso de Banco de Dados para Sistemas para Internet:

## **Procedimentos Armazenados (Stored Procedures)**

### O que são?
São blocos de código SQL armazenados no servidor do banco de dados que podem ser chamados por aplicações. São como "funções" do banco de dados.

### Características principais:
- Armazenados no SGBD (Sistema Gerenciador de Banco de Dados)
- Podem receber parâmetros de entrada e retornar valores
- Contêm lógica de programação (condicionais, loops, etc.)
- Executam operações complexas diretamente no servidor

### Exemplo em SQL (MySQL):
```sql
DELIMITER //
CREATE PROCEDURE sp_cadastrar_cliente(
    IN p_nome VARCHAR(100),
    IN p_email VARCHAR(100),
    OUT p_mensagem VARCHAR(100)
)
BEGIN
    INSERT INTO clientes(nome, email) VALUES(p_nome, p_email);
    SET p_mensagem = 'Cliente cadastrado com sucesso!';
END //
DELIMITER ;

-- Chamando o procedimento
CALL sp_cadastrar_cliente('João Silva', 'joao@email.com', @msg);
SELECT @msg;
```

### Vantagens:
- Melhor desempenho (execução no servidor)
- Redução de tráfego de rede
- Reutilização de código
- Maior segurança (controle de acesso)

---

## **Gatilhos (Triggers)**

### O que são?
São procedimentos automáticos que são executados em resposta a eventos específicos em uma tabela (INSERT, UPDATE, DELETE).

### Características principais:
- Disparados automaticamente pelo SGBD
- Associados a uma tabela específica
- Executados antes ou depois do evento
- Não recebem parâmetros explicitamente

### Exemplo em SQL (MySQL):
```sql
CREATE TRIGGER tg_auditoria_clientes
AFTER UPDATE ON clientes
FOR EACH ROW
BEGIN
    INSERT INTO auditoria(tabela, acao, dados, usuario, data)
    VALUES ('clientes', 'UPDATE', CONCAT('ID:', OLD.id), CURRENT_USER(), NOW());
END;
```

### Tipos de Triggers:
1. **BEFORE INSERT/UPDATE/DELETE** - Executa antes da operação
2. **AFTER INSERT/UPDATE/DELETE** - Executa após a operação

### Casos de uso comuns:
- Auditoria de dados (log de alterações)
- Validação complexa de dados
- Manutenção de dados derivados
- Replicação de dados entre tabelas

### Vantagens:
- Automatização de tarefas
- Garantia de integridade complexa
- Registro automático de atividades

---

## **Diferenças principais**

| Característica        | Procedimentos Armazenados       | Gatilhos                |
|----------------------|--------------------------------|------------------------|
| Execução             | Chamado explicitamente         | Automático por evento  |
| Parâmetros           | Aceita parâmetros              | Não aceita parâmetros  |
| Associação           | Independente de tabelas        | Vinculado a uma tabela |
| Controle             | Controlado pelo desenvolvedor  | Controlado pelo SGBD   |

Ambos são ferramentas poderosas para implementar regras de negócio diretamente no banco de dados, o que é especialmente útil em aplicações web como as que você está aprendendo a desenvolver.