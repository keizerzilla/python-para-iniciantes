## AULA 07: Dicionários

Dicionários, assim como listas, são dados do tipo sequência. Dicionários também podem guardar qualquer tipo de dados, mas esses são acessados de maneira diferente das listas. Ao invês de indíces numéricos, usamos chaves. Em outras palavras, um dicionário é uma estrutura de dados composta por relações entre **chaves** e **valores**; usamos uma *chave* para acessar o seu respectivo *valor*. O conjunto chave mais valor é chamado de **item**. O tipo de um dicionário em Python é ```dict```.

Por exemplo, vejamos a tabela abaixo que traz os preços de um conjunto de hortaliças:

| PRODUTO | PREÇO (R$) |
|---------|------------|
| Alface  | 0,45       |
| Batata  | 1,20       |
| Tomate  | 2,30       |
| Couve   | 1,50       |

A tabela possui 4 entradas, portanto nosso dicionário terá 4 itens. Usaremos a coluna PRODUTO para as chaves e o valor será o correspondente da coluna PREÇO. A sintaxe do Python para construção segue as seguintes regras:

- usamos o operador ```{}``` para criar o dicionário
- separamos as chaves dos valores usando ```:```
- assim como nas listas, separamos os itens entre si usando ```,```
- o acesso a cada valor é feito usando o operador ```[]``` passando a chave

```python
tabela = {"Alface" : 0.45, "Batata" : 1.20, "Tomate" : 2.30, "Couve" : 1.50}

print(tabela)
#>{'Alface': 0.45, 'Batata': 1.2, 'Tomate': 2.3, 'Couve': 1.5}
print(tabela["Alface"])
#>0.45
print(tabela["Tomate"])
#>2.30
print(tabela["Batata"])
#>1.20
print(tabela["Couve"])
#>1.50
```

Um dicionário vazio seria escrito apenas como ```{}```, ou seja, com zero itens:

```python
dic = {}
```

Podemos rescreever a declaração do dicionário ```tabela``` de uma forma mais organizada e legível, posicionando cada item do dicionário numa linha separada:

```python
tabela = {
    "Alface" : 0.45,
    "Batata" : 1.20,
    "Tomate" : 2.30,
    "Couve" : 1.50
}
```

**ATENÇÃO:** Tanto as chaves quanto os valores podem ser de qualquer tipo. Entretanto, é boa prática que as chaves sejam escritas como strings.

### Adição de itens em um dicionário

A inclusão de novos itens num dicionário é mais flexível que nas listas. Quando atribuímos um valor a uma chave, duas coisas podem acontecer:

1. Se a chave já existe, o valor atual é trocado pelo novo valor
2. Se a chave não existe, ela é criada com o valor passado

```python
tabela = {
    "Alface" : 0.45,
    "Batata" : 1.20,
    "Tomate" : 2.30,
    "Couve" : 1.50
}

# mudando o valor de uma chave que já existe
tabela["Alface"] = 1.12
print(tabela["Alface"])
#>1.12

# criando uma nova chave
tabela["Arroz"] = 3.14
print(tabela["Arroz"])
#>3.14
print(tabela)
#>{'Alface': 1.12, 'Batata': 1.2, 'Tomate': 2.3, 'Couve': 1.5, 'Arroz': 3.14}

# ATENÇÃO: tentar acessar uma chave que não existe gera um erro do tipo KeyError:
print(tabela["Arroz"])
#>Traceback (most recent call last):
#>KeyError: 'Arroz'
```

### Manipulando chaves e valores

Veremos agora uma sequência de operadores, funções e métodos já embutidos no Python para manipulação de dicionários.

#### Podemos verificar se uma chave existe no dicionário usando o operador ```in```:

```python
tabela = {
    "Acerola" : 2.45,
    "Maracujá" : 1.30,
    "Laranja" : 0.30,
    "Uva" : 1.70
}

print("Manga" in tabela)
#>False
print("Acerola" in tabela)
#>True
```

#### A remoção de um item é feita através do operador ```del```:

```python
tabela = {
    "Alface" : 0.45,
    "Batata" : 1.20,
    "Tomate" : 2.30,
    "Couve" : 1.50
}

print(tabela)
#>{'Alface': 0.45, 'Batata': 1.2, 'Tomate': 2.3, 'Couve': 1.5}
del tabela["Batata"]
print(tabela)
#>{'Alface': 0.45, 'Tomate': 2.3, 'Couve': 1.5}
```

#### O tamanho (número de itens) de um dicionário é retornado usando a função ```len()```:

```python
tabela = {
    "Artur" : True,
    "Arthur" : False,
    "Arthu" : False,
}

print(len(tabela))
#>3
```

### Métodos de dicionários

- ```.keys()```: retorna uma lista com todas as chaves
- ```.values()```: retorna uma lista com todos os valores
- ```.copy()```: cria uma cópia do dicionário
- ```.clear```: limpa o dicionário (apaga todos os itens)
- ```.update()```: adiciona um novo item ao dicionário
- ```.items()```: gera pseudo-tuplas; primeiro elemento é a chave e segundo elemento, o valor
- ```.get()```: retorna valor de uma chave; se não a encontrar, retorna um valor pré-definido

