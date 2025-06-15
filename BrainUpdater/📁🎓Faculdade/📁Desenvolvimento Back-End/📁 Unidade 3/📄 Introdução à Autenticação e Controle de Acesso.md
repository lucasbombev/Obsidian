tags: #BackEnd #Concurso #Faculdade 
___
## Autenticação
Começamos com o processo de verificar a identidade do usuário.
O objetivo é garantir que o usuário seja quem ele diz ser.
Exemplo: Login com um e-mail e senha.
## Autorização
O processo de verificar os privilégios e permissões de um usuário autenticado
Define o que o usuário pode acessar ou fazer no sistema
Exemplo: Apenas admins podem excluir usuários ou acessar dados confidenciais.
___
## Tipos Comuns de Autenticação
Autenticação por Senha: Usuário fornece um nome de
usuário e senha. O sistema verifica se a combinação está correta.
Exemplo: Login em redes sociais como Facebook ou Instagram.

Autenticação por Token: Usuário recebe um token após o login, que é enviado em cada requisição subsequente.
O token pode ser um JSON Web Token (JWT) ou outro tipo de token.
Exemplo: APIs RESTful que utilizam JWT para autenticação.

Autenticação Multifator (MFA): Requer múltiplas formas
de verificação.
Combina algo que o usuário sabe (senha) com algo que ele tem (código enviado por SMS) ou é (biometria).
Exemplo: Verificação em duas etapas no Google.
___
## JWT (JSON Web Token)

Padrão aberto usado para :
- Transmitir informações entre partes de forma segura como objetos JSON.
- Garantir a integridade e autenticidade dos dados com assinaturas.
é composto por:
**Header** (Cabeçalho): Contém o tipodo token e o algoritmo de assinatura
![[Pasted image 20250614011745.png]]
**Payload** (Carga de Dados): Contém as informações (claims) que serão transmitidas 
![[Pasted image 20250614011810.png]]
**Signature** (Assinatura): Verifica a integridade dos dados.
Gerada a partir do header, payload e uma chave secreta
___
## Fluxo Básico JWT

O usuário faz login e o servidor gera um JWT com os dados do usuário.
O cliente armazena o token (normalmente no local Storage ou em um cookie).
Em cada requisição, o cliente envia o JWT no header (Authorization) para que o
servidor valide o acesso.

___
## Por que usar?
É estateless: O servidor não precisa armazenar sessões, apenas verifica o
token recebido.
Fácil de integrar com APIs RESTful.
___
## Proteção de Rotas com Middleware de Autenticação
## O que é?
uma função que verifica o JWT antes de permitir o acesso a uma rota protegida.
serve para restringir o acesso apenas a usuários autenticados.
