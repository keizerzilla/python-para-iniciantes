## Parte 05: REPETIÇÕES

Na aula anterior, aprendemos a "fazer desvios" em nossos programas através de condições. Sabemos agora como executar ou não trechos específicos do código a partir de decisões tomadas com a ajuda das estruturas condicionais ```if```, ```else``` e ```elif```. Com elas, nossa capacidade de escrever programas mais sofisticados aumentou drasticamente.

Agora, veremos a última estrutura algorítmica básica: repetições. Assim como é importante sabermos executar ou não certos pedaços do programa, é de grande importância aprendermos a **repetir um mesmo conjunto de instruções certa quantidade de vezes**.

Vejamos um exemplo. Imagine que você precisa escrever um programa que lê 3 números via teclado; você pode chamar a função input() 3 vezes. Depois houve uma mudança no funcionamento do programa e agora você precisa ler 5 números, ou talvez 20 números; a cada mudança, você teria de modificar o seu código, adicionando ou removendo mais chamadas à função input(). Agora imagine que a quantidade de números lidos **é escolhida pelo usuário**: o que fazer?

A solução é o uso de **repetições**, também conhecidas como **laços** (do inglês _loop_). Python dispõe de duas estruturas de repetição: ```while``` e ```for```. Abordaremos nesta aula o ```while```, por ser a estrutura genérica de repetição. Deixaremos o ```for``` para quando estudarmos variáveis do tipo sequência, pois em Python essa estrutura está ligada a tarefas de varredura desse tipo de dado.

### Um programa que conta de 1 a 5

Vamos supor que você queira escrever um programa que mostra na tela a sequência de números de 1 a 5. Apenas com o conhecimento que já aprendemos, você poderia escrever algo como:

```python
print(1)
print(2)
print(3)
print(4)
print(5)
#>1
#>2
#>3
#>4
#>5
```

Se por um acaso o primeiro número da sequência não fosse mais 1 e sim 4, você teria que trocar manualmente o argumento de cada função print(). Outra maneira seria de guardar o valor inicial em uma variável, por exemplo ```x```, e incrementar o valor a cada print():

```python
x = 1 # valor incial da sequência
print(x)
x = x + 1
print(x)
x = x + 1
print(x)
x = x + 1
print(x)
x = x + 1
print(x)
#>1
#>2
#>3
#>4
#>5
```

Essa nova versão gera o mesmo resultado de antes, mas agora basta mudar apenas o valor inicial de ```x``` para que uma nova sequência seja impressa (para ```x = 3```, teríamos: 3, 4, 5, 6, 7; por exemplo). Bem mais flexível! Mas ainda temos um problema: caso a quantidade de números da sequência mude, ainda teríamos de adicionar ou remover manualmente linhas de ```print(x)``` e ```x = x + 1```.

### while

A solução é usarmos o ```while```. Em Python, sua estrutura é:

```
while <condição>:
    <bloco do while>
```

O ```while``` repetirá um conjunto de instruções (```<bloco do while>```) enquanto uma certa ```<condição>``` for verdadeira. Muito parecido com o comportamento das estruturas condicionais que vimos na aula anterior. Vamos reescrever o programa que conta de 1 a 5, agora usando ```while```:

```python
x = 1
while x <= 5:
    print(x)
    x = x + 1
#>1
#>2
#>3
#>4
#>5
```

A execução desse programa seria:

1. A variável ```x``` é criada e a ela é atribuido o valor ```1```;
2. Chegamos na condição do ```while``` e testamos ```x <= 5```. Como ```x``` vale ```1```, tal condição é verdade e entramos no bloco;
3. Exibimos o valor de ```x``` com a função print();
4. Incrementamos ```x``` que agora vale ```2```. Como essa foi a última instrução do bloco ```while```, **o programa retorna para a linha da condição**;
5. De volta a linha da condição, testamos novamente ```x <= 5```. Como ```x``` vale ```2```, tal condição é verdade e entramos novamente no bloco;
6. Esse processo se repete até que a condição do ```while``` seja falsa, e então o programa segue a execução. Como não há mais nenhuma instrução, o programa termina.

Veja que uma estrutura de repetição adiciona uma dinâmica a mais aos nossos programas. Aquele problema de quantos elementos serão impressos fica agora bem fácil de resolver, bastando apenas mudar o valor de comparação na condição do ```while```. Um programa genérico que imprime uma sequência de tamanho variável poderia ser:

```python
n = int(input("Quantos números possui a sequência? "))
x = 1
while x <= n:
    print(x)
    x = x + 1
#>Quantos números possui a sequência? 8
#>1
#>2
#>3
#>4
#>5
#>6
#>7
#>8
```
**CONTINUAR...**
