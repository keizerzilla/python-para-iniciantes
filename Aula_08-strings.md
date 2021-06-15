## AULA 08: Strings

As strings são estruturas já comuns em nosso curso, mas até o momento foram usadas apenas como mensagens de apoio na interação entre usuário e programa; hoje veremos como manipulá-las de forma mais livre. Também conhecidas como "cadeias de caracteres", strings são sequências de caracteres delimitados por chaves duplas ```"``` ou simples ```'``` (escolha livre). Por serem um tipo de dado sequência, a maioria das manipulações possíveis com listas também são possíveis com strings.

O exemplo a seguir condensa:

- uso do operador de acesso ```[]```
- sintaxe de fatiamento
- tamanho da string usando função ```len()```
- concatenção usando operador ```+```
- busca de substrings usando operador ```in```

```python
# - podemos acessar caracteres individuais usando o operador de acesso []
# - a contagem segue a mesma lógica das listas: a partir do índice 0
nome = "Artur Rodrigues Rocha Neto"
print(nome[0])
#>A
print(nome[7])
#>o
print(nome[15]) # espaço em branco entre Rodriges e Rocha :)
#>

# - podemos fatiar uma string usando a mesma sintaxe de fatiamento de listas
print(nome[3:16])
#>tur Rodrigues R

# - a função len() retorna o tamanho da string, ou seja, quantos caracteres ela possui
print(len(nome))
#>26

# - a concatenção de strings é feita usando o operar +
saudacao = "Olá, "
convidado = "Fulano de tal"
mensagem = sudacao + convidado
print(mensagem)
#>Olá, Fulando de tal

# Podemos verificar se um string menor está contida dentro de uma maior usando o operador in
print("Artur" in nome)
#>True
print("Arthur" in nome)
#>False
print("artur" in nome) # note que strings são sensíveis à capitalização
#> False
```

A maior diferença entre listas e strings é que strings são imutáveis, ou seja, **não podemos mudar seus caracteres formadores depois que uma string é criada**:

```python
letras = "ABCDIF"
letras[4] = "E"
#>Traceback (most recent call last):
#>TypeError: 'str' object does not support item assignment
```

### Comparando strings

Usando o operador de comparação ```==``` assim como na comparação de números. A operação retornará ```True``` se todos os caractéres das duas strings testadas forem exatamente iguais e nas respectivas posições, e ```False``` caso contrário:

```python
txt1 = "jeremirio"
txt2 = "jeremirio"
txt3 = "hugo"
txt1 == txt2
#>True
txt1 == txt3
#>False
```

### Strings com múltiplas linhas

Para manipular strings muito grandes, que se prolongam por mais de uma linha, delimitamos os caracteres não com duas mas com três aspas duplas (ou simples):

```python
poema = """vale nada
vale tudo
você topa qualquer parada
porque é de nada
e não é de tudo"""

print(poema)
#>vale nada
#>vale tudo
#>você topa qualquer parada
#>porque é de nada
#>e não é de tudo
```

### Percorrendo strings usando laço ```for```

Assim como listas e dicionários, strings são tipos de dado sequência. Portanto, podemos percorrer seus elementos (no caso, caracteres) usando um laço ```for```. Cada elemento por iteração do laço será um caractere da string, do primeiro até o final.

```python
txt = "Bom dia."
for c in txt:
    print(c)
#>B
#>o
#>m
#> 
#>d
#>i
#>a
#>.
```

### Métodos de strings

A cada nova versão do Python, novos métodos de string são adicionados. Até o momento da criação desta aula, estavam disponíveis mais de 20 métodos. Focaremos a atenção em alguns que julgamos ser mais importantes e deixamos para a sua curiosidade pesquisar a documentação dos demais.

**ATENÇÃO: todos os métodos de strings geram novas strings, ou seja, não mudam a string que os chama!**

- ```.strip()```: remove espaços em branco no início e fim da string
- ```.lower()```: retorna string apenas com letras minúsculas
- ```.upper()```: retorna string apenas com letras maiúsculas
- ```.capitalize()```: converte o primeiro caractere em maiúscula
- ```.title()```: converte a primeira letra de cada palavra em maiúscula
- ```.swapcase()```: inverte a capitalização; maiúscula se torna minúscula e vice-versa
- ```.center()```: retorna uma string centralizada
- ```.count()```: retorna o número de vezes que uma substring aparece dentro de uma string
- ```.endswith()```: retorna ```True``` se a string termina com a substring passada, ```False``` caso contrário
- ```.beginswith()```:  retorna ```True``` se a string começa com a substring passada, ```False``` caso contrário
- ```.find()```: procura uma substring dentro de uma string e retorna a posição da primeira ocorrência
- ```.replace()```: troca uma substring por outra substring
- ```.split()```: divide a string em substrings sempre que encontra a string de seperação argumento
- ```.format()```: converte e posiciona valores automaticamente em uma string

