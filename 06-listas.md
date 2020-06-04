
## PARTE 06: LISTAS

Lista é um tipo de variável que permite guardar vários valores em sequência. Cada valor de uma lista é chamado **elemento** e a sua posição na lista, **índice**. Uma lista pode guardar nenhum ou vários elementos, de mesmo tipo ou de tipos diferentes (incluindo outras listas!). Chamamos de **tamanho** da lista a quantidade de valores que ela guarda. Seu tipo no python é o ```list```.

Imagine uma lista como um fita de papel dividia em vários quadradinhos. Cada quadradinho guarda um valor, ou seja, um elemento. A posição do quadradinho é o índice. Nós começamos a contar os índices a partir de 0 (zero). Portanto, em uma fita com 7 elementos, nós contamos os índices de 0 a 6. Se dermos o nome de ```F``` para essa lista, o acesso de cada elemento é feito usando colchetes ```[]```: ```F[0]``` retorna o primeiro elemento, enquanto ```F[6]``` retorna o último. A imagem abaixo visualiza esse exemplo; em vermelho temos os elementos da lista e em azul, os índices correspondentes.

![Exemplo visual de uma lista. Em vermelho estão os elementos. Em azul, os índices.](https://i.imgur.com/WAdjflM.png)

A mesma lista ```F``` pode ser criada em Python escrevendo:

```python
F = [4, 5, 7, 2, 9, 0, 3]
```

Veja que uma lista é criada usando colchetes ```[]```. Os elementos da lista são separados por vírgulas. Podemos criar uma lista vazia (sem elementos) fazendo:

```python
L = []
```

Você pode armazenar absolutamente QUALQUER tipo de dado em uma lista, inclusive misturar os tipos:

```python
A = [1, 2, 3, 4, 5] # lista de inteiros
B = [3.14, 2.33, 7.77, 0.98] # lista de pontos flutuantes
C = ["queen", "the strokes", "rhapsody", "agnaldo timoteo"] # lista de strings
D = [3.14, 7, "marx", "lenin", 0.99, 1] # lista misturada
```

Assim como todos os outros tipos de dados que vimos até o momento, listas possuem uma função própria usada para conversões. Essa função também tem o mesmo nome do tipo de varíavel: ```list()```. Mais a frente veremos quais tipos de dados podem ser convertidos diretamente em listas.

Listas são variáveis mutáveis, ou seja, elas podem mudar. Podemos adicionar e remover elementos, destruí-las por completo e reconstruí-las facilmente. Além dessa flexibilidade, listas são variáveis especiais chamadas de **objetos** e possuem funções especiais chamadas de **métodos**. Métodos são funções acessadas diretamente por objetos usando ponto ```.``` (detalhes mais a frente).

Eu arriscaria dizer que listas são o que Python tem de mais poderoso. Outras linguagens de programação possuem seus próprios mecanismos para armazenar dados sequenciais, mas não com a mesma flexibilidade que as listas do Python.

### Acesso e modificação de elementos

Como já mencionamos, o acesso de elementos é feito usando colchetes ```[]``` e passando o índice do elemento que queremos acessar. Por exemplo:

```python
Z = [3, 6, 1, 2]
print(Z[0])
#>3
print(Z[1])
#>6
print(Z[2])
#>1
print(Z[3])
#>2
```

Se tentarmos acessar um índice que não existe na lista, Python retornará um erro do tipo ```OutOfBounds``` (fora dos limites).

Podemos mudar o valor de um elemento tão facilmente quanto mudamos o valor de qualquer variável. Usando o acesso via índice, podemos fazer:

```python
Z = [3, 6, 1, 2]
print(Z[0])
#>3
Z[0] = 9
print(Z[0])
#>9
print(Z) # podemos mostrar uma lista por inteiro!
#>[3, 6, 1, 2]
```

### Cópia de listas

Como mencionamos na introdução, listas são variáveis especiais chamadas de objetos. Objetos são copiados de maneira diferente que variáveis comuns. Quando atribuímos uma lista a outra varíavel, não estamos fazendo uma cópia elemento-a-elemento, apenas passando a "referência" da lista para a outra variável. Um exemplo deve ajudar a entender melhor:

```python
A = [1, 2, 3, 4]
B = A
print(A)
#>[1, 2, 3, 4]
print(B)
#>[1, 2, 3, 4]

A[0] = 9
print(A)
#>[9, 2, 3, 4]
print(B)
#>[9, 2, 3, 4]

# o elemento do índice 0 foi mudado em ambas as listas!!!
```
Para criarmos uma cópia de verdade de uma lista, usamos a sintaxe ```[:]```. Podemos refazer o exemplo anterior e agora criarmos uma cópia:

```python
A = [1, 2, 3, 4]
B = A[:]
print(A)
#>[1, 2, 3, 4]
print(B)
#>[1, 2, 3, 4]

A[0] = 9
print(A)
#>[9, 2, 3, 4]
print(B)
#>[1, 2, 3, 4]

# o elemento do índice 0 foi mudado apenas na lista A
```

### Fatiamento de listas

Podemos usar uma sintaxe parecida com a de cópia de listas para fazer um tipo de acesso muito poderoso chamado fatiamento. Fatiar é, como o nome indica, acessar pedaços de uma lista. A sintaxe de fatiamento é:

```
[<indice_inicial>:<indice_depois_do_final>]
```

```<indice_inicial>``` é a posição de onde queremos começar o fatiamento. ```<indice_depois_do_final>``` é a posição após o fim do fatiamento. Ou seja, se queremos fatiar do índice 2 ao índice 7, usamos ```[2:8]```. Se quisermos fatiar do índice 0 ao índice 3, usamos ```[0:4]```.

```python
L = [5, 3, 2, 1, 8]
print(L[0:4])
#>[5, 3, 2, 1]
print(L[2:4])
#>[2, 1]
print(L[1:3])
#>[3, 2]
```

Podemos acessar uma lista de trás pra frente usando índices negativos. ```-1``` indica o último elemento, ```-2``` o penúltimo, e assim sucessivamente:

```python
L = [5, 3, 2, 1, 8]
print(L[-1])
#>8
print(L[-2])
#>1
print(L[-3])
#>2
```

### Concatenação de listas: operador ```+```

Podemos usar o operador ```+``` para "somar" duas listas. O termo mais correto para essa operação é concatenação:

```python
L1 = [1, 2, 3]
L2 = [4, 5, 6]
L3 = L1 + L2
print(L3)
#>[1, 2, 3, 4, 5, 6]
```

### Removendo um elemento: operador ```del```

A instrução ```del``` serve para remover um elemento de uma lista. Seu uso é bem simples:

```python
L = [2, 1, 5, 3, 8]
del L[2]
print(L)
#>[2, 1, 3, 8]
del L[1]
print(L)
#>[2, 3, 8]
```
### Verificando se um elemento está na lista: operador ```in```

O operador ```in``` retorna um valor lógico (```True``` ou ```False```) se um dado elemento estiver presente numa lista:

```python
frutas = ["banana", "mexerica", "melancia", "uva"]
print("banana" in frutas)
#>True
print("goiaba" in frutas)
#>False

notas = [5, 7, 6, 9, 8]
print(2 in notas)
#>False
print(5 in notas)
#>True
```

### Tamanho de uma lista: função ```len()```

Como mencionamos na introdução dessa aula, chamamos de tamanho da lista o número de elementos que ela guarda. Podemos usar a função ```len()``` para retornar o tamanho de uma lista::

```python
L = [6, 6, "artur", 2.3]
print(len(L))
#>4
J = ["melancia", "ednaldo", "birina", "lenha", "uniao", "tranca"]
print(len(J))
#>6
```

### Funções super práticas: ```min()```, ```max()```, ```sum()```

No caso de listas que contem apenas valores números (inteiros ou ponto fluantes), temos à disposição 3 funções bastantes úteis: ```min()```, ```max()```, ```sum()```. Como os nomes sugerem, elas servem para retornar o menor valor de uma lista, o maior valor de uma lista e a soma de todos os valores da lista, respectivamente.

```python
L = [9, 2, 3, 10, 5, -4, 2, -8, -11, 58, 2]

# min(): retorna o menor valor
print(min(L))
#>-11

# max(): retorna o maior valor
print(max(L))
#>58

# sum(): retorna a soma
print(sum(L))
#>68
```

As funções ```min()``` e ```max()``` podem ser usadas em listas de strings também. Seu funcionamento é o seguinte:
- primeiro, a função ordena as strings em ordem alfabética em uma lista temporária (não altera a original!)
- com base nessa lista ordenada, a função retornará o primeiro elemento (no caso de ```min()```) ou o último (no caso de ```max()```).

Vejamos um exemplo:

```python
roupas = ["luvas", "jaqueta", "calça", "blusa", "cueca", "meias"]

print(min(roupas))
#>blusa
print(max(roupas))
#>meias
print(roupas)
#>['luvas', 'jaqueta', 'calça', 'blusa', 'cueca', 'meias']

# note que a lista não se alterou!
```

### Métodos de lista

Como falamos na introdução, listas são variáveis especiais chamadas de objetos. Objetos se diferenciam de variáveis comuns por possuírem métodos. Imagine um método como uma **"função interna"** a um objeto ou como uma **"função própria"** de um objeto. Ou seja, métodos só podem ser usados por objetos de mesmo tipo. O uso de um método é através do ponto ```.```

As listas do Python possuem 11 métodos:

- ```.append()```: adiciona um elemento ao final da lista
- ```.clear()```: remove todos os elementos da lista
- ```.copy()```: retorna uma cópia da lista (mesmo efeito de ```[:]```)
- ```.count()```: retorna a quantidade de ocorrências de um valor específico na lista
- ```.extend()```: adiciona todos os elementos de uma lista ao final da lista que chama
- ```.index()```: retorna o índice da primeira ocorrência de um valor específico na lista
- ```.insert()```: adiciona um elemento à lista numa posição específica
- ```.pop()```: remove e retorna um elemento da lista numa posição específica
- ```.remove()```: remove a primeira ocorrência de um valor específico na lista
- ```.reverse()```: inverte a ordem dos elementos da lista
- ```.sort()```: ordena a lista de forma crescente ou descrescente

### Exemplos de uso dos métodos de lista

#### ```.append()```: adiciona um elemento ao final da lista

```python
frutas = ["laranja", "melancia", "uva"]
frutas.append("goiaba")
print(frutas)
#>["laranja", "melancia", "uva", "goiaba"]

notas = [5, 4, 2, 8, 9]
notas.append(10)
print(notas)
#>[5, 4, 2, 8, 9, 10]
```

#### ```.clear()```: remove todos os elementos da lista

```python
roupas = ["calça", "camiseta", "cueca", "meias"]
roupas.clear()
print(roupas)
#>[]
```

#### ```.copy()```: retorna uma cópia da lista (mesmo efeito de ```[:]```)

```python
L = [6, 5, 4, 3, 2, 1]
J = L.copy()
print(J)
#>[6, 5, 4, 3, 2, 1]
```

#### ```.count()```: retorna a quantidade de ocorrências de um valor específico na lista

```python
notas = [5, 8, 5, 7, 9, 10]
x = notas.count(5)
print(x)
#>2
y = notas.count(10)
print(y)
#>1
z = notas.count(6)
print(z)
#>0
```

#### ```.extend()```: adiciona todos os elementos de uma lista ao final da lista que chama

```python
L = [1, 2, 3, 4, 5]
J = [6, 7, 8, 9]
L.extend(J)
print(L)
#>[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### ```.index()```: retorna o índice da primeira ocorrência de um valor específico na lista

```python
cartas = ["valete", "damas", "reis", "A"]
i = fruits.index("reis")
print(i)
#>2
```

#### ```.insert()```: adiciona um elemento à lista numa posição específica

```python
jogos = ["tetris", "super mario", "ragnarok"]
jogos.insert(1, "final fantasy")
print(jogos)
#>["tetris", "final fantasy", "super mario", "ragnarok"]
```

#### ```.pop()```: remove e retorna um elemento da lista numa posição específica

```python
notas = [5, 5, 9, 7]
x = notas.pop(2)
print(x)
#>9
print(notas)
#>[5, 5, 9, 7]
```

#### ```.remove()```: remove a primeira ocorrência de um valor específico na lista

```python
aparelhos = ["computador", "celular", "pager", "gameboy"]
aparelhos.remove("computador")
print(aparelhos)
#>["celular", "pager", "gameboy"]
```

#### ```.reverse()```: inverte a ordem dos elementos da lista

```python
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9]
numeros.reverse()
print(numeros)
#>[9, 8, 7, 6, 5, 4, 3, 2, 1]
```

#### ```.sort()```: ordena a lista de forma crescente ou descrescente

```python
cedulas = [50, 10, 10, 2, 5, 20, 100, 50]
cedulas.sort()
print(cedulas)
#>[2, 5, 10, 10, 20, 50, 50, 100]

