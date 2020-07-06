## EXERCÍCIO 10: Funções

> A maioria dos exercícios desta lista pedirá para que você escreva uma ou mais funções. Além de implementá-las, você também deve escrever o código necessário que as chama e as testa.

**10.1:** Escreva uma função que receba o tamanho do lado de um quadrado e retorne a sua área.

**10.2:** Escreva uma função que receba dois número e retorne ```True``` se o primeiro for múltiplo do segundo ou ```False``` caso-contrário.

**10.3:** Escreva uma função que receba uma lista de números e retorne a média dos valores.

**10.4:** Escreva uma função que receba uma string ```txt``` e um número inteiro ```n```. A função deve imprimir ```txt``` na tela ```n``` vezes.

**10.5:** Escreva uma função que receba uma lista de números inteiros e que retorne, respectivamente, a quantidade de números pares e ímpares.

**10.6:** Escreva um programa que receba um número inteiro ```n``` e que imprime na tela:

```
1
1 2
1 2 3
1 2 3 4
...
1 2 3 4 ... n
```

**10.7:** Escreva uma função que converte um hora em formato 24 horas para o formato de 12 horas. Por exemplo, passar 21:30 deve retornar 9:30.

**10.8:** Faça uma função que recebe um número inteiro e retorne o seu reverso. Por exemplo, passar 856 deve retornar 658.

**10.9:** Escreva uma função que receba um número não determinado de strings. Para cada uma, mostre seu conteúdo seguido de seu respectivo tamanho.

**10.10:** Escreva uma função que desenha uma moldura retangular na tela, como por exemplo:

```
--------------
-            -
-            -
-            -
-            -
--------------
```

A função deve receber a quantidade de linhas e de colunas da moldura, além do caractere usado para montá-la. Por padrão, o caractere de montagem deve ser ```-```, como no exemplo acima.

**10.11:** Um quadrado mágico é um conjunto de números dispostos em linhas e colunas (matematicamente chamado de matriz) de forma que a soma dos valores de qualquer linha, qualquer coluna ou qualquer diagonal é sempre a mesma. Por exemplo, a matriz 3x3 (pois tem 3 linhas e 3 colunas) abaixo é dita mágica de valor 15 pois esse é o resultado de qualquer soma de linha, coluna ou diagonal:

```
8  3  4 
1  5  9
6  7  2
```

Escreva uma função que receba uma matriz de números e retorna ```True``` se a matriz representar um quadrado mágico ou ```False``` caso contrário. A matriz pode ter qualquer tamanho, contanto que o número de linhas e colunas seja igual (2x2, 3x3, 4x4, 5x5, etc).

> A próxima função é mais um exercício de matemática que de funções. Portanto, declaro que ela é opcional.

**10.opcional:** Escreva uma função que aproxima o número Pi usando a série de Gregory–Leibniz descrita como:

![Séria de Gregory-Leibniz](https://i.imgur.com/9MO4ai5.png)

A função deve receber como parâmetro o intervalo superior do somatório e retornar o valor de Pi encontrado.
