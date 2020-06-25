## AULA 04: CONDIÇÕES

Os seus programas até agora foram todos "lineares". A sequência de execução das operações (linhas) dos seus programas seguiu sempre uma mesma direção, da linha mais ao topo até a última mais embaixo. Entretanto, é possível que seu programa faça "curvas" ou "desvios" ao longo das linhas. Ou seja, o seu programa pode tomar **decisões** se vai ou não executar certas linhas. O que vai permitir esse novo tipo de comportamento no seu programa são as **condições** (ou **condicionais**).

Para entender condições, três conhecimentos precisam estar bem fundamentados:

1. Variáveis de tipo lógico
2. Operadores lógicos
3. Operadores relacionais

Os dois primeiros já foram apresentados nas Partes 2 e 3, respectivamente. Falaremos agora dos operadores relacionais e, sem seguida, mostraremos a estruturas condicionais do Python: ```if```, ```else``` e ```elif```.

### Operadores relacionais

Operadores relacionais são aqueles que relacionam dois valores de maneira lógica (igual, maior, menor, diferente, etc). Usamos o verbo "avaliar" para representar a execução de uma operação relacional. A tabela abaixo mostra os operadores relacionais presentes no Python:

| OPERADOR       | OPERAÇÃO           |
|----------------|--------------------|
| ```==```       | igualdade          |
| ```>```        | maior que          |
| ```<```        | menor que          |
| ```!=```       | diferente          |
| ```>=```       | maior ou igual que |
| ```<=```       | menor ou igual que |

O resultado de uma operação relacional é um valor lógico. Ou seja, ```True``` ou ```False```. Vejamos alguns exemplos:

```python
x = 7
y = 10
z = 3
w = 7

x == y     # x é igual a y?
#>False
y > x      # y é maior que x?
#>True
x < y      # x é menor que y?
#>True
x == w     # x é igual a w?
#>True
y >= x     # y é maior ou igual a x?
#>True
z <= y     # z é menor ou igual a y?
#>True
w != x     # w é diferente de x?
#>False
w != y     # w é diferente de y?
#>True
```

Como o resultado de uma operação relacional é uma variável de tipo lógico, você pode armazenar a resolução de uma operação em uma variável:

```python
nota = 8
media = 7
aprovado = nota > media
print(aprovado)
#>True
```

Podemos criar operações relacionais mais complexas usando os operadores lógicos (```and```, ```or```, ```not```). Como já vimos, estes operadores atuam em valores lógicos. Se uma operação relacional gera um valor lógico, então podemos agrupar duas ou mais operações relacionais com um operador lógico.

```python
nota = 8
media = 7
aprovado_com_louvor = nota > media and nota > 9
print(aprovado_com_louvor)
#>False
```

Quando um valor de tipo lógico é usado como tomador de decisão, nomeamos esse valor de **condição**.

### Condionais: if

A estrutura de condição mais simples é o ```if```. Em português, ```if``` é "se".

A partir de uma condição, o bloco abaixo do ```if``` será executado (se a condição for verdadeira, ```True```) ou não (se a condição for falsa, ```False```).

Sua estrutura básica é:

```
if <condição>:
    <bloco verdade: linhas que serão executados para condição True>
```

Vejamos um exemplo:

```python
a = float(input("Primeiro número: "))
b = float(input("Segundo número: "))
if a > b:
    print("O primeiro número é maior!")
if b > a:
    print("O segunda número é maior!")
```

Após a entrada de valores via input(), temos uma estrutura ```if``` que avalia se ```a``` é maior que ```b```. Caso seja verdade, a linha logo abaixo (note o espaçamento!) será executada. Depois, temos o teste análogo; se ```b``` é maior que ```a```. Da mesma forma, a linha abaixo desse segundo ```if``` só será executada caso a condição seja verdadeira. (_Reflexão_: é possível um conjunto de valores ```a``` e ```b``` que avalie verdadeiro para os dois ```if``` desse programa? E para ambos falso?)

Note que as linhas do bloco verdade estão deslocada mais para a direita. Chamamos isso de **identação**. O motivo é que Python define um conjunto de linhas de de código como de um mesmo bloco se essas linhas estiverem com a mesma identação, ou seja, o mesmo espaçamento para direita. A identação pode ser feita com espaços em branco ou tabulações (tecla TAB), mas atente: se você iniciar a identação com espaços em branco, faça dessa forma até o final do seu programa, e o mesmo para TABs! O interpretador Python vai gerar um erro se dois blocos de um mesmo programa usarem tipos de identação diferentes.