# para ordenar de forma descrescente, use o argumento posicional reverse=True
# mais detalhes de como argumentos posicionais funcionam na aula de Funções!

cedulas = [50, 10, 10, 2, 5, 20, 100, 50]
cedulas.sort(reverse=True)
print(cedulas)
#>[100, 50, 50, 20, 10, 10, 5, 2]

# a ordenação de elementos string segue a sequência do alfabeto

frutas = ["laranja", "banana", "melancia", "uva"]
frutas.sort()
print(frutas)
#>['banana', 'laranja', 'melancia', 'uva']

# ATENÇÃO: palavras iniciadas com maíusculas são ordenadas primeiro que minúsculas

frutas = ["laranja", "Ameixa", "abobora", "banana", "melancia", "uva", "Uva"]
frutas.sort()
print(frutas)
#>['Ameixa', 'Uva', 'abobora', 'banana', 'laranja', 'melancia', 'uva']
```

### Listas que não mudam: tuplas

Python possúi um outro tipo de variável sequencial muito parecida com lista: são as tuplas (tipo ```tuple```). Uma tupla e uma lista são _quase_ a mesma coisa. As diferenças começam com a forma de declaração; criamos tuplas usando parênteses ```()```. O acesso a elementos ainda é feito usando colchetes ```[]```:

```python
t = (2, 4, 3, 1)
print(t[0])
#>2
print(t[2])
#>3
```

É possível usar apenas as operações de acesso, fatiamento e concatenção nas tuplas.  Não é possível adicionar, remover ou mudar elementos de tuplas. Essa é a grande diferenças entre essas duas sequências: listas são mutáveis, **tuplas não são mútaveis**.

A propriedade mais especial de tuplas (e que listas não possuem) é chamada **desempacotamento**. Podemos desempacotar, ou seja, retirar os elementos de uma tupla e armazená-los variáveis de forma automatica:

```python
# DESEMPACOTAMENTO:
# as variáveis à esquerda do operador = receberão os elementos da tupla em sequência
t = (5, 3, 2)
x, y, z = t
print(x)
#>5
print(y)
#>3
print(z)
#>2
```

O contrário, ou seja, o empacotamento, também é possível. Intuitivamente, a sintaxe do empacotamento é a inversa do desempacotamento; podemos criar uma tupla a partir de um conjunto de variáveis:

```python
a = 10,
b = 66
c = 7
t = a, b, c
print(t)
#>(10, 66, 7)
```

### Laço sequencial: ```for```

Como você viu, dá pra fazer muita coisa com listas. Não é à toa que elas são as estruturas mais poderosas da linguagens. Além das diversas operações e métodos, Python conta com um instrução de laço feita especialmente para percorrer os elementos de uma lista: ```for```.

A instrução ```for``` funciona de maneira bem semelhante que a ```while```, mas a cada repetição utiliza um elemento diferente da lista. A cada iteração do laço, o próximo elemento em sequencial será utilizado, repetindo até que não sobre mais nenhum elemento na lista. A estrutura do ```for``` é:

```
for <variavel_elemento> in <lista>:
    # <bloco_do_for>