#### ```.keys()```: retorna uma lista com todas as chaves
#### ```.values()```: retorna uma lista com todos os valores

```python
tabela = {
    "Alface" : 0.45,
    "Batata" : 1.20,
    "Tomate" : 2.30,
    "Couve" : 1.50
}

chaves = tabela.keys()
print(chaves)
#>dict_keys(['Alface', 'Batata', 'Tomate', 'Couve'])
valores = tabela.values()
print(valores)
#dict_values([0.45, 1.2, 2.3, 1.5])

# o tipo dict_values é uma pseudo-lista, assim como as retornadas pela função range()
# você pode transformá-las em listas reais usando a função list()

chaves = list(chaves)
valores = list(valores)
print(chaves)
#>['Alface', 'Batata', 'Tomate', 'Couve']
print(valores)
#[0.45, 1.2, 2.3, 1.5]
```

#### ```.copy()```: cria uma cópia do dicionário

```python
tabela = {
    "Mustang" : 100000,
    "Uno" : 20000,
    "Ferrari" : 500000,
    "BNW" : 200000
}

tabela2 = tabela.copy()
tabela2["Uno"] = 1
print(tabela["Uno"])
#>20000
print(tabela2["Uno"])
#>1
```

#### ```.clear```: limpa o dicionário (apaga todos os itens)

```python
tabela = {
    "Mustang" : 100000,
    "Uno" : 20000,
    "Ferrari" : 500000,
    "BNW" : 200000
}

tabela.clear()
print(tabela)
#>{}
```

#### ```.update()```: adiciona um novo item ao dicionário

```python
carro = {
    "marca" : "Gurgel",
    "modelo" : "BR-800",
    "ano" : 1988
}

carro.update({"cor" : "Cinza"})

print(carro)
#>{"marca" : "Gurgel", "modelo" : "BR-800", "ano" : 1988, "cor" : "Cinza"}
```

#### ```.items()```: gera pseudo-tuplas; primeiro elemento é a chave e segundo elemento, o valor

```python
agenda = {
    "Antônio" : 33429192,
    "Maria" : 23451918,
    "Roberto" : 99015544,
    "Marcos" : 33427640
}

# muito útil em laços for!

for chave, valor in agenda.items():
    print("O telefone de", chave, "é", valor)

#>O telefone de Antônio é 33429192
#>O telefone de Maria é 23451918
#>O telefone de Roberto é 99015544
#>O telefone de Marcos é 33427640
```

#### - ```.get()```: retorna valor de uma chave; se não a encontrar, retorna um valor pré-definido

```python
freq = {
    "oi" : 3,
    "casa" : 65,
    "proletariado" : 18,
    "carro" : 9
}

print(freq.get("oi", 0)) # procura pela chave "oi": se achar, retorna valor; senão, retorna 0
#>3
print(freq.get("proletariado", 0)) # procura pela chave "proletariado": se achar, retorna valor; senão, retorna 0
#>18
print(freq.get("livro", 0)) # procura pela chave "livro": se achar, retorna valor; senão, retorna 0
#>0

# O segundo parâmetro pode ser qualquer valor, não apenas 0!
```

### Percorrendo chaves usando laço ```for```

Se tentarmos percorrer um dicionário de forma direta usando um laço ```for```, estaremos percorrendo suas chaves:

```python
notas = {
    "segunda" : "consulta ao ortopedista",
    "terça" : "comprar roupas no centro fashion",
    "quarta" : "levar o cachorro para tosar",
    "quinta" : "fazer compras do mês",
    "sexta" : "beber"
}

for chave in notas:
    print(chave)

#>segunda
#>terça
#>quarta
#>quinta
#>sexta
```

### Dicionários com listas

Os valores de um dicionário podem ser listas. O acesso a elementos das lista é feita a partir do sequenciamento de operadores de acesso ```[]```: o primeiro para a chave do dicionário e o segundo, para o elemento da lista:

```python
notas = {
    "maria" : [10, 6, 6],
    "roberto" : [4, 5, 7],
    "mauricio" : [9, 9,8],
    "fernanda" : [5, 6, 7]
}

print(notas["maria"])
#>[10, 6, 6]
print(notas["robertos"])
#>[4, 5, 7]
print(notas["mauricio"][0])
#>9
print(notas["fernanda"][1])
#>6
```

### Dicionários aninhados

Os valores de um dicionário podem ser outros dicionários. Assim como nas listas aninhadas e nos dicionários com listas, o acesso é feito usando múltiplos operadores de acesso ```[]```:

```python
familia = {
    "filho1" : {"nome" : "Eduardo", "ano" : 1997},
    "filho2" : {"nome" : "Glauber", "ano" : 2000},
    "filho3" : {"nome" : "José", "ano" : 2005}
}

print(familia["filho1"]["nome"])
#>Eduardo
print(familia["filho2"]["ano"])
#>2000
print(familia["filho3"])
#>{"nome" : "José", "ano" : 2005}
```
