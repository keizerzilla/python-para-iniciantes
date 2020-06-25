## AULA 03: OPERADORES

Um operador é um símbolo que manipula valores e variáveis. Podemos agrupar os operadores de acordo com a categoria de tipo que eles manipulam:

| CATEGORIA | OPERADORES                                                      |
|-----------|-----------------------------------------------------------------|
| Numérico  | ```+```, ```-```, ```*```, ```/```, ```%```, ```**```, ```//``` |
| Texto     | ```+```, ```*```                                                |
| Lógico    | ```and```, ```or```, ```not```                                  |

Algumas observações antes de continuarmos. 1) Discutiremos os operadores das categorias *Sequência*, *Mapeamento*, *Conjunto* e *Binário* em tempo oportuno. 2) Existe uma categoria especial de operadores, chamados **operadores relacionais**, que veremos na **Parte 04: Condições**.

### Operadores numéricos

Os operadores numéricos representam operações aritméticas simples, como adição, subtração e potenciação.

```python
# + : adição
a = 32
b = 10
c = a + b
print(c)
#>>42

# - : subtração
a = 120
b = 33
c = a - b
print(c)
#>>87

# * : multiplicação
a = 77.5
b = 2
c = a * b
print(c)
#>>155.0

# / : divisão real (retorna um número ponto flutuante)
a = 16
b = 4
c = a / b
print(c)
#>>4.0

# % : resto da divisão
a = 93
b = 4
c = a % b
print(c)
#>>1

# ** : potenciação (ou exponenciação)
a = 5
b = 4
c = a ** b
print(c)
#>>625

# // : divisão inteira (retorna apenas a parte inteira da divisão)
a = 43
b = 5
c = a // b
print(c)
#>>8
```

É possível serializar um conjunto de operações aritméticas em uma única expressão. A ordem com que as operações serão executadas depende da **prioridade do operador**. Em jargão de programação, prioridade é sinônimo de **precedência**. Os operadores numéricos na tabela estão ordenados em ordem crescente de prioridade/precedência.

É boa prática de programação usar parênteses para delimitar partes menores de expressões aritméticas grandes. Por mais que saibamos da prioridades dos operadores, fica mais legível saber o que é executado primeiro através desse tipo de segmentação.

### Operadores de texto

As duas operações básicas com texto são **concatenação** (```+```) e **multiplicação** (```*```). A concatenação é uma operação que toma duas strings e a une/junta/gruda em uma única string. A multiplicação é o mesmo que um conjunto concatenações em sequência: ela toma uma string e um número inteiro e gera uma string formada pela repetição da string de entrada o número de vezes escolhido. Exemplos:

```python
# + : concatenação
nome = "artur"
sobrenome = " rodrigues"
nome_sobrenome = nome + sobrenome
print(nome_sobrenome)
#>>artur rodrigues

# * : multiplicação
som = "PEI"
papocos = 10
barulho = som * papocos
print(barulho)
#>>PEIPEIPEIPEIPEIPEIPEIPEIPEIPEI
```

### Operadores lógicos

Vimos que Python dá suporte a variáveis do tipo lógico, aquelas que só podem receber os valores Verdadeiro (```True```) e Falso (```False```). A matemática que manipula esses tipos de variável é chamada **Lógica Booleana**. As três manipulações básicas, também chamadas Operações Lógicas ou Operações Booleanas, são: operação **E** (```and```), operação **OU** (```or```) e operação **NÃO** (```not```).

Podemos agrupar todas as possibilidades dessas operações em tabelas conhecidas como **Tabelas Verdade**:

#### TABELA VERDADE ```and```
| ```V1```    | ```V2```    | ```V1 and V2``` |
|-------------|-------------|-----------------|
| ```True```  | ```True```  | ```True```      |
| ```True```  | ```False``` | ```False```     |
| ```False``` | ```True```  | ```False```     |
| ```False``` | ```False``` | ```False```     |

#### TABELA VERDADE ```or```
| ```V1```    | ```V2```    | ```V1 or V2``` |
|-------------|-------------|----------------|
| ```True```  | ```True```  | ```True```     |
| ```True```  | ```False``` | ```True```     |
| ```False``` | ```True```  | ```True```     |
| ```False``` | ```False``` | ```False```    |

#### TABELA VERDADE ```not```
| ```V1```    | ```not V1``` |
|-------------|--------------|
| ```True```  | ```False```  |
| ```False``` | ```True```   |

Em termos de código:

```python
a = True
b = False
c = a and b
print(c)
#>>False

d = False
e = True
f = d or e
print(f)
#>>True

g = False
print(not g)
#>>True
```
