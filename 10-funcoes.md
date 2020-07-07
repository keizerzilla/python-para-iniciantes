
## AULA 10: Funções

Já estamos bastante familiarizados com o uso de funções. Exemplos como ```print()```, ```input()```, e ```len()```, para citar apenas três, já foram usados amplamente em exemplos e exercícios. Agora está na hora de aprendermos a escrever as nossas próprias funções em Python!

### Motivação: por que escrever funções?

Quanto mais longo e complexo um programa, maior a chance de partes dele se repetirem ocasionalmente ao logno do código. Um programa responsável por analisar a emoção descrita em um texto provavelmente executa um conjunto de instruções de leitura de arquivo e cálculo de indíces matemáticos um número repetido de vezes. Ou um programa que procura por rostos numa foto e que precisa executar um algoritmo de indentificação para cada região previamente delimitada da imagem. Nesses e em diveros outros casos, podemos dividir as diversas tarefas que o programa precisa executar (ler arquivo, calcular índices, identifcar rosto, delimitar imagem, etc) em funções. Essa filosofia de dividir uma tarefa complexa em tarefas menores é chamada de **dividir para conquistar**.

Outra vantagem do uso de funções é na manutenção do código. Imagine ter de copiar as mesmas, digamos 5, linhas de código em pontos diferentes de um mesmo programa. Imagine agora que você encontrou um erro na quarta linha desses blocos repetidos; você precisaria corrigir essas mesmas linhas em todas as ocorrências repetidas. Para cada erro encontrado, você precisaria fazer uma correção. Agora, se essas instruções tivessem sido usadas para criar uma função, bastaria você chamá-la em cada ocasião e, na descoberta de erros, bastaria corrigir a definição da função que automaticamente o restante do código se adequaria, pois você deixou de copiar e colar o mesmo código para apenas **chamar um mesmo conjunto de instruções**.

Nesta linha de dividir para conquistar, você perceberá que é mais fácil escrever várias funções pequenas que resolvem problemas específicos do que um grande programa que resolve tudo de uma vez. **Uma função bem escrita executa apenas uma única tarefa**. Assim, nosso programa passa a parecer um conjunto de bloquinhos (as diversas funções) que se juntam e formam a ferramenta que precisámos para resolver o problema geral. Esse é o poder das funções e nesta aula veremos as diversas maneiras de defini-las em Python.

### Uma definição visual

Formalmente, definimos função como _um bloco de código que só é executado quando é chamado_. Você pode passar dados como entrada para funções e retornar dados como resposta. Vamos começar tentando visualizar uma função e seus elementos formadores.

Imagine uma função como sendo uma caixinha. Dentro dessa caixinha temos o código da função, ou seja, o conjunto de instruções que ela executa, aquilo que ela faz. A caixinha pode receber, através de **entradas**, dados para serem processados. Representamos as entradas como setas entrando pelo lado esquerdo da caixinha. Do mesmo jeito, a função pode gerar um ou mais resultados de **saída**, representados por setas saindo pelo lado direito da caixinha. Toda combinação de entrada e saída é possível:

- com entradas e com saídas;
- com entradas, mas sem saídas;
- sem entradas, mas com saídas; e
- sem entradas e sem saídas.

Você quem decide a forma da caixinha!

Por exemplo, vamos pensar uma função que soma dois números e retorna o resultado da adição. Seu nome será convenietemente escolhido como ```soma()```. A caixinha correspondente seria:

