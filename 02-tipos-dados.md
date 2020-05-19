## PARTE 02: TIPOS DE DADOS

Vimos que variáveis são compartimentos da memória que armazenam dados. Nos exemplos mostrados já foi possível ter uma noção dos **tipos de dados** possíveis que podemos armazenar. Agora vamos formalizar os tipos de dados possíveis em Python. Outras linguagens de programação podem apresentar mais ou menos possibilidades de tipos possíveis.

Podemos agrupar os tipos possíveis no Python em algumas categorias:

| CATEGORIA  | TIPOS                                          |
|------------|------------------------------------------------|
| Numérico   | ```int```, ```float```, ```complex```          |
| Texto      | ```str```                                      |
| Lógico     | ```bool```                                     |
| Sequência  | ```list```, ```tuple```, ```range```           |
| Mapeamento | ```dict```                                     |
| Conjunto   | ```set```, ```frozenset```                     |
| Binário    | ```bytes```, ```bytearray```, ```memoryview``` |

Vamos detalhar as três primeiras categorias por enquanto, por estas serem as mais comuns. As demais terão atenção particular em momento oportuno.

**1- Numérico:** tipos de números. int são dados inteiros, também conhecidos como "números naturais" (-5, 2, 0, 666, 3, 8, 10, etc). float armazena dados "ponto flutuante", também conhecidos como "número racionais", "decimais" ou "quebrados" (3.14, 5.5555556, 78.9, etc). complex armazena os "números complexos", também chamados de "números imaginários" (1+3j, -5+2j, 6j, etc).

**2- Texto:** armazena texto. Possui apenas um tipo, str, chamado *string*, também conhecido como sequência de caractéres, texto e cadeia de caractéres. O jargão de programação mais comum é string.

**3- Lógico:** dados de natureza lógica binária, ou "números booleanos". Um dado bool só pode receber dois valores possíveis: True ou False.

Python é inteligente o suficiente para detectar o tipo do dado guardado em uma variável. Ou seja, você não precisa especificar que vai guardar um inteiro ou uma string:

```python
a = 2 # python detecta automaticamente que a é um int
b = "tutu" # python detecta automaticamente que b é uma str
c = True # python detecta automaticamente que c é um bool
d = 6.28 # python detecta automaticamente que d é um float
e = 1+3j # python detecta automaticamente que e é um complex
```

Isso também permite que uma variável troque de tipo quando se troca o dado que ela guarda. Em outras palavras, uma variável que nasceu como inteira se torna string ou ponto flutuante no momento que se troca o dado que ela guarda:

```python
a = 45 # a inicia como variável int
a = 45.2 # agora, a é uma variável float
a = "quarenta e cinco ponto dois" # agora, uma str
```

**Trocar o tipo** de uma variável ao trocar o valor que ela guarda não é a mesma coisa que **conversão de tipo**! Falaremos de conversão na última seção desta parte.

Mesmo sendo possível essa troca de tipo dinamicamente, não é considerado uma boa prática de programação resignificar uma variável num mesmo programa. Se suas variáveis representam coisas muito diferentes em momentos diferentes do programa, isso tornará seu código mais difícil de ser lido e interpretado por outras pessoas (ou por você mesmo, no futuro distante aonde você não lembra mais o que escreveu). Portanto, se uma variável chamada ```num``` foi criada carregando um número ponto flutuante, é boa prática que ela permaneça armazenando pontos flutuantes por toda a vida.

### type()

Python possui uma função muito útil capaz de retornar o tipo de dado de uma variável: type()

```python
raiz = 4
print(type(raiz))
#>>int
```

```python
cpf = "123456789"
print(type(cpf))
#>>str
```

A função type() é muito importante quando se deseja testar o tipo de uma variável antes de tentar realizar uma operação sobre ela, evitando assim possíveis erros.

### Conversão de Tipos

Vimos que uma variável pode armazenar tipos diferentes em momentos diferentes do programa, bastando apenas que troquemos o valor que ela guarda. Essa transformação exige que o programador troque, de maneira estática, o valor por outro. Agora, existem casos aonde é possível trocar o tipo da variável se houver compatibilidade entre eles. Chamamos essa troca de conversão. Um exemplo:

```python
num1 = "34"
print(type(num1))
#>>str

# num1 é uma variável que guarda a string "34"
# o resultado da função type(), portanto, será str
# reflexão: "34" string e 34 inteiro parecem semelhantes entre si...
# pergunta: é possível converter "34" em 34?
# resposta: SIM! basta usar o tipo para onde se quer converter como uma função!

num2 = int(num1)
print(type(num2))
#>>int

# num2 foi gerada a partir da conversão de num1 em int
# o resultao de type(), agora, será int!
# reflexão: perceba que usamos o nome do tipo como uma função, no caso int()
# pergunta: poderíamos converter para float usando a mesma lógica?
# resposta: SIM!

num3 = float(num1)
print(type(num3))
#>>float

# veja que, agora, convertemos de str para float
# pergunta: podemos fazer o caminho inverso?
# resposta: SIM de novo! como queremos agora uma string a partir de um número, usamos str()

num4 = str(num2)
print(type(num4))
#>>str
```

De maneira resumida:

- usa-se ```int()``` para tentar converter uma variável em inteiro
- usa-se ```float()``` para tentar converter uma variável em ponto flutuante
- usa-se ```str()``` para tentar converter uma variável em string

### Caso mais comum de conversão: função input()

Vamos aprender uma coisa nova sobre a função input(). Você já sabe que nós a usamos para capturar um valor entrado via teclado. **Pergunta: a função input() consegue detectar automaticamente o tipo da informação entrada?**

A resposta, infelizmente, é **não**. A função input() retorna toda informação passada para ela como string. É fácil testar:

```python
raio = input("Qual o raio do círculo? ")
#>>6.66
print(type(raio))
#>>str
```

No exemplo acima, a razão nos diz que a variável ```raio``` deve ser tratada como um número real (em jargão de programação: ponto flutuante). Mas a função input() não tenta adivinhar o tipo da informação; é responsabilidade do programar realizar a **conversão de tipo**. Para isso, basta usar as funções de tipo que vimos na seção anterior. Refazendo o exemplo:


```python
raio = input("Qual o raio do círculo? ")
#>>6.66
raio = float(raio)
print(type(raio))
#>>float
```

Pronto, agora podemos manipular ```raio``` como uma variável ponto flutuante. Podemos realizar multiplicações, adições, divisões... Outro detalhe é que o código acima não criou uma nova variável (por exemplo, ```raio2```) só para guardar o resultado da conversão. Podemos reusar a variável que já tinhamos. Essa ressignificação é válida, além de boa prática de programação!
