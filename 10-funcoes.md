## AULA 10: Funções

Até o momento já estamos bastante familiarizados com o uso de funções, como ```print()```, ```input()```, e ```len()```, para citar apenas três. Formalmente, definimos função como um bloco de código que só é executado quando é chamado. Você pode passar dados (parâmetros) como entrada para funções e retornar dados como resultado. Nesta aula aprenderemos como construir nossas próprias funções em Python.

### Uma definição visual

Imagine uma função como sendo uma caixinha. Dentro dessa caixinha temos o código da função, ou seja, o conjunto de instruções que ela executa. A caixinha pode receber, através de entradas, dados para serem processados, que representamos por setas entrando pelo lado esquerdo. Do mesmo jeito, o código da função pode gerar um ou mais resultados, representados por setas saindo pelo lado direito. Toda combinação de entrada e saída é possível: com entradas e sem saídas, sem entradas e com saídas e sem nenhum nem outro; a forma da caixinha é você quem decide.

Usando essa analogia, vamos imaginar uma função que soma dois números e retorna o resultado; seu nome será convenietemente escolhido como ```soma()```:

![Exemplo de função representado por caixinha](https://i.imgur.com/29EtgGx.png)

Nesse exemplo, a nossa função ```soma()``` possui duas entradas: ```a``` e ```b```. Em jargão de programação, as entradas são chamadas de **parâmetros** e são colocadas entre parênteses logo após o nome da função, como podemos ver na imagem. Dentro da caixinha temos o conjunto de instruções, que nesse exemplo são apenas duas, mas que podem ser bem mais dependendo da complexidade da nossa função; o conjunto de instruções de uma função recebe o nome de **escopo**. Para "abrirmos um buraco" no lado direito da caixinha e assim retornar valores, usamos a instrução ```return``` seguida dos dados que queremos retornar como resultado; no exemplo, estamos retornando o valor ```c``` que guarda a soma de ```a``` com ```b```.

Finalmente, podemos implementar essa caixinha em Python. Para isso, falta apenas apresentar a instrução usada para definir uma função: ```def```:

```python
def soma(a, b):
    c = a + b
    return c
```

Primeiro, damos um nome à nossa função. Depois, passamos a lista de parâmetros entre parênteses, separados entre si por vírgula. Terceiro, fechamos essa primeira linha com o dois-pontos ```:```. Essa linha que definie o nome e os parâmetros da função é chamada de **assinatura**.

Escrevemos nas linhas seguintes o bloco de código da função. Assim como os outros blocos de código que já vimos, como o do ```if``` e o do ```while```, é a identação que define quando o bloco começa e termina. Portanto, é a identação que diz quando a função começa e termina. No caso da função ```soma()```, o bloco de código possui apenas duas linhas, mas poderia ter apenas uma como várias.

### Chamando uma função

A chamada de uma função que foi criada por nós segue a mesma sintaxe das funções já existentes no Python: o nome da função seguido de parênteses com os possíveis parâmetros na ordem que foram definidos:

```python
def soma(a, b):
    c = a + b
    return c

resultado = soma(4, 5)
print(resultado)
#>9
```

Como ```soma()``` é uma função que retorna valores, podemos armazenar seu resultado em uma variável

### Funções que não retornam resultados: a palavra ```None```

Como vimos na introdução visual, podemos ter qualquer combinação entre entradas e saídas, inclusive funções que não tem saídas. Imagine a função abaixo que diz "Oi" para uma pessoa:

```python
def saudacao(nome):
    print("Olá, {}!".format(nome))

saudacao("Artur")
#>Olá, Artur!
saudacao("Samuel")
#>Olá, Samuel!
```

Perceba que a função ```saudacao()``` não faz uso da instrução ```return```, ou seja, não tem retorno explícito. Se por um acaso tentarmos guardar o retorno dessa função em uma varíavel, o que acontece?

```python
def saudacao(nome):
    print("Olá, {}!".format(nome))

resultado = saudacao("Artur")
#>Olá, Artur!
print(resultado)
#>None
```

Note que, ao chamarmos a função, ela executou normalmente. Seu retorno foi armazenado na variável ```resultado``` e, quando tentamos imprimí-la na tela, apareceu a palavra ```None```. Em Python, ```None``` significa "nada". Toda função que não tem retorno retorna "nada", ou seja, ```None```.

### Funções que retornam mais de um resultado

Uma função pode retornar múltiplos valores como resultado, basta sequenciar um conjunto de valores separados por vírgula após a instrução ```return```. Um retorno múltiplo é tratado como uma tupla, portanto usamos desempacotamento na hora de guardar os resultados em variáveis.

Imaginemos uma função que retorna tanto o seno quanto o cosseno de um certo ângulo em radianos:

```python
import math

def seno_cosseno(angulo):
    seno = math.sin(angulo)
    cosseno = math.cos(angulo)
    return seno, cosseno

res_seno, res_cosseno = seno_cosseno(3.14)
print(res_seno)
#>0.0015926529164868282
print(res_cosseno)
#>-0.9999987317275395
```

Se formos imaginar a função ```seno_cosseno()``` como uma caixinha, ela teria apenas uma seta de entrada e duas setas de saída. Na hora da chamada à função, posicionamos as varíaveis que guardarão os resultados na mesma sequência que o retorno foi definido.

### Número fixo de parâmetros

Por padrão, uma função deve ser chamada passando exatamente a quantidade de parâmetros que fora definidos. No caso da nossa função ```soma()``` que espera dois parâmetros, caso passemos menos de 2 ou mais que 2 o interpretador disaparará um erro:

```python
def soma(a, b):
    c = a + b
    return c

resultado = soma(10)
#>TypeError: soma() missing 1 required positional argument: 'b'
```

Veremos a seguir outras maneiras de definir a quantidade de argumentos.

### Número variado de parâmetros

Você já deve ter se perguntado por quê podemos passar quantos parâmetros quisermos para a função ```print()``` e ela funciona perfeitamente bem em todos os casos. Esse comportamento é possível porque Python possui uma sintaxe que permite passarmos um número variável de parâmetros. Para isso, defina uma função com apenas um parâmetro e posicione um ```*``` antes do nome dele. Assim, Python enxergará esse parâmetro como uma tupla de valores e, portanto, podemos acessar sequencialmente usando o operador de acesso ```[]``` ou de forma iterativa com um laço ```for```. Exemplos:

```python
def exemplo_acesso(*parametros):
    print("Esse é o terceiro parâmetro:", parametros[2])

exemplo_acesso("ednaldo", "birina", "fleige")
#>Esse é o terceiro parâmetro: fleige

# No exemplo acima, o função geraria um erro caso passâsemos menos de 3 parâmetros
# Portanto, é mais comum tratar número variado de parâmetros percorrendo-os com for
# Os exemplos abaixo mostram como

def saudacoes(*nomes):
    for nome in nomes:
        print("Olá, {}!".format(nome))

saudacoes("artur", "hugo")
#>Olá, artur!
#>Olá, hugo!
saudacoes("bruno")
#>Olá, bruno!
saudacoes("hamlet", "caio", "ednaldo", "birinha")
#>Olá, hamlet!
#>Olá, caio!
#>Olá, ednaldo!
#>Olá, birinha!

def multi_soma(*valores):
    c = 0
    for valor in valores:
        c = c + valor
    return c

res1 = multi_soma(1, 2, 3)
print(res1)
#>6
res2 = multi_soma(10, 20, 30, 5, 7, 33)
print(res2)
#>105
res3 = multi_soma()
#>0
res4 = multi_soma(4)
#>4
```

### Chaveando argumentos

Vimos que, por definição, chamamos uma função passando os parâmetros na ordem que estes foram definidos. Entretanto, Python permite que a ordem dos parâmetros seja embaralhada na chamada da função. Para isso, basta passarmos os valores dos parâmetros usando explicitamente os nomes dos respectivos parâmetros numa sintaxe ```nome=valor```:

```python
def filhos(filho1, filho2, filho3):
    print("O filho mais novo é {}".format(filho3))

filhos("joão", "augusto", "matheus")
#>O filho mais novo é matheus
filhos(filho3="matheus", filho1="joão", filho2="augusto")
#>O filho mais novo é matheus

# Mesmo resultado em ambos os casos seja passando em ordem ou usando nome=valor
```

O uso da sintaxe ```nome=valor``` é mais comum quando tratamos de parâmetros com valor pré-definido, o próximo tópico que veremos.

### Parâmetros com valores pré-definidos

Valores pré-definidos ou valores padrão, como os nomes já sugerem, são maneiras de garantir que alguns parâmetros tenham valores passados para a função em casos quando não escolhemos esses valores explicitamente. Para definir um valor padrão, usamos a sintaxe ```nome=valor``` na definição da função; caso aquele parâmetro não receba um valor na hora da chamada da função, o valor usar será o pré-definido:

```python
def comida_favorita(comida="pizza")
    print("A minha comida favorita é {}".format(comida))

comida_favorita("pastel")
#>A minha comida favorita é pastel
comida_favorita("acarajé")
#>A minha comida favorita é acarajé
comida_favorita()
#>A minha comida favorita é pizza
comida_favorita("canjica")
#>A minha comida favorita é canjica

# No exemplo abaixo, a função raiz() tem dois parâmetros: radicando e indice
# Por padrão, indice vale 2, o que significa que calculamos raízes quadradas
# Porém,se passarmos um outro valor no parâmetro indice, mudaremos o tipo de raíz

def raiz(radicando, indice=2):
    r = radicano**(1/indice)
    return r

print(raiz(4))
#>2
print(raiz(9))
#>3
print(raiz(125, 3))
>#4.999999999999999
```

### Funções em construção: a instrução ```pass```

Funções não podem ser vazias, ou seja, não possuirem linhas de código em seu bloco. Entretanto, quando queremos apenas definir a assinatura da função e construí-la depois, podemos preencher o bloco apenas com a instrução ```pass```, que significa algo como "ignore por enquanto".

```python
def conjunto_mandelbrot(z, c):
    # ainda estou estudando como esse conjunto funciona
    # o que sei por enquanto é que preciso de dois parâmetros: z, c
    # volto quando eu absolver mais
    pass
```

### Nomes e números variados de parâmetros

Quando vimos número variado de parâmetros, aprendemos que podemos passar uma tupla de valores para a função usando a sintaxe ```*``` antes do nome do único parâmetro. Se por um acaso quisermos definir, além dos múltiplos valores, os nomes dos parâmetros, usamos uma sintaxe semelhante, mas agora com dois asteriscos ```**``` antes do nome do único parâmetro. Dessa forma, estaremos passando um dicionário para a função, de tal forma que cada par ```nome=valor``` passado como parâmetro será interpretado como um elemento respectivo ```chave=valor``` do dicionário:

```python

# PRIMEIRO EXEMPLO: mostrando que o parâmetro construído é um dicionário
# aqui não fazemos uso direto de alguma chave, apenas mostramos o conteúdo completo

def configuracao(**arg):
    print(arg)

configuracao(ip="localhost", porta=26225)
#>{'ip': 'localhost', 'porta': 26225}
configuracao(sistema="linux", versao=5.12, distro="Ubuntu")
#>{'sistema': 'linux', 'versao': 5.12, 'distro': 'Ubuntu'}

# SEGUNDO EXEMPLO: esperando um valor específico dentre os parâmetros passados
# como o único parâmetro é um dicionário, podemos acessar os valores através de chaves

def conexao(**arg):
    print("Tentando conexão na porta {}".format(arg["porta"]))
    print("Todos os parâmetros: {}".format(arg))

conexao(porta=666, sistema="Linux")
#>Tentando conexão na porta 666
#>Todos os parâmetros: {'porta': 666, 'sistema': 'Linux'}
conexao(porta=2255, sistema="Windows", versao=10)
#>Tentando conexão na porta 2255
#>Todos os parâmetros: {'porta': 2255, 'sistema': 'Windows', 'versao': 10}

# Caso chamemos conexao() sem um parâmetro com nome porta, geraremos um erro de chave:

conexao(sistema="Windows", versao="XP")
#>KeyError: 'porta'
```

### Variáveis que guardam funções

É possível armazenar uma função em uma varíavel. Atenção: não o valor de retorno de uma função, mas a própria função. Imagine que você precise executar uma certa função com base numa escolha feita pelo usuário; por exemplo, qual operação matemática num programa de calculadora. Python permite que guardemos o nome de uma função em um variável e, assim, chamar a função em questão via essa variável. Variáveis que guardam funções são normalmente chamadas de "variáveis coringa".

Atribuímos uma função a uma variável usando o operador ```=``` onde na esquerda temos a variável e na direita apenas o nome da função. Por exemplo:

```python
# usaremos a função exit() do módulo sys para abortar o programa em caso de erro
import sys

def soma(a, b):
    return a + b

def subtrai(a, b):
    return a - b

def multiplica(a, b):
    return a * b

def divide(a, b):
    return a / b

# a variável operacao é iniciada com None para indicar que ela não guarda nada até o momento
# dependendo da escolha do usuário, operacao receberá uma das 4 funções que escrevemos

operacao = None
print("Escolha a operação que executarei em cima de 10 e 2:")
print("1- Soma\n2- Subtração\n3- Multiplicação\n4- Divisão")
escolha = int(input("> "))

if escolha == 1:
    operacao = soma
elif escolha == 2:
    operacao = subtrai
elif escolha == 3:
    operacao = multiplica
elif escolha == 4:
    operacao = divide
else:
    print("Opção inválida!")
    sys.exit()

# se a escolha tiver sido válidam, operacao guarda uma das funções que definimos
# podemos chamar a função de maneira direta através da variável operacao
# imagine que a variável é um "coringa"

resultado = operacao(10, 2)
print("Resultado:", resultado)
```
