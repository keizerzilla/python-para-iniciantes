## PARTE 07: Dicionários e Strings

Como vimos na aula anterior, a estrutura de listas do Python é bastante poderosa. Sua flexibilidade de manipulação e vasta lista de funções e métodos já prontos para uso as tornam essenciais em quase todo programa escrito na linguagem. As outras estruturas de dados do Python que veremos hoje, dicionários e strings, herdam a flexibilidade das listas por serem intimamente ligadas entre si.

Os dicionários nos permite agrupar dados através da relação entre o que definiremos como "chave" e o seu respectivo "valor". As strings são estruturas já comuns em nosso curso, mas até o momento foram usadas apenas como mensagens de apoio na interação entre usuário e programa; hoje veremos como manipulá-las de forma mais livre.

### Dicionários

Um dicionário é uma estrutura de dados composta por relações entre **chaves** e **valores**. Usamos uma **chave** para acessar o seu respectivo **valor**. Por exemplo, vejamos a tabela abaixo que traz os preços de um conjunto de hortaliças:

| PRODUTO | PREÇO R$ |
|---------|----------|
| Alface  | 0,45     |
| Batata  | 1,20     |
| Tomate  | 2,30     |
| Couve   | 1,50     |

Podemos construir uma dicionário que representa essa tabela de forma que as chaves serão os nomes das hortliças e os valores, seus respectivos preços.

- usamos o operador ```{}``` para criar o dicionário
- separamos as chaves dos valores usando ```:```
- assim como nas listas, seperamos os elementos entre si usando ```,```
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

Um dicionário vazio seria escrito apenas como ```{}```.

Podemos rescreever a mesma declaração acima de uma forma mais organizada e legível, posicionando cada elemento do dicionário numa linha separada:

```python
tabela = {
    "Alface" : 0.45,
    "Batata" : 1.20,
    "Tomate" : 2.30,
    "Couve" : 1.50
}
```

**ATENÇÃO:** Tanto as chaves quanto os valores podem ser de qualquer tipo. Entretanto, é boa prática que as chaves sejam escritas como strings.

A inclusão de novos elementos nos dicionários é mais flexível que nas listas. Quando atribuímos um valor a uma chave, duas coisas podem acontecer:

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
```

Tentar acessar uma chave que não existe gera um erro do tipo ```KeyError```.

#### Manipulando chaves e valores

Veremos agora uma sequência de operador, funções e métodos já embutidos no Python para manipulação de dicionários.

Podemos verificar se uma chave existe no dicionário usando o operador ```in```:

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

A remoção de um elemento é feita através do operador ```del```:

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

O tamanho (número de elementos) de um dicionário é retornado usando a função ```len()```:

```python
tabela = {
    "Artur" : True,
    "Arthur" : False,
    "Arthu" : False,
}

print(len(tabela))
#>3
```

Podemos retornar uma lista com todas as chaves usando o método ```keys()``` e todos os valores usando o método ```values()```:

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

Assim como as listas, os dicionários são objetos referenciados; para criar uma cópia, usamos o método ```copy()```:

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

O método ```clear()``` serve para apagar todo o conteúdo de uma lista:

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
O método ```items()``` retorna pseudo-tuplas onde o primeiro valor é uma chave e o segundo, o valor respectivo; esse método é bastante usando para percorrermos o dicionário usando um laço ```for```:

```python
agenda = {
    "Antônio" : 33429192,
    "Maria" : 23451918,
    "Roberto" : 99015544,
    "Marcos" : 33427640
}

for chave, valor in agenda.items():
    print("O telefone de", chave, "é", valor)

#>O telefone de Antônio é 33429192
#>O telefone de Maria é 23451918
#>O telefone de Roberto é 99015544
#>O telefone de Marcos é 33427640
```

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

### Strings

Strings, ou "cadeias de caractéres", são sequências de caractéres delimitados por chaves duplas ```"``` ou simples ```'```. Por serem um tipo de dado sequência, a maioria das manipulações possíveis com listas também são possíveis com strings.

```python
# - podemos acessar caractéres individuais usando o operador de acesso []
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

# - a função len() retorna o tamanho da string, ou seja, quantos caractéres ela possui
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

#### Métodos de strings

CONTINUAR...