![Exemplo de função representado por caixinha](https://i.imgur.com/29EtgGx.png)

A nossa função ```soma()``` possui duas entradas: ```a``` e ```b```. Em jargão de programação, as entradas são chamadas de **parâmetros**.

Dentro da caixinha temos o conjunto de instruções que compõem a função. Nesse exemplo temos apenas duas linhas de código, podendo ser bem mais dependendo da complexidade da função.

Em nosso exemplo, ```soma()``` possui apenas uma **saída**. Para "abrirmos um buraco" na caixinha por onde a saída é retornada, usamos a instrução ```return``` seguida dos dados que queremos retornar; no exemplo, estamos retornando o valor ```c```, que guarda a soma de ```a``` com ```b```.

### Definindo funções em Python: a instrução ```def```

Em Python, uma função é um bloco de código que descreve nome, parâmetros e conjunto de instruções a serem executadas. A palavra ```def``` serve para iniciar a _definição_ de uma função. A estrutura básica de uma função em Python é:

```
def <nome_funcao>(<parametros>):
    <bloco_da_funcao>
```

Vejamos como implementar a caixinha da função ```soma()``` em Python:

```python
def soma(a, b):
    c = a + b
    return c
```

Primeiro, damos um nome à nossa função, no caso _soma_. As regras de nomeação de funções são as mesmas que aplicamos para variáveis. Depois, passamos a lista de parâmetros dentro dos parênteses, separados entre si por vírgula. Caso a função não tenha parâmetros, não colocamos nada dentro dos parênteses. Terceiro, fechamos o ínicio da definição com dois-pontos ```:```. Essa linha que definie o nome e os parâmetros da função é chamada de **assinatura da função** ou somente **assinatura**.

Escrevemos nas linhas seguintes, corretamente identadas à esquerda, o bloco de código da função; assim como os outros blocos de código que já vimos, como o do ```if``` e o do ```while```, é a identação que define quando o bloco começa e termina. Portanto, é a identação que diz quando a função começa e termina.

Pronto, agora sabemos o básico de definição de funções! Mais um exemplo antes de seguirmos com aspectos mais profundos: escrevamos um função que recebe um texto qualquer e o mostra em caixa-alta, caixa-baixa e o seu tamanho:

```python
def sobre_texto(txt):
    print("CAIXA-ALTA: {}".format(txt.upper()))
    print("CAIXA-BAIXA: {}".format(txt.lower()))
    print("TAMANHO: {} caracteres".format(len(txt)))

sobre_texto("Olá, meu nome é Goku!")
#>CAIXA-ALTA: OLÁ, MEU NOME É GOKU!
#>CAIXA-BAIXA: olá, meu nome é goku!
#>TAMANHO: 21 caracteres
```

A função acima toma apenas um parâmetroa, ```txt```, e não tem nenhum valor de retorno; toda sua lógica se resume a mensagem formatadas.

### Parâmetro ou argumento?

É muito comum encontrarmos a palavra "argumento" como sinônimo de parâmetro; em inglês usa-se a palavra _argument_ para representar o conceito de parâmetro. Parâmetro e argumento podem sim serem sinônimos, mas em alguns contextos podem representar coisas diferentes. Usaremos apenas a palavra parâmetro para representar os dados passados como entrada de um função.

### Boas práticas de nomeação de funções

É considerado uma ótima prática de programação nomear as funções de maneira autoexplicativa, mas sem exagerar no tamanho do nome. Nomes genéricos, como ```func()``` ou ```teste()```, não deixam claro o que as funções fazem. Analogamente, nomes como ```calcula_raiz_cubica_numero()``` ou ```conta_palavras_repetidas_textos()``` são exageradamente grandes e, por mais que expliquem bem o que essas funções fazem, poderiam ser trocadas por ```raiz_cubica()``` e ```conta_repetidas()``` sem muita perda de significado, por exemplo.

Em geral, use nome não muito grandes, no máximo 3 palavras, e evite conectores entre essas palavras. Foque a escolha das palavras ao redor do verbo que representa aquilo que a função faz, como contar, calcular, mostrar, descobrir, ser, etc.

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

Acima, a função ```soma()``` foi chamada passando como parâmetros os valores ```4``` e ```5``` que foram associados aos parâmetros ```a``` e ```b```, respectivamente. Como ```soma()``` é uma função que retorna valores, podemos armazenar seu resultado em uma variável, por exemplo ```resultado```. Por fim, usamos a conhecida função ```print()``` para mostrar na tela o resultado.

Por padrão, uma função deve ser chamada passando exatamente a quantidade de parâmetros que foram definidos. No caso da nossa função ```soma()``` que espera dois parâmetros, caso passemos menos de 2 ou mais que 2 o interpretador reclamará com um erro:

```python
def soma(a, b):
    c = a + b
    return c

resultado = soma(10)
#>TypeError: soma() missing 1 required positional argument: 'b'
```

Mais a frente veremos um conjunto de maneiras que Python nos fornece para flexibilizar a definição dos parâmetros.

### Escopos: local e global

O _escopo_ de uma variável se refere aos lugares do código onde você pode acessar essa variável. Indicamos o quão interno ou externo é um escopo através da identação do código; vimos que o bloco de código de um ```if```, por exemplo, definie um nível mais interno, e portanto um escopo mais interno. Se você definir uma variável no topo do seu programa, sem identação alguma, essa variável é dita **global**, pois está no nível mais externo possível e ela será visível em qualquer outro escopo.

Funções, assim como variáveis, também possuem escopo. O escopo de um variável é o lugar do código ocupado pelas suas instruções. Um escopo de uma função é dito **local**.

Vimos também que as funções se comunicam com o código principal através das entradas e saídas. Entretanto, é possível que uma função "enxergue" outras variáveis mesmo que essas não sejam passadas explicitamente via parâmetros. Por exemplo:

```python
pi = 3.14

def area_circulo(raio):
    return pi*raio**2

print(area_circulo(5))
#>78.5
```

A função acima usa a fórmula ```Pi*R²``` para calcular a área de um círculo. Note que o valor do número Pi foi guardado fora do escopo da função, mas ainda assim ela foi capaz de usá-lo no cálculo sem nenhum problema. Isso acontece porque toda variável criada no escopo global é visível em qualquer escopo local. Por mais que isso seja possível, **não é considerado boa prática de programação usar variáveis de um escopo global dentro do escopo local de uma função! Use parâmetros de entrada!**

Agora, se por um acaso você _criar_ dentro de uma função uma variável com o mesmo de outra do escopo global, Python as tratará como duas variáveis diferentes:

```python
nome = "Ednaldo"

def mostra_nome():
    nome = "Birina"
    print(nome)

mostra_nome()
#>Birina
print(nome)
#>Ednaldo
```

Veja que você criou uma variável ```nome``` dentro de ```mostra_nome()``` mesmo depois de, fora da função, ter criado um variável como mesmo nome. Aqui Python tratou as duas variáveis como distintas, por isso que os dois ```print()``` (o de dentro e o de fora da função) mostraram dois nomes diferentes: o local e o gloabl.

Em resumo:

- se você tentar, dentro de uma função, acessar uma variável que não foi passada via parâmetro, Python procurará essa variável no escopo global; e
- se você criar, ainda dentro de uma função, uma variável que possui o mesmo nome que uma do escopo global, Python a considerará como uma variável diferente.

### Mais de uma instrução ```return``` em uma única função

A palavra ```return``` é a instrução usada para definir os valores de saída de uma função. A função termina de ser executada no momento que não há mais linhas em seu bloco de código ou quando ela alcança uma linha com uma chamada ```return```. Isso quer dizer que podemos ter mais de uma linha com ```return```, cada uma representando uma saída possível da nossa função.

Por exemplo, vamos imaginar que nossa função recebe um número e deve retornar ```True``` se o número for par ou ```False``` se ímpar:

```python
def num_par(n):
    if n % 2 == 0:
        return True
    else:
        return False

print(num_par(44))
#>True
print(num_par(5))
#>False
```

Note que a nossa função ```num_par()``` tem duas linhas com chamadas ```return```, uma para cada uma das condições possíveis. Quando a execução alcançar qualquer uma delas, a função termina e o programa continua a execução de onde ela foi chamada.

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

Note que, ao chamarmos a função, ela foi executada normalmente. Seu retorno foi armazenado na variável ```resultado``` e, quando tentamos imprimí-la na tela, apareceu a palavra ```None```. Em Python, ```None``` é uma palavra reservada que  significa "nada". Toda função que não tem retorno retorna "nada", ou seja, ```None```.

**Toda função Python retorna alguma coisa, seja os valores que nós definimos explicitamente usando a instrução ```return```, seja a palavra ```None``` quando não dizemos o que retornar.**

Além desse aspecto técnico, a palavra ```None``` é bastante usada como retorno explícito em casos que a função decidiu que não pode ser executada corretamente, por exemplo em caso de problemas nos parâmetros. Vamos imaginar uma função que toma uma lista de números como entrada e retorna uma lista com os quadrados de cada um desses números. Como queremos fazer acessos e outras manipulações de listas, é importante garantir que o parâmetro passado seja do tipo ```list```. A função, portanto, pode logo de cara testar o tipo do parâmetro usando a função ```type()``` e, caso não seja o correto, encerrar imediatamente retornando ```None``` para indicar que houve um problema:

```python
def quadrados(numeros):
    if type(numeros) != list:
        return None
    
    quad = []
    for num in numeros:
        quad.append(num**2)
    
    return quad

print(quadrados([4, 2, 7, 6, 1]))
#>[16, 4, 49, 36, 1]
print(quadrados("Olá, mundo!"))
#>None
print(quadrados(3.14))
#>None
```

Como vimos em um tópico anterior, a função termina de ser executada em duas ocasiões: quando nã há mais linhas a serem executadas ou quando alcança uma instrução ```return```. No caso da função ```quadrados()```, caso o tipo do parâmetro seja diferente de lista nós abortamos imediatamente a execução e retornamos ```None```.

### Funções que retornam mais de um resultado

Uma função pode retornar múltiplos valores como resultado, basta sequenciar um conjunto deles separados por vírgula após a instrução ```return```. Um retorno múltiplo é tratado como uma tupla, portanto temos duas opções de como guardá-lo:

1. usar a sintaxe de desempacotamento e guardar os valores em varíaveis separadas; ou
2. armazenar o retorno em uma única variável que guardará a tupla inteira

Imaginemos uma função que retorna tanto o seno quanto o cosseno de um certo ângulo em radianos. Se formos imaginar a função ```seno_cosseno()``` como uma caixinha, ela teria apenas uma seta de entrada e duas setas de saída. Em Python:

```python
import math

def seno_cosseno(angulo):
    seno = math.sin(angulo)
    cosseno = math.cos(angulo)
    return seno, cosseno

# DESEMPACOTANDO O RETORNO
seno_pi, cosseno_pi = seno_cosseno(3.14)
print(seno_pi)
#>0.0015926529164868282
print(cosseno_pi)
#>-0.9999987317275395

# GUARDANDO A TUPLA COMPLETA NUMA ÚNICA VARIÁVEL
res = seno_cosseno(2.71)
print(type(res))
#>tuple
print(res)
#>(0.418317940675659, -0.9083006663593701)
```

O exemplo acima chama a função ```seno_cosseno()``` duas vezes: a primeira desempacotando o retorno em duas variáveis separadas e a segunda, guardando a tupla por completo numa variável só. No primeiro caso, posicionamos as varíaveis que guardarão os resultados na mesma sequência que o retorno foi definido.

### Número variado de parâmetros

Você já deve ter se perguntado por quê podemos passar quantos parâmetros quisermos para a função ```print()``` e como ela funciona perfeitamente bem em todos os casos. Esse comportamento é possível porque Python possui uma sintaxe que permite passarmos um número variável de parâmetros. No caso de ```print()```, podemos passar um série de valores que, independente da quantidade, serão igualmente convertidos para strings, concatenado e por fim mostrados na tela.

É muito fácil definir uma função que recebe um número variado de parâmetros. Para isso, defina uma função com apenas um parâmetro e posicione um ```*``` antes do nome dele. Python enxergará esse parâmetro como uma tupla de valores e, portanto, podemos acessá-los sequencialmente usando o operador ```[]``` ou de forma iterativa com um laço ```for```.

O primeiro exemplo prova que o parâmetro é enxergado como uma tupla e que podemos acessar os elementos via índie:

```python
def exemplo_acesso(*param):
    print("Você passou {} parâmetros".format(len(param)))
    print("Esse é o terceiro parâmetro:", param[2])

exemplo_acesso("ednaldo", "birina", "fleige")
#>Você passou 3 parâmetros
#>Esse é o terceiro parâmetro: fleige

# A função geraria um erro caso passâsemos menos de 3 parâmetros (índice 2 não exisitiria).
# Portanto, é mais comum tratar o número variado de parâmetros percorrendo-os com for.
```

Exemplo de função quer percorre todos os parâmetros da tupla gerada (conjunto de nomes) saudando cada um:

```python
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
```

Função que recebe um número variado de número e retorna a soma deles:

```python
def multi_soma(*valores):
    c = 0
    for valor in valores:
        c = c + valor
    return c

print(multi_soma(1, 2, 3))
#>6
print(multi_soma(10, 20, 30, 5, 7, 33))
#>105
print(multi_soma())
#>0
print(multi_soma(4))
#>4

```

### Chaveando parâmetros

Vimos que, por definição, chamamos uma função passando os parâmetros na ordem que estes foram definidos. Entretanto, Python permite que a ordem dos parâmetros seja embaralhada na chamada da função. Para isso, basta passarmos os valores dos parâmetros usando explicitamente os nomes dos respectivos parâmetros numa sintaxe ```nome=valor```:

```python
def filhos(filho1, filho2, filho3):
    print("O filho mais novo é {}".format(filho3))

filhos("joão", "augusto", "matheus")
#>O filho mais novo é matheus
filhos(filho3="matheus", filho1="joão", filho2="augusto")
#>O filho mais novo é matheus

# Mesmo resultado em ambos os casos, seja passando em ordem ou usando a sintaxe nome=valor.
```

O uso da sintaxe ```nome=valor``` é mais comum quando tratamos de parâmetros com valor pré-definido, o próximo tópico que veremos.

### Parâmetros com valores pré-definidos

Valores pré-definidos ou valores padrão, como os nomes já sugerem, são maneiras de garantir que alguns parâmetros tenham valores passados para a função em casos quando não escolhemos esses valores explicitamente. Para definir um valor padrão, usamos a sintaxe ```nome=valor``` na assinatura da função; caso aquele parâmetro não receba um valor na hora da chamada da função, o valor usar será o pré-definido.

Imagine uma função que mostra uma mensagem simples dizendo a comida favorita do usuário. Caso nenhum valor seja passado para o parâmetro ```comida```, a função usará "pizza":

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
```

No exemplo abaixo, a função ```raiz()``` tem dois parâmetros: ```radicando``` e ```indice```. Por padrão, ```indice ``` vale 2, o que significa que calcularemoss raízes quadradas. Porém,se passarmos um outro valor em ```indice ```, mudaremos a raíz calculada de acordo:

```python
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

Funções não podem ser vazias, ou seja, elas devem ter pelo menos um linha de código formando seu bloco. Mas à vezes queremos apenas definir a assinatura da função e deixamos a implementação para o futuro. O exemplo mais comum dessa prática é quando trabalhamos em um programa grande, com várias funções, onde é impossível desenvolver tudo de um vez e então dividimos o desenvolvimento ao longo de dias ou semanas.

Criar funções vazias ou em construção é muito fácil. Basta preencher o bloco de código com apenas a instrução ```pass```, que significa algo como "passe pra frente", "deixe pra lá", "ignore por enquanto".

```python
def conjunto_mandelbrot(z, c):
    # ainda estou estudando como esse conjunto funciona
    # o que sei por enquanto é que preciso de dois parâmetros: z, c
    # volto quando eu absolver mais
    pass
```

Note que além da instrução ```pass```, a função foi preenchida com algumas linhas de comentário. O intuito é deixar "avisos" ou "notas" para você ou quem quer que seja que vai implementar a função ter uma mínima noção do que será necessário fazer. Documentar o código é considerado uma boa prática de programação. Na opinião deste autor, a melhor de todas as práticas.

### Variáveis que guardam funções

É possível armazenar uma função em uma varíavel. **Atenção:** não estamos falando do valor de retorno de uma função, mas a própria função! Python permite que guardemos o _nome_ de uma função em um variável e, assim, chamar a função de maneira indireta via essa variável. Variáveis que guardam funções são normalmente chamadas de "variáveis coringa".

Atribuímos uma função a uma variável usando o operador ```=```, onde na esquerda temos a variável e na direita apenas o nome da função, assim como em qualquer atribuição de valor. Por exemplo:

```python
def mensagem1():
    print("Eu sou a função mensagem1! Oi! (:")

def mensagem2():
    print("Eu sou a função mensagem2! Que legal! :D")

func = mensagem1
func()
#>Eu sou a função mensagem1! Oi! (:
func = mensagem2
func()
#>Eu sou a função mensagem2! Que legal! :D
```

A seguir um exemplo mais elaborado onde as funções possuem parâmetros de entrada e a variável coringa vai ser carregada mediante decisão do usuário. Imaginemos um programa de calculadora simples com as operações de adição, subtração, multiplicação e divisão:

```python
def soma(a, b):
    return a + b

def subtrai(a, b):
    return a - b

def multiplica(a, b):
    return a * b

def divide(a, b):
    return a / b

# a variável 'operacao' é iniciada com None para indicar que ela não guarda nada até o momento
# dependendo da escolha do usuário, 'operacao' receberá uma das 4 funções que escrevemos
# o programa rodará em loop até que o usuário não queira mais
operacao = None
escolha = 0
while escolha != 5:
    a = input("Primeiro valor da operação: ")
    b = input("Segundo valor da operação: ")
    print("Escolha a operação a ser executada em cima de {} e {}2:".format(a, b))
    escolha = input("1- +\n2- -\n3- *\n4- /\n5- FINALIZAR\n> ")
    
    if escolha == 1:
        operacao = soma
    elif escolha == 2:
        operacao = subtrai
    elif escolha == 3:
        operacao = multiplica
    elif escolha == 4:
        operacao = divide
    elif escolha == 5:
        break
    else:
        print("Opção inválida!")
        print()
        continue
    
    # se a escolha tiver sido válida, 'operacao' guarda uma das funções que definimos
    print("Resultado:", operacao(a, b))
```

### Nomes e números variados de parâmetros: parâmetros opcionais

Quando vimos número variado de parâmetros, aprendemos que podemos passar uma tupla de valores para a função usando a sintaxe ```*``` antes do nome do único parâmetro. Se por um acaso quisermos definir, além dos múltiplos valores, os nomes dos parâmetros, usamos uma sintaxe semelhante, mas agora com dois asteriscos ```**``` antes do nome do único parâmetro. Dessa forma, estaremos passando um dicionário para a função, de tal forma que cada par ```parametro=valor``` passado será interpretado como o elemento respectivo ```chave=valor``` do dicionário:

```python
# PRIMEIRO EXEMPLO: mostrando que o parâmetro construído é um dicionário
# aqui não fazemos uso direto de alguma chave, apenas mostramos o conteúdo completo

def configuracao(**arg):
    print(arg)

configuracao(ip="localhost", porta=26225)
#>{'ip': 'localhost', 'porta': 26225}
configuracao(sistema="linux", versao=5.12, distro="Ubuntu")
#>{'sistema': 'linux', 'versao': 5.12, 'distro': 'Ubuntu'}
```

```python
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

É muito comum bibliotecas de código complexas usarem parâmetros opcionais para representar configurações extras de uma função. Além disso, foi informalmente padronizado pela comunidade Python que parâmetros opcionais são nomeados como ```**kwargs```.