```

Como exemplo, podemos escrever um programa que mostra todos os elementos de uma lista:

```python
L = [8, 7, 9]
for e in L:
    print(e)
#>8
#>7
#>9
```

Na primeira iteração, ```e``` receberá o valor do primeiro elemento da lista, ```8```. Na segunda, o segundo elemento: ```7```. Na terceira, o terceiro elemento: ```9```. Como a lista não possui mais elementos, o laço acaba e o programa continua.

Veja o que precisaríamos escrever se tivéssemos de fazer o mesmo programa, mas usando ```while```:

```python
L = [8, 7, 9]
x = 0
while x < len(L):
    e = L[x]
    print(e)
    x = x + 1
#>8
#>7
#>9
```

Nesse exemplo, o uso de ```for``` foi mais simples e elegante que ```while```, mas isso não quer dizer que aquele substitua este em todos os casos. O ```for``` é recomenado quando se quer processar todos os elementos de uma lista. O ```while``` é usado para lógicas de repetição nas quais não sabemos ao certo quantas vezes vamos repetir ou quando essa lógica possui uma condição de parada ou não bem definida.

### Gerador de listas: ```range()```

A função ```range()``` é do tipo _geradora_. Em Python, funções geradoras são aquelas que criam _pseudo-coisas_. Portanto, uma geradora de listas cria _pseudo-listas_.

Uma pseudo-lista não existe na memória de forma completa. Seus elementos são criados apenas quando são acessados. Assim, é possível gerar listas enormes e economizar memória.

A função ```range()``` gera pseudo-listas de números e possui três argumentos:

1) _start_: o primeiro elemento da sequência de números
2) _stop_: o elemento depois do final da lista (parecido com o elemento final do fatiamento, lembra?)
3) _step_: o espaçamento entre os valores

Se ```range()``` for chamada apenas com um argumento, ele será atribuído a _stop_ e _start_ será definido como 0 (zero). Se for chamada com dois, o primeiro será _start_ e o segundo será _stop_. Se for usada com os três, eles serão _start_, _stop_ e _step_, respectivamente.

O uso de ```range()``` está intimamente ligado ao laço ```for```, por isso todos os exemplos serão usando esse tipo de repetição:

```python
# apenas um argumento: apenas stop
for v in range(5):
    print(v)
