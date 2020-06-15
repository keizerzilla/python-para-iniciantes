
## EXERCÍCIOS 08: Strings

**8.1:** Faça um programa que leia duas strings. Depois, mostre-as seguidos de seus respectivos tamanhos. Por fim, diga se elas são iguais ou diferentes.

**8.2:** Escreva um programa que leia uma string. Depois, mostre-a de trás pra frente e com todas os caracteres maiúsculos.

**8.3:** Faça um programa que leia uma string. Depois, mostre seu contéudo em "escadinha". Supondo que a string entrada tenha sido **FULANO**, mostre:

```
F
FU
FUL
FULA
FULAN
FULANO
```

**8.4:** Escreva um programa que leia duas strings. Verifique se a segunda ocorre dentro da primeira e imprima a posição de início. Exemplo

```
1ª string: AABBEFAATT
2ª string: BE
Resultado: BE encontrado na posição 3 de AABBEFAATT
```

**8.5:** Escreva um programa que leia uma data no formato ```dd/mm/aaaa``` e que mostra a data com o mês por extenso. Por exemplo:

```
Entrada: 29/10/1991
Resultado: 29 de outubro de 1991
```

**8.6:** Escreva um programa que leia duas strings e gere uma terceira com os caracteres comuns às duas strings. A ordem dos caracteres da string resultado não é importante, mas deve conter todas as latras comuns a ambas.

**8.7:** Escreva um programa que traduz uma string para a língua do P. Exemplo:

```
Entrada: Oi, meu nome é Artur.
Resultado: Oi, peu pope é Appup.
```

**8.8:** Um palíndromo é uma seqüência de caracteres cuja leitura é idêntica se feita da direita para esquerda ou vice−versa. Por exemplo: **OSSO** e **OVO** são palíndromos. Em textos mais complexos os espaços e pontuação são ignorados. A frase **SUBI NO ONIBUS** é o exemplo de uma frase palíndroma onde os espaços foram ignorados. Faça um programa que leia uma seqüência de caracteres, mostre−a e diga se é um palíndromo ou não.

**8.9:** Escreva um programa que leia uma frase do usuário. Depois, gere um dicionário onde cada chave seja um caractére da frase entrada e seu valor correspondente seja o número de ocorrências desse caractére na frase. Por exemplo:

```python
# Suponha que a frase entrada tenha sido:
# "Vale nada, vale tudo."
# O dicionário gerado deve ser:

dic = {
    'V': 1,
    'a': 4,
    'l': 2,
    'e': 2,
    ' ': 3,
    'n': 1,
    'd': 2,
    ',': 1,
    'v': 1,
    't': 1,
    'u': 1,
    'o': 1,
    '.': 1
 }
```
