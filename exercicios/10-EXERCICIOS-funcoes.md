

## EXERCÍCIO 10: Funções

### AQUECIMENTO

**10A.01:** Escreva uma função que recebe dois números ```a``` e ```b``` e retorna ```True``` se o primeiro foi maior ou igual ao segundo, ou ```False``` caso-contrário.

**10A.02:** Escreva uma função que calcula o "quadrado de uma string": ele deve retornar dois valores: a string duplicada e o quadrado do tamanho da string (a string "Artur" tem 5 letras, portanto o quadrado seria 25).

_Exemplo:_

```
entrada: "Ednaldo"
saída: EdnaldoEdnaldo, 49
```

**10A.03:** Um colega aprendiz de hacker precisa de uma função para ajudá-lo a quebrar um conjunto de senhas criptografas que ele achou num pendrive na rua. Ele pediu ajuda a você, um hacker experiente, e te enviou uma lista de códigos criptografados:

```
H3KF92NFC0
LKFI781YVN
194KVK0L0A
KDS929NVP7
```

Cada código representa uma senha. Ele descobriu que as senhas são constituídas apenas por 4 números na seguinte sequência:

```
<quantidade_consoantes><quantidade_vogais><quantidade_pares><quantidade_impares>
```

Ele quebrou a criptografia do primeiro código na mão, como exemplo:

```
H3KF92NFC0
- 6 consoantes
- 0 vogais
- 2 pares
- 2 impares
SENHA: 6022
```

Ele pediu que você escrevesse uma função python que toma como entrada um string criptografada e retorna na saída uma string com a senha quebrada. Use o exemplo acima quebrado na mão para validar sua função.

### LISTA ORIGINAL

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

### EXTRAS

**10E.01:** Escreva uma função que receba uma string e retorne um dicionário de duas chaves, ```maiusculas``` e ```minusculas```, cujos valores são a quantidade de letras maíusculas e minúsculas, respectivamente.

_Exemplo:_

```
entrada: "Olá, meu nome é Ednaldo. Se escreve E-D-N-A-L-D-O."
saída: {'maiusculas': 10, 'minusculas': 24}
```

_Dicas:_

- Procure pelos métodos de string ```.isupper()``` e ```.islower()```

**10E.02:** Escreva uma função que receba uma string e retorne um dicionário cujas chaves sejam as palavras da string e o valor correspondente a quantidade de ocorrências da palavra.

_Exemplo:_

```
entrada: "casa limpa é casa bem cuidada e bem cheirosa"
saída: {'casa': 2, 'limpa': 1, 'é': 1, 'bem': 2, 'cuidada': 1, 'e': 1, 'cheirosa': 1}
```

**10E.03:** Escreva uma função que receba um dicionário como entrada e exibe na tela uma tabela cuja primeira colunas guardará as chaves do dicionário e a segunda coluna, os valores correspondentes.

_Exemplo:_

```
entrada: {"nome" : "Artur", "idade" : 28, "favoritos" : ["Hakkinen", "Raikkonen", "Kubica"]}
saída:
-------------------------------------------------
CHAVES       VALORES
-------------------------------------------------
nome         Artur
idade        28
favoritos    ["Hakkinen", "Raikkonen", "Kubica"]
-------------------------------------------------
```

_Dicas:_

- O visual da tabela não precisa ser tal qual o exemplo. Use a criatividade!
- O dicionário do exemplo não deve ser tomado como único formato possível. Qualquer dicionário deve servir de entrada.

**10E.04:** Imagine um jogo de dados simples aonde dois jogadores rolam um dado ao mesmo tempo e marcam pontos caso o seu número foi maior que o do oponente. Em caso de empate no números rolados, nenhum ganha ponto. O jogo tem 7 rodadas, vence quem tiver marcado mais pontos.

Escreva uma função que receba duas listas de números, a primeira representando as rolagens do jogador 1 e a segunda, do jogador 2. A função deve verificar quantos pontos cada jogador marcou e dizer quem venceu ou se deu empate.

_Exemplo:_

```
entrada:
[1, 4, 2, 6, 6, 3]
[3, 3, 2, 5, 4, 5]
saída:
Jogador1: 3 pontos
Jogador2: 2 pontos
Jogador1 venceu!!!
```

_Dica:_

- As listas com números podem ser geradas de maneira estática sem problema; o importante é validar o funcionamento da tua função.
- A saída do programa pode ter um visual diferente do exemplo, mas deve mostrar obrigatoriamente as pontuações e quem venceu (ou se foi empate).
