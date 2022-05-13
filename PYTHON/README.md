# Python

Created: February 27, 2022 4:19 PM
Tags: back, python

# VARIÁVEIS

Variáveis são, na verdade, objetos, na linguagem Python.

## DECLARAÇÃO

```python
variavel = "istó é uma variável";

#Tipos

inteiro = 1
decimal = 1.0
texto = "hello world"
complexos = 1 + 2j
```

## FLOAT

```python
varFloat = 0.0

#limita num de casas decimais
round(varFloat, 2)
print("%0.2f" %varFloat)
```

## STRING

```python
varString = " "

#Pula uma linha
print(varString, "\n", varString)
```

## ARRAY

```python
#type: list

varArray = []
varArray = list()

VarArray = [1, 2, 3]
VarArray = list([1, 2, 3])

V = [a for a in range(5)] # gera a lista [0, 1, 2, 3, 4]
M = [x*2 for x in range(3)] # gera a lista [0, 2, 4]

#NEW DATA
#adiciona novos campos
varArray.append("newData")

L.insert(3, 59) # acrescenta o valor 59 na posição 3 da lista

#PRINTS
#Quebra o array para string
print("\n".join(map(str, varArray))) #após converter p/ string, substitui os intervalos do array por "enter"

print(varArray[1]) #Printa o índice 1

MinhaLista = [2, 4, 6, 8]
for N in MinhaLista:
 print(N)

#GERAR O ÍNDICE E O VALOR
Cardapio = ['pizza', 'massa', 'salada', 'churrasco']
print('As possibilidades são:')
for indice, item in enumerate(Cardapio):
 print(indice, item)

#COPIANDO 
#Aponta pro mesmo objeto e pode afetar a memória
L1 = [6, 7, 8, 9]
L2 = L1

#CLONANDO
#Cria um novo objeto
L1 = [6, 7, 8, 9]
L2 = L1[:]

#JUNTANDO LISTAS
m = [1, 2, 3]
n = [4, 5, 6]
o = m + n
print(o) # [1, 2, 3, 4, 5, 6]
o += [7, 8, 9]
print(o) # [1, 2, 3, 4, 5, 6, 7, 8, 9]

#FUNÇÕES
.append()
.index() # mostra o índice do valor inserido
.insert()
           animals = ["ant", "bat", "cat"]
           animals.insert(1, "dog")
           print(animals) # ["ant", "dog", "bat", "cat"]
.remove
           animals = ["ant", "bat", "cat"]
           animals.remove("ant")
           print(animals) # ["bat", "cat"]
.pop #Remove através do índice
           animals = ["ant", "bat", "cat"]
           animals.pop(0) # 'ant'
           print(animals) # ["bat", "cat"]
.sort #Deixa a lista em ordem crescente.
sorted([])

#HÁ ELEMENTOS?
>>> animals = ["ant", "bat", "cat"]
>>> 'dog' in animals
False
>>> 'cat' in animals
True

```

# OPERADORES

| + | Soma |
| --- | --- |
| - | Subtração |
| * | Multiplicação |
| / or // | Divisão |
| % | Resto |
| ** | Potência |
| == | igualdade |
| < | menor q |
| >  | maior que |
| < = or > =  | ma or me or igual |
| ! = | diferente |

# PRINT DE DADOS

```python
print(var1, var2)

print("%0.2f" %var1) #Variável irá ocupar 2 casas depois da vírgula

print("{} {}".format(var1, var2)) 

print("{:5}".format(var1)) #variável vai ocupar 5 casas, mesmo vazias

```

# ATRIBUIÇÕES

```python
a = float(18) # transforma variáel em float, mesmo sendo a entrada de um inteiro

a = input("Digite: ") # permite entrada de dados

a = float(input("Digite: ")) # entrada de dados convertida para float

a, b = input().split() #permite a entrada de dois valores na mesma linha 

#funções de conversão
int()
float()
complex()
str()

type(variavel) #determina o tipo de variável
```

# IF ELSE

## SINTAXE

```python
if (a == b):
#código
elif not(a == b):
#código
else:
#código
```

## OPERADORES LÓGICOS

| A == B | igualdade |
| --- | --- |
| A < B | menor q |
| A > B | maior que |
| A <= B or A >= B  | ma or me or igual |
| A ! = B | diferente |
| and | duas condições |
| or | uma ou outra |
| not(A > B) | se A não for maior que B (negação) |

# LOOP REPETIÇÃO

Um loop de repetição compõe:

- Configuração inicial
- Condição de continuidade
- variável de controle

**ACUMULADOR:** sentença que faz uma var crescer cada vez mais.

## WHILE

### SINTAXE

```python
i = 0
N = 10

while i < N:
  print("Linha", i)
  i += 1

    
```

# CÓDIGOS ÚTEIS

## VERIFICAR SE UM NÚMERO É PRIMO

```python
if N == 2:
    print("{} é primo".format(N))
elif N % 2 == 0:
    print("{} não é primo".format(N))
else:
    raiz = N ** 0.5
    R = 1
    i = 3
    while i <= raiz and R != 0:
        R = N % i
        i += 2
    if R == 0:
        print("{} não é primo".format(N))
    else:
        print("{} é primo".format(N))
```
