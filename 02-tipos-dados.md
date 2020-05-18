**PARTE 02: TIPOS DE DADOS**

Vimos que variáveis são compartimentos da memória que armazenam dados. Nos exemplos mostrados já foi possível ter uma noção dos **tipos de dados** possíveis que podemos armazenar. Agora vamos formalizar os tipos de dados possíveis em Python. Outras linguagens de programação podem apresentar mais ou menos possibilidades de tipos possíveis.

Podemos agrupar os tipos possíveis no Python em algumas categorias:

Numérico:		int, float, complex
Texto:			str
Lógico:			bool
Sequência:		list, tuple, range
Mapeamento:		dict
Conjunto:		set, frozenset
Binário:		bytes, bytearray, memoryview

Vamos detalhar as três primeiras categorias por enquanto, por estas serem as mais comuns. As demais terão atenção particular em momento oportuno.

**1- Numérico:** tipos de números. int são dados inteiros, também conhecidos como "números naturais" (-5, 2, 0, 666, 3, 8, 10, etc). float armazena dados "ponto flutuante", também conhecidos como "número racionais", "decimais" ou "quebrados" (3.14, 5.5555556, 78.9, etc). complex armazena os "números complexos", também chamados de "números imaginários" (1+3j, -5+2j, 6j, etc).
**2- Texto:** armazena texto. Possui apenas um tipo, str, chamado *string*, também conhecido como sequência de caractéres, texto e cadeia de caractéres. O jargão de programação mais comum é string.
**3- Lógico:** dados de natureza lógica binária, ou "números booleanos". Um dado bool só pode receber dois valores possíveis: True ou False.

Python é inteligente o suficiente para detectar o tipo do dado guardado em uma variável. Ou seja, você não precisa especificar que vai guardar um inteiro ou uma string:

```python
a = 2 # python detecta automaticamente que a é um int
b = "tutu" # python detecta automaticamente que b é uma str
c = True # python detecta automaticamente que c é um bool
```

Isso também permite que uma variável troque de tipo quando se troca o dado que ela guarda. Em outras palavras, uma variável que nasceu como inteira se torna string ou ponto flutuante no momento que se troca o dado que ela guarda:

```python
a = 45 # a inicia como variável int
a = 45.2 # agora, a é uma variável float
a = "quarenta e cinco ponto dois" # e agora, uma str
```

Mesmo sendo possível essa troca de tipo dinamicamente, não é considerado uma boa prática de programação resignificar uma variável num mesmo programa. Se suas variáveis representam coisas muito diferentes em momentos diferentes do programa, isso tornará seu código mais difícil de ser lido e interpretado por outras pessoas. Portanto e por exemplo, se uma variável chamada 'num' foi criada carregando um número ponto flutuante, é boa prática que ela permaneça armazenando pontos flutuantes por toda a vida.

Python possui uma função muito útil capaz de retornar o tipo de dado de uma variável: type()

```python
raiz = 4
print(type(raiz))

>>RESULTADO:
int
```

```python
cpf = "123456789"
print(type(cpf))

>>RESULTADO:
str
```