Um bloco de código pode ter mais de uma linha. Vejamos outro exemplo para consolidar um pouco mais o uso do ```if```, dessa vez com blocos de duas linhas cada:

```python
idade = int(input("Qual é a sua idade? "))
if idade > 30:
    print("Poxa, você é velho!")
    print("Não esqueça de ir ao médico frequentemente!")
if idade < 30:
    print("Você é novo, têm muito pela frente ainda!")
    print("Mas cuidado com o álcool!")
```

### Condicionais: else

O ```else``` é o contraponto do ```if```. Enquanto este é o "se", aquele é o "se não". Sua estrutura é:

```
<presença de algum if>
else:
    <bloco do else>
```

Vamos tomar como exemplo o último exemplo acima, o programa que diz se você é novo ou velho. Note que o segundo ```if``` serve como contraponto da condição do primeiro. Afinal, se ```idade``` não for maior ou igual a 30, ela só pode ser menor! Podemos substituir o segundo ```if``` por um ```else```:

```python
idade = int(input("Qual é a sua idade? "))
if idade > 30:
    print("Poxa, você é velho!")
    print("Não esqueça de ir ao médico frequentemente!")
else:
    print("Você é novo, têm muito pela frente ainda!")
    print("Mas cuidado com o álcool!")
```

Note que esse programa funciona tal como o primeiro, mas do ponto de vista lógico ele está mais fácil de se compreender.

Todo bloco ```else``` depende de um ```if```. A associação é dada, mais uma vez, pela identação. É impossível escrever um ```else``` isolado.

### Condicionais: elif

Python dispõe de uma estrutura condicional inexistente em muitas outras linguagens de programação: ```elif```. Este representa a "soma" de um ```else``` com um ```if```. Ou seja, ele é um bloco ```else``` (contraponto a um "se"), mas que só executa mediante a uma condição. Sua estrutura básica é:

```
<presença de algum if>
elif <condição>:
    <bloco do elif>
```

Exemplo:

```python
idade = int(input("Qual é a sua idade? "))
if idade > 30:
    print("Poxa, você é velho!")
    print("Não esqueça de ir ao médico frequentemente!")
elif idade == 30:
    print("Eita, bem na fronteira!")
    print("Hora de aproveitar a vida enquanto pode!")
else:
    print("Você é novo, têm muito pela frente ainda!")
    print("Mas cuidado com o álcool!")
```

Mais uma versão do programa da idade, dessa vez nós testamos se ```idade``` é exatamente igual a 30 usando ```elif``` para executar um bloco de mensagens especial.

### Condições dentro de condições: estruturas aninhadas

A lógica do nosso programa (o nosso algoritmo) pode, e muitas vezes será, mais complicado que o normal. É perfeitamente possível que precisemos testar outras condições caso algum tenha sido satisfeita. Em termos de código: é perfeitamente possível que precisemos escrever uma estrutura ```if``` dentro do bloco verdade de outro ```if```. Quando fazemos isso, dizemos que estamos usando **aninhamento**, ou um **estrutura aninhada**; aninhar é sequenciar blocos de código semelhantes um dentro do outro.

Voltemos ao programa anterior, o que diz se você é velho ou jovem. Vamos supor que o programa deve exibir uma mensagem especial caso o usuário tenha mais que 50 anos. A semântica (significado) disso é perceber que a condição ```idade > 50``` depende previamente que a condição ```idade > 30``` seja verdade. Veja:

```python
idade = int(input("Qual é a sua idade? "))
if idade > 30:
    print("Poxa, você é velho!")
    print("Não esqueça de ir ao médico frequentemente!")
    if idade > 50:
        print("Eita, tudo isso?")
        print("Faça caminhadas diariamente!")
elif idade == 30:
    print("Eita, bem na fronteira!")
    print("Hora de aproveitar a vida enquanto pode!")
else:
    print("Você é novo, têm muito pela frente ainda!")
    print("Mas cuidado com o álcool!")
```

A solução foi aninhar uma nova estrutura de ```if``` dentro do bloco verdade do primeiro. Note que valores entre 31 e 50 não ativaram as novas mensagens, pois estes não avaliam verdade para a nova condição.