#>0
#>1
#>2
#>3
#>4
```

```python
# dois argumentos: start, stop
for v in range(5, 8):
    print(v)
#>5
#>6
#>7
```

```python
# três argumentos: start, stop, step
for v in range(2, 10, 2):
    print(v)
#>2
#>4
#>6
#>8
```

Podemos transformar um pseudo-lista gerada com ```range()``` em uma lista real usando a função ```list()```:

```python
r = range(0, 10)
print(r)
#>range(0, 10)
L = list(r)
print(L)
#>[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### Rastreando índices: ```enumerate()```

A função ```enumerate()``` é usada quando queremos ter acesso, ao mesmo tempo, tanto aos **valores dos elementos** quanto aos **índices dos elementos** durante a execução de um laço ```for```. Ela também é geradora, assim como ```range()```, mas de tuplas: o primeiro valor será o índice do elemento atual e o segundo, o valor do elemento atual. Como o nome sugere, portanto, ela "enumera" os elementos de uma sequência.

Note que no exemplo abaixo escrevemos o início do laço como ```for i, e in enumerate(frutas)```; a parte ```i, e``` nada mais que a propriedade do desempacotamento de tuplas sendo usada.

```python
frutas = ["laranja", "banana", "melancia", "uva"]
for i, e in enumerate(frutas):
    print(i, e)
#>0 laranja
#>1 banana
#>2 melancia
#>3 uva
```

