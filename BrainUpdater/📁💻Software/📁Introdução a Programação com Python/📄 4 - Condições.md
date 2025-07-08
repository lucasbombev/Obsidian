Tags: #Python #Lógica #Software
___
As condições servem para decidir quando uma parte do programa deve ser ativada e quando deve ser ignorada. em Python a estrutura de decisão é o <font color="#4f81bd">if</font>:
seu formato -> 

if <condição>:
	bloco verdadeiro

programa 4.1 - lê dois valores e imprime qual valor é maior

```python
a = int(input("Primeiro valor: "))
b = int(input("Segundo valor: "))
if a > b:
	print("O primeiro é maior!")
if b > a:	
	print("O segundo é maior!")
```

e se os 2 valores forem iguais? nesse caso nenhum bloco será executado pois nenhuma condição é verdadeira. Veja que se eu digitar 5 e 5, nenhum valor será maior que outro, sendo falsa qualquer comparação de maior.

