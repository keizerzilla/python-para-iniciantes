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

Primeiro, damos um nome à nossa função. Depois, passamos a lista de parâmetros entre parênteses, separados entre si por vírgula. Terceiro, fechamos essa primeira linha com o dois-pontos ```:```. Escrevemos nas linhas seguintes o bloco de código da função. Assim como os outros blocos de código que já vimos, como o do ```if``` e o do ```while```, é a identação que define quando o bloco começa e termina. Portanto, é a identação que diz quando a função começa e termina.

### Chamando uma função

A chamada de uma função que foi criada por nós segue a mesma sintaxe das funções já existentes no Python: o nome da função seguido de parênteses com os possíveis parâmetros:

```python
def soma(a, b):
    c = a + b
    return c

resultado = soma(4, 5)
print(resultado)
#>9
```

Como ```soma()``` é uma função que retorna valores, podemos armazenar seu resultado em uma variável

### Funções que não retornam valores: a palavra ```None```

Como vimos na introdução visual, podemos ter qualquer combinação entre entradas e saídas, inclusive funções que não tem saídas. Imagine a função abaixo que diz "Oi" para uma pessoa:

```python
def saudacao(nome):
    print("Olá, {}!".format(nome))

saudacao("Artur")
#>Olá, Artur!
saudacao("Samuel")
#>Olá, Samuel!
```

Se por um acaso tentarmos guardar o retorno dessa função em uma varíavel, o que acontece?

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

Você já deve ter se perguntado por quê podemos passar quantos parâmetros quisermos para a função ```print()``` e ela funciona perfeitamente bem em todos os casos. Esse comportamento é possível porque Python possui uma sintaxe que permite passarmos um número variável de parâmetros. Para isso, defina uma função com apenas um parâmetro e posicione um ```*``` antes do nome dele. Assim, Python enxergará esse parâmetro como uma tupla de valores e, portanto, podemos acessar sequencialmente usando o operador de acesso ```[]``` ou de forma iterativa com um laço ```for```. Exemplo:

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
