
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

**8.10:** Carregue seu programa com o texto abaixo:

> O proletariado se apodera da força do Estado e começa por transformar os meios de produção em propriedade do Estado. Por esse meio, ele próprio se destrói como proletariado, abole todas as distinções e antagonismos de classes e, simultaneamente, também o Estado, como Estado. A antiga sociedade, que se movia através dos antagonismos. de classe, tinha- necessidade do Estado, isto é, de uma organização da classe exploradora, em cada época, para manter as suas condições exteriores de produção e, principalmente, para manter pela força a classe explorada nas condições de opressão exigidas pelo modo de produção existente (escravidão, servidão, trabalho assalariado). O Estado era o representante oficial de toda a sociedade, a sua síntese num corpo visível, mas só o era como Estado da própria classe que representava em seu tempo toda a sociedade: Estado de cidadãos proprietários de escravos, na antigüidade; Estado da nobreza feudal, na Idade Média; e Estado da burguesia de nossos dias. Mas, quando o Estado se toma, finalmente, representante efetivo da sociedade inteira, então toma-se supérfluo. Uma vez que não haja nenhuma classe social a oprimir; uma vez que, com a soberania de classe e com a luta pela existência individual, baseada na antiga anarquia da produção, desapareçam as colisões e os excessos que daí resultavam - não haverá mais nada a reprimir, e ,um poder especial de repressão, um Estado, deixa de ser necessário. O primeiro ato pelo qual o Estado se manifesta realmente como representante de toda a sociedade - a posse dos meios de produção em nome da sociedade - é, ao mesmo tempo, o último ato próprio do Estado. A intervenção do Estado nas relações sociais se vai tomando supérflua daí por diante e desaparece automaticamente. O governo das pessoas é substituído pela administração das coisas e pela direção do processo de produção. O Estado não é abolido: morre. É desse ponto de vista que se deve apreciar a palavra de ordem de Estado livre do povo, tanto em seu interesse passageiro para a agitação, como em sua definitiva insuficiência científica; é, igualmente, desse ponto de vista que se deve apreciar a reivindicação dos chamados anarquistas, pretendendo que o Estado seja abolido de um dia para o outro.

Depois, limpe o texto de todo e qualquer acentuação possível, restando apenas palavras válidas. O resultado pode ser tanto uma string com apenas palavras válidas ou uma lista com essas palavras.
