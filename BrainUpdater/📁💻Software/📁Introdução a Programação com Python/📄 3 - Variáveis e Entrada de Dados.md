Tags: #Python #Lógica #Software 
___

## Nomes de Variáveis 
Em python nomes de variáveis pode começar com letra <font color="#4f81bd">minuscula</font> ou <font color="#4f81bd">sublinha (_)</font>
após o primeiro caractere pode conter letras, números e sublinha.
## Variáveis Numéricas
Dizemos que uma variável é numérica quando ela armazena um número inteiro ou de ponto flutuante.
Python possui outros tipos de dados numéricos como <font color="#4f81bd">complex, decimal e fraction</font>

sublinha, assim como o ponto, pode ser usado para separar números grandes no Python. e também pode ser combinado com o ponto: 1_000 (mil)
## Representação de Valores Numéricos
Para números inteiros Python utiliza um sistema de precisão ilimitada que permite a representação de números inteiros muito grandes. Você pode calcular em Python valores como: 2¹⁰⁰⁰⁰⁰⁰

Em ponto flutuante temos limite e problemas de representação.
Vejamos: O número 0.1 não tem nada de especial no sistema decimal, mas é uma dizima periódica no sistema binário.
___
## Variáveis do Tipo Lógico
Armazenam Valores Lógicos ou Booleanos:


```python
verdadeiro = True
falso = False
```

## Operadores Relacionais
Para realizarmos comparações lógicas, utilizaremos operadores relacionais

| ==  | igual          |
| --- | -------------- |
| >   | maior que      |
| <   | menor que      |
| !=  | diferente      |
| >=  | maior ou igual |
| <=  | menor ou igual |
O resultado da comparação de operadores relacionais, vai resultar em um valor lógico, ou seja True ou False

## Operadores Lógicos
Para agrupar operadores com lógica booleana usamos operadores lógicos.
Python suporta três operadores básicos: <font color="#4f81bd">not, and, or</font>

### Operador not
Esse operador é unário, também é chamado de operador de inversão, pois ele inverte o valor booleano.

```python
ex = True
print(not(ex))

```

### Operador and
Esse operador é binário, esse operador resulta verdadeiro apenas quando seus dois operandos forem verdadeiros.

### Operador or
esse operador resulta falso apenas se seus dois operandos forem falsos

___
## Expressões Lógicas
Os operadores lógicos podem ser combinados para formar expressões lógicas mais complexas, quando uma expressão lógica por complexa respeitamos a ordem de precedência.

Ordem de Precedência: not -> and -> or

Os operadores relacionais também podem ser utilizados com operadores lógicos, nesse caso os relacionais são avaliados primeiro.


```python
salario = 100
idade = 20

result = salario > 1000 and idade > 18
# 100 > 1000 and 20 > 18
# False and True
# result == False
print(result)

```

____
## Variáveis de String
As variáveis do tipo string são uma cadeira de caracteres, cada letra ou caractere ocupa uma posição no endereço de memória.

representação de string:

| L   | U   | C   | A   | S   |
| --- | --- | --- | --- | --- |
| 0   | 1   | 2   | 3   | 4   |

para representarmos o tamanho de uma string utilizamos a função <font color="#4f81bd">len</font>
para acessarmos o indice de uma string, colocamos o indice desejado entre colchetes [ ]


```python
nome = "Lucas"
print(nome[0])
print(nome[4])
# Mostrará 'L' e 's'
```