### Tuplas a partir de duas listas: a função ```zip()```

A função ```zip()``` toma como argumento uma ou mais listas de mesmo tamanho. O retorno é uma sequência de tuplas aonde o primeiro valor vem do primeiro argumento e o segundo valor, do segundo. Seu uso é bem semelhante ao da função ```enumerate()```: quando usada num laço for, podemos desempacotar o retorno de ```zip()``` em duas variáveis e tratar os valores de duas listas mais 

```python
# zip de duas listas
L = [4, 3, 1, 0]
J = [5, 2, 3, 9]
for l, j in zip(L, J):
    print(l, j)
#>4 5
#>3 2
#>1 3
#>0 9

# zip de três listas
nome = ["artur", "hugo", "hamlet", "caio", "bruno"]
idade = [28, 28, 60, 28, 29]
cor = ["vermelho", "azul", "verde", "roxo", "amarelo"]
for n, i, c in zip(nome, idade, cor):
    print(n, i, c)
#>artur 28 vermelho
#>hugo 28 azul
#>hamlet 60 verde
#>caio 28 roxo
#>bruno 29 amarelo
```

### Lista de listas

Como podemos misturar qualquer tipo de dado em uma mesma lista, Python permite armazenar listas dentro de uma outra lista. O acesso de elementos de uma lista interna (ou "lista elemento", ou "sub-lista") é feito usando múltiplos operadores colchete ```[]```. O primeiro índice localiza o elemento na posição da lista. Se esse elemento for uma lista, podemos acessar um valor desse a partir do segundo índice. O exemplo abaixo monta uma lista que guarda três outras listas, cada uma com três elementos. Primeiro, podemos imprimir as listas internas por completo, usando apenas um índice. Com o uso do segundo índice, podemos acessar elementos das listas internas:

```python
# outra forma de inicializar listas de listas é espaçando as linhas assim:
#
# matriz = [
#     [1, 2, 3],
#     [4, 5, 6],
#     [7, 8, 9]
# ]
#
# alguns argumentam que essa é mais organizada e legível
# a escolha de estilo vai de programador para programador

matriz = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

# ACESSANDO LISTAS INTERNAS POR COMPLETO
print(matriz[0])
#>[1, 2, 3]
print(matriz[1])
#>[4, 5, 6]
print(matriz[2])
#>[7, 8, 9]

# ACESSANDO ELEMENTOS DAS LISTAS INTERNAS
print(matriz[0][0])
#>1
print(matriz[1][2])
#>6
print(matriz[2][1])
#>8
```
