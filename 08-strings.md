
## PARTE 08: Strings

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

#### Exemplos de uso dos métodos de string

**```.strip()```: remove espaços em branco no início e fim da string**

```python
txt = "  Hello, World!   "
print(txt)
#>  Hello, World!   
print(txt.strip())
#>Hello, World!
```

**```.lower()```: retorna string apenas com letras minúsculas**

```python
txt = "AVISO IMPORTANTE"
print(txt.lower())
#>aviso importante
```

**```.upper()```: retorna string apenas com letras maiúsculas**

```python
txt = "mesangem de perigo"
print(txt.upper())
#>MENSAGEM DE PERIGO
```

**```.capitalize()```: converte o primeiro caractere em maiúscula**

```python
txt = "olá e bem-vindo!"
print(txt.capitalize())
#>Olá e bem-vindo!
```

**```.title()```: converte a primeira letra de cada palavra em maiúscula**

```python
txt = "trabalho de conclusão de curso"
print(txt.title())
#>Trabalho De Conclusão De Curso
```

**```.swapcase()```: inverte a capitalização; maiúscula se torna minúscula e vice-versa**

```python
txt = "eItA qUe BeLeZa"
print(txt.swapcase())
#>EiTa QuE bElEzA
```

**```.center()```: retorna uma string centralizada**

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

**```.count()```: retorna o número de vezes que uma substring aparece dentro de uma string**

```python
txt = "Eu amo pêra, pêras são minhas frutas favoritas"
print(txt.count("pêra"))
#>2
```

**```.endswith()```: retorna ```True``` se a string termina com a substring passada, ```False``` caso contrário**

```python
txt = "meu_arquivo.doc"
print(txt.endswith(".doc"))
#>True
print(txt.endswith(".xls"))
#>False
```

**```.beginswith()```:  retorna ```True``` se a string começa com a substring passada, ```False``` caso contrário**

```python
txt = "cmd: atacar"
print(txt.beginswith("cmd: "))
#>True
print(txt.beginswith("act: "))
#>False
```

**```.find()```: procura uma substring dentro de uma string e retorna a posição da primeira ocorrência**

```python
txt = "Olá, meu nome é Artur"
print(txt.find("Artur"))
#>16
```

**```.replace()```: troca uma substring por outra substring**

```python
txt = "Olá, meu nome é Artur"
print(txt.replace("Artur", "Eduardo"))
#>Olá, meu nome é Eduardo

# .replace() troca todas as ocorrências da substring, não só a primeira
txt = "cmd: atacar | cmd: mover | cmd: usar | cmd: atacar | cmd: mover"
print(txt.replace("atacar", "usar"))
#>cmd: usar | cmd: mover | cmd: usar | cmd: usar | cmd: mover
```

**```.split()```: divide a string em substrings sempre que encontra a string de seperação argumento**

```python
# .split() retorna uma lista

txt = "Bem-vindo, senhor Anderson."
print(txt.split(","))
#>["Bem-vindo", " senhor Anderson."]

txt = "cmd: atacar | cmd: mover | cmd: usar | cmd: atacar | cmd: mover"
print(txt.split(" | "))
["cmd: atacar", "cmd: mover", "cmd: usar", "cmd: atacar", "cmd: mover"]
```

**```.format()```: converte e posiciona valores automaticamente em uma string**

```python
# .format() posiciona os múltiplos argumentos em sequência nos locais da string que
# tiverem com {}

txt = "Olá, {}! Bem-vindo ao {}. Poderia me informar seu {}?"
print(txt.format("Artur", "Hospital", "RG"))
#>Olá, Artur! Bem-vindo ao Hospital. Poderia me informar seu RG?
print(txt.format(18, "batalhão", "código de segurança"))
#>Olá, 18! Bem-vindo ao batalhão. Poderia me informar seu código de segurança?
```