#### ```.strip()```: remove espaços em branco no início e fim da string

```python
txt = "  Hello, World!   "
print(txt)
#>  Hello, World!   
print(txt.strip())
#>Hello, World!
```

#### ```.lower()```: retorna string apenas com letras minúsculas

```python
txt = "AVISO IMPORTANTE"
print(txt.lower())
#>aviso importante
```

#### ```.upper()```: retorna string apenas com letras maiúsculas

```python
txt = "mesangem de perigo"
print(txt.upper())
#>MENSAGEM DE PERIGO
```

#### ```.capitalize()```: converte o primeiro caractere em maiúscula

```python
txt = "olá e bem-vindo!"
print(txt.capitalize())
#>Olá e bem-vindo!
```

#### ```.title()```: converte a primeira letra de cada palavra em maiúscula

```python
txt = "trabalho de conclusão de curso"
print(txt.title())
#>Trabalho De Conclusão De Curso
```

#### ```.swapcase()```: inverte a capitalização; maiúscula se torna minúscula e vice-versa

```python
txt = "eItA qUe BeLeZa"
print(txt.swapcase())
#>EiTa QuE bElEzA
```

#### ```.center()```: retorna uma string centralizada

```python
txt = "banana"

# com apenas um parâmetro: tamanho da string final e espaçamento feito com espaço em branco
print(txt.center(20))
#>       banana       

# com dois parâmetros: primeiro o tamanho, segundo o caractere de espaçamento
print(txt.center(20, "-"))
#>-------banana-------
print(txt.center(20, "="))
#>=======banana=======
print(txt.center(20, "+"))
#>+++++++banana+++++++
```

#### ```.count()```: retorna o número de vezes que uma substring aparece dentro de uma string

```python
txt = "Eu amo pêra, pêras são minhas frutas favoritas"
print(txt.count("pêra"))
#>2
```

#### ```.endswith()```: retorna ```True``` se a string termina com a substring passada, ```False``` caso contrário

```python
txt = "meu_arquivo.doc"
print(txt.endswith(".doc"))
#>True
print(txt.endswith(".xls"))
#>False
```

#### ```.startswith()```:  retorna ```True``` se a string começa com a substring passada, ```False``` caso contrário

```python
txt = "cmd: atacar"
print(txt.startswith("cmd: "))
#>True
print(txt.startswith("act: "))
#>False
```

#### ```.find()```: procura uma substring dentro de uma string e retorna a posição da primeira ocorrência

```python
txt = "Olá, meu nome é Artur"
print(txt.find("Artur"))
#>16
```

#### ```.replace()```: troca uma substring por outra substring

```python
txt = "Olá, meu nome é Artur"
print(txt.replace("Artur", "Eduardo"))
#>Olá, meu nome é Eduardo

# .replace() troca todas as ocorrências da substring, não só a primeira
txt = "cmd: atacar | cmd: mover | cmd: usar | cmd: atacar | cmd: mover"
print(txt.replace("atacar", "usar"))
#>cmd: usar | cmd: mover | cmd: usar | cmd: usar | cmd: mover
```

#### ```.split()```: divide a string em substrings sempre que encontra a string de seperação argumento

```python
# .split() retorna uma lista

txt = "Bem-vindo, senhor Anderson."
print(txt.split(","))
#>["Bem-vindo", " senhor Anderson."]

txt = "cmd: atacar | cmd: mover | cmd: usar | cmd: atacar | cmd: mover"
print(txt.split(" | "))
["cmd: atacar", "cmd: mover", "cmd: usar", "cmd: atacar", "cmd: mover"]
```

#### ```.format()```: converte e posiciona valores automaticamente em uma string

```python
# .format() posiciona os múltiplos argumentos em sequência nos locais da string que
# tiverem com {}

txt = "Olá, {}! Bem-vindo ao {}. Poderia me informar seu {}?"
print(txt.format("Artur", "Hospital", "RG"))
#>Olá, Artur! Bem-vindo ao Hospital. Poderia me informar seu RG?
print(txt.format(18, "batalhão", "código de segurança"))
#>Olá, 18! Bem-vindo ao batalhão. Poderia me informar seu código de segurança?
```

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
