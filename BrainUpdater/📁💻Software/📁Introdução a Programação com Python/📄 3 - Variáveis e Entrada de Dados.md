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


## Fatiamento de Strings
O fatiamento permite dividirmos a string em pedaços menores
existem vários recursos de fatiamento, se precisar manipular strings, pesquise.

## Sequências e Tempo
O programa é executado linha por linha, executando as operações descritas no programa uma após a outra, assim como lemos textos no nosso alfabeto.

Exemplo de sequência de tempo:


```python
divida = 0 #1
compra = 100 #2
divida += compra #3
compra = 200 #4
divida += compra #5
compra = 300 #6
divida += compra #7
compra += 0 #8
#note que o programa é executado linha a linnha.
print(divida)

```

em 2 temos a primeira compra no valor de 100, no entanto a dívida continua sendo 0, pois ainda não alteramos seu valor de forma a adicionar a compra realizada. isso é feito em 3. observe que estamos atualizando o valor da dívida com o SEU valor ATUAL mais o valor ATUAL de COMPRA.
Isso se repete até o valor final. em 8 o valor da compra é 0, representado que a pessoa não comprou mais nada.

## Rastreamento
