## AULA 05: REPETIÇÕES

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

Em termos gerais, uma estrutura de repetição é aquele que repete um conjunto de instruções até que uma dada condição não seja mais avaliada como verdadeira. Chamamos de **iteração** cada vez que a repetição repete o seu conjunto de instruções. Aproveito para lembrar também que é muito comum chamarmos uma estrutura de repetição de **laço** ou **loop**, jargões de programação mais usuais.

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

### Aninhamento de repetições

Assim como condições aninhadas, também é perfeitamente possível aninhar estruturas de repetição. Imagine um programa que exibe a tabuada de multiplicar de um número inteiro escolhido pelo usuário:

```python
n = int(input("Qual número deseja visualizar a tabuada? "))
m = 1 # variável que guarda o multiplicador
while m <= 10:
    print(n, "x", m, "=", n*m)
    m = m + 1
#>Qual número deseja visualizar a tabuada? 3
#>3 x 1 = 3
#>3 x 2 = 6
#>3 x 3 = 9
#>3 x 4 = 12
#>3 x 5 = 15
#>3 x 6 = 18
#>3 x 7 = 21
#>3 x 8 = 24
#>3 x 9 = 27
#>3 x 10 = 30
```

Como modificaríamos esse programa para exibir todas as tabuadas de 1 até um outro número também escolhido pelo usuário? O primeiro passo é perceber que código anterior exibe uma única tabuada, responsável por iterar sobre a variável ```m```. Se, agora, este laço estiver interno a outro laço, que por sua vez iterará sobre o valor da variável ```n```, podemos gerar várias tabuadas:

```python
maximo = int(input("Escolha o número máximo que queira exibir a tabuada: "))
n = 1
while n <= maximo:
    m = 1
    while m <= 10:
        print(n, "x", m, "=", n*m)
        m = m + 1
    print("-----------")
    n = n + 1
#>Escolha o número máximo que queira exibir a tabuada: 2
#>1 x 1 = 1
#>1 x 2 = 2
#>1 x 3 = 3
#>1 x 4 = 4
#>1 x 5 = 5
#>1 x 6 = 6
#>1 x 7 = 7
#>1 x 8 = 8
#>1 x 9 = 9
#>1 x 10 = 10
#>-----------
#>2 x 1 = 2
#>2 x 2 = 4
#>2 x 3 = 6
#>2 x 4 = 8
#>2 x 5 = 10
#>2 x 6 = 12
#>2 x 7 = 14
#>2 x 8 = 16
#>2 x 9 = 18
#>2 x 10 = 20
-----------
```

### Laço infinito: erro ou objetivo

Um erro muito comum, principalmente entre programadores iniciantes, é a implementação incorreta da condição do ```while``` ou do mecanismo de atualização da variável da condição. Tais equívocos podem levar o laço a nunca atingir sua condição de parada e o programa executaria as intruções do bloco infinitamente. Chamamos esse fenômemo de **laço infinito**.

Entretanto, podemos ter laços infinitos propositais. Um programa que é interrompido de maneira arbitrária por um agente externo, por exemplo o usuário, não pode ter uma condição de parada explícita. e são escritos como ```while True:```.

### Interrompendo um laço: break

Python dispõe de um comando especial responsável por abortar (ou quebrar) a execução de uma repetição: ```break```. Se o laço atinge uma linha com essa palavra, ele é automaticamente encerrado e a execução do programa continua nas demais linhas depois da repetição.

Por exemplo, veja um programa que exibe o dobro de todo número entrado pelo usuário, de maneira aparentemente infinita, mas que aborta caso o usuário entre com 0:

```python
print("Programa que multiplica por 2! Entre 0 para terminar.")
while True:
    n = int(input("número: "))
    if n == 0:
        break
    print(n, "x 2 =", n*2)
print("FIM")
#>Programa que multiplica por 2! Entre 0 para terminar.
#>número: 3
#>3 x 2 = 6
#>número: 1
#>1 x 2 = 2
#>número: 10
#>10 x 2 = 20
#>número: 5555
#>5555 x 2 = 11110
#>número: 23
#>23 x 2 = 46
#>número: 1
#>1 x 2 = 2
#>número: 0
#>FIM
```

### Pulando uma iteração: continue

Python também possui um mecanismo para pular diretamente para a próxima iteração de um laço, ignorando assim quaisquer instruções que ainda poderiam ser executadas; a palavra ```continue``` é responsável por isso. Seu uso é mais comum em laços do tipo ```for```, portanto retomaremos seu uso (com exemplos) na próxima aula.
## EXERCÍCIOS 05: Repetições

**5.1:** Escreva um programa que conta de 50 a 100.

**5.2:** Escreva um programa que mostra a contagem regressiva de lançamento de um foguete. Ele deve exibir 10, 9, 8, ..., 2, 1, FOGO.

**5.3:** Escreva um programa que exibe o quadrado de todos os números de 0 a N, onde N é um número inteiro escolhido pelo usuário.

**5.4:** Escreva um programa que exibe todos os números pares entre 0 e N, onde N é um número escolhido pelo usuário.

**5.5:** Escreva um programa que exibe todos os números múltiplos de 3 de 0 a N, onde N é um número escolhido pelo usuário.

**5.6:** Escreva um programa que leia dois números e mostre a multiplicação de um pelo outro. Entretanto, **você deve usar apenas o operador de adição**. Lembre-se que podemos entender a multiplicação como um conjunto de adições sucessivas.

**5.7:** Escreva um programa que pergunte o depósito inicial e a taxa de juros de uma poupança. Exiba os valores mês a mês para os 12 primeiros meses. Escreva o total ganho com juros nesse período.

**5.8:** Escreva um programa que leia números inteiros do teclado. O programa deve ler os números até que o usuário digite 0 (zero). Ao final da execução, exiba a quantidade de números digitados, assim como a soma e a média aritmética deles.

**5.9:** Escreva um programa que controla uma pequena máquina registradora. Você deve solicitar ao usuário que digite o código do produto e quantidade comprada. Utilize a tabela de códios abaixo para otber o preço de cada produto:

| CÓDIGO | PREÇO UNITÁRIO |
|--------|----------------|
| 1      | 0,50           |
| 2      | 1,00           |
| 3      | 4,00           |
| 4      | 7,00           |
| 5      | 8,00           |

O programa acaba quando o usuário digitar o código 0 (zero). Ao final, exiba o total de produtos comprados e o valor total acumulado.

**5.10:** Escreva um programa que leia 10 números e exiba o maior deles.

**5.11:** Escreva um programa que leia 10 números e exiba a quantidade de números pares e números ímpares lidos.

**5.12:** Escreva um programa que calcula o fatorial de um número inteiro N lido do teclado. A função fatorial é escrita como N! e é definida com uma sequência de multiplicações decrescentes do número N até 1. Exemplo: 5! = 5*4*3*2*1 = 120.

**5.13:** Os números primos possuem várias aplicações dentro da Computação, por exemplo na Criptografia. Um número primo é aquele que é divisível apenas por um e por ele mesmo. Faça um programa que peça um número inteiro e determine se ele é ou não um número primo.
