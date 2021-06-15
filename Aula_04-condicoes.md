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
## EXERCÍCIOS 04: Condições

A lista de exercícios propostos abaixo é a mais extensa até o momento. Não há, intencionalmente, um aumento no nível de dificuldade a cada programa. Portanto, caso você tenha dúvidas: 1) use o nosso espaço no servidor para pedir ajuda e 2) não fique estancado em um programa e tente resolver outro.

Alguns programas necessitam de uma lógica não explicitada no enunciado. Use quaisquer conhecimentos prévios seus ou pesquise na internet para descobrir as peças que faltam para estes casos. Use nosso espaço para pedir ajuda aos colegas, mas atenção: para você que vai prestar ajuda, não dê a resposta já em código! Explique a lógica que falta, mas deixe a parte da implementação (ou seja, a transformação em código) para o colega que pediu ajuda!

_**DIVIRTA-SE!**_

**4.1:** Escreva um programa que leia três números e que imprima o maior deles.

**4.2:** Escreva um programa que leia três números e que imprima o maior e o menor deles.

**4.3:** Como técnico de informática do departamento de trânsito estadual, você recebeu a tarefa de escrever o protótipo do novo sistema de multas. Escreva um programa que pergunte a velocidade do carro do usuário. Caso ultrapasse 80 km/h, exiba uma mensagem avisando o usuário que ele foi multado e o valor da multa, calculada como R$ 5,00 por km acima de 80.

**4.4:** Você foi contratado pelo setor financeiro de uma empresa. A empresa promoverá aumentos de salário a todos os empregados. Foi requisitado um programa que calcula o valor desse aumento, que é calculado com base no salário atual. Para salários superiores a R$ 1.250,00, o aumento será de 10%. Para inferiores ou iguais a este valor, 15%.

**4.5:** Uma empresa de ônibus interestadual precisa de um programa que calcula o preço de uma viagem com base na distância percorrida. O programa deve perguntar a distância de uma viagem, em km, e calcular o seu preço, cobrando R$ 0,50 por km para viagens de até 20 km e R$ 0,45 para viagens mais longas.

**4.6:** Escreva um programa que leia dois números e que pergunte qual operação aritmética você deseja realizar. As operações possíveis são adição (+), subtração (-), multiplicação (*) e divisão (/). Exiba o resultado da operação realizada.

**4.7:** Escreva um programa que calcula a conta de energia elétrica de um dado endereço. O programa deve perguntar quantos kWh foram consumidos e qual a categoria do endereço: residencial, comercial ou industrial. Use a tabela abaixo, que relaciona categoria e consumo, para saber o preço por kWh consumido:

| CATEGORIA   | CONSUMO (kWh) | PREÇO   |
|-------------|---------------|---------|
| Residencial | até 500       | R$ 0,40 |
|             | acima de 500  | R$ 0,65 |
| Comercial   | até 1000      | R$ 0,55 |
|             | acima de 1000 | R$ 0,60 |
| Industrial  | até 5000      | R$ 0,55 |
|             | acima de 5000 | R$ 0,60 |

**4.8:** Escreva um programa que leia um número e que diz se ele é par ou ímpar (DICA: operador aritmético ```%```).

**4.9:** Escreva um programa que leia um número e que diz se ele é positivo ou negativo.

**4.10:** Escreva um programa que leia as 3 notas parciais de um aluno ao longo de uma disciplina. Depois, calcule a média dessas 3 notas. Por fim, o programa deve mostrar se o aluno foi aprovado (média maior que 7), reprovado (média menor que 7) e, caso aprovado, se foi com louvor (média maior que 9).

**4.11:** Escreva um programa que leia um número e exiba o dia da semana correspondente (1- Domingo, 2- Segunda, etc). Se o número for inválido, o programa deve avisar o usuário do erro.

**4.12:** Escreva um programa que leia as 4 notas parciais de um aluno ao longo de uma disciplina. Depois, calcule a médias dessas 4 notas. Depois, exiba o conceito alcançado com base na média a partir da tabela abaixo:

| MÉDIA            | CONCEITO |
|------------------|----------|
| entre 9.0 e 10.0 | A        |
| entre 7.5 e 9.0  | B        |
| entre 6.0 e 7.5  | C        |
| entre 4.0 e 6.0  | D        |
| entre zero e 4.0 | E        |

**4.13:** Escreva um programa que leia um ano (ex: 1917) e que informe se este é ou não bissexto.

**4.14:** Faça um programa que avalia o nível de suspeita de um indivíduo com relação a um crime. O programa deve fazer as seguintes perguntas:

> 1- Telefonou para a vítima?
>
> 2- Esteve no local do crime?
>
> 3- Mora próximo da vítima?
>
> 4- Devia para a vítima?
>
> 5- Já trabalhou com a vítima?

Ao final, o programa deve exibir uma classificação do indivíduo. Caso 2 respostas forem positivas, ele deve ser classificado como "SUSPEITO". Entre 3 e 4 respostas positivas, "CÚMPLICE". Se as 5 forem positivas, "ASSASSINO". Caso contrário, ele será classificado como "INOCENTE".
