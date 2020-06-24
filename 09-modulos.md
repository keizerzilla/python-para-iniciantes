## AULA 09: Biblioteca Padrão do Python

Além da sintaxe básica da linguagem, Python oferece uma vasta biblioteca de funções já prontas que almejam facilitar a vida do programador e tornar Python um linguagem portável ao longo de várias plataformas diferentes. A biblioteca padrão oferece recursos que facilitam a resolução de problemas cotidianos de programação, como manipulação de arquivos, entrada/saída, análise matemática e comunicação em rede, para citar apenas alguns poucos.

Nesta aula, veremos como acessar funções da biblioteca padrão e daremos alguns poucos exemplos de módulos bastante úteis; seria necessário um livro inteiro para comentar cada um dos módulos básicos e suas respectivas funções, que, até a redação desta aula, acumulavam mais de 300 funções.

Veremos no final desta aula como instalar da internet módulos criados pela comunidade de programadores Python através do Gerenciador de Pacotes Python, o ```pip```. Na próxima aula, Funções, veremos como construir nossos próprios módulos.

### Arquitetura de software: Biblioteca, Módulos e Componentes

Um **módulo** é um conjunto de códigos já prontos que resolvem problemas de uma certa natureza. Por exemplo, imagine um módulo para ajudar na comunição com um servidor de arquivos; ele terá funções que ajudam a abrir e fechar uma conexão, transferir e receber dados e configurar protocolos de comunicação. Ou um outro módulo que facilite a construção de interfaces gráficas; criar uma janela, adicionar elementos como botões e menus, definir iteratividade com o mouse e teclado, entre outros.

Os elementos de um módulo são chamados de **componentes**. Os exemplos mais comuns de componentes são funções, constantes e classes (não discutidas neste curso). Um módulo bem escrito ataca um problema específico e somente ele, como mostramos nos exemplos do parágrafo anterior. Um módulo que, ao mesmo tempo, possui funcionalidades de naturezas distintas (análise estatística e manipulação de áudio, por exemplo) não é considerado um produto de boa prática de programação.

Por fim, **biblioteca** é um conjunto de módulos. Assim como uma biblioteca do mundo real, com várias estantes com livros de diversas áreas do conhecimento, um biblioteca de programação acumula módulos com recursos de vários contextos. A figura abaixo esquematiza melhor a relação entre biblioteca, módulos e componentes.

![Arquitetura simples de uma biblioteca com três módulos.](https://i.imgur.com/68KTjbI.png)
### Acessando módulos em Python: ```import```

Chamamos de "importar" o ato de carregar em nosso programa um módulo externo. Para isso, Python conta com uma sintaxe de importação baseada na palavra ```import```:

```
import <nome_do_modulo>
```

Por exemplo, vamos carregar o módulo ```math```, que agrupa funcionalidade matemáticas gerais. Dentro de ```math``` temos a função ```sqrt()```, que calcula a raíz quadrada de um número. Acessamos a função do módulo a partir do operador ponto ```.```:

```python
import math

numero = 16
raiz = math.sqrt(numero)
print(raiz)
#>4.0
```

### Carregando apenas algumas funcionalidades: ```from```

Quando carregamos um módulo como no exemplo anterior, estamos importando o conjunto completo de funcionalidades daquele módulo. Entretanto, muitas vezes estamos interessados em apenas um ou poucos recursos, tornando desnecessário carregar o módulo inteiro. Podemos especificar o que queremos importar usando a sintaxe da palavra ```from```. Em inglês, ```from``` significa "**de/do/da**", então podemos interpretála como _"do módulo **X**, importe a funcionalide **Y**"_. Podemos reescrever o último exemplo assim:

```python
from math import sqrt

numero = 16
raiz = sqrt(numero)
print(raiz)
#>4.0
```

Podemos separar vários recursos que queremos carregar de um mesmo módulo usando vírgulas:

```python
from math import sqrt, factorial

numero = 16
raiz = sqrt(numero)
fatorial = factorial(numero)
print("Raiz =", raiz)
print("Fatorial =", fatorial)
#>4.0
#>20922789888000
```

### Carregando todas as funcionalidades sem acesso pelo modulo: ```*```

Podemos usar o símbolo estrela ```*``` (o mesmo do operador de múltiplicação) para representar "**tudo**". Usando a sintaxe do ```from```, podemos importar todas as funcionalidades de um módulo. Em termos práticos isso significa o mesmo que apenas ```import <nome_modulo>```, mas sem a necessidade de acessar as funções via operador ponto ```.```:

```python
# este exemplo funciona tal qual o último
# note que o uso das funções sqrt() e factorial() não mudou em nada
# entretanto, agora temos acesso a TODAS as demais funcionalidades do modulo math
# e, como já explicado, sem a necessidade de acessá-los usando o operador .
from math import *

numero = 16
raiz = sqrt(numero)
fatorial = factorial(numero)
print("Raiz =", raiz)
print("Fatorial =", fatorial)
#>4.0
#>20922789888000

# ceil() e floor() são outras duas funções do modulo math
# como importamos tudo usando a estrela *, essas funções também estão disponíveis
valor = 2.66
arredondado_cima = ceil(valor)
arredondado_baixo = floor(valor)
print("Valor arredondado para cima:", arredondado_cima)
print("Valor arredondado para baixo:", arredondado_baixo)
#>3
#>2
```

### Apelidos para módulos e funções: ```as```

Python permite darmos apelidos a módulos e funções carregadas usando a palavra ```as```, do inglês "como". Usando a sintaxe simples do ```import```, podemos importar o pacote matemática ```math``` com um novo nome fazendo ```import math as matematica```. Podemos ler essa instrução como _"importe **math** com o apelido **matematica**"_. Por exemplo:

```python
import math as matematica

numero = 16
raiz = matematica.sqrt(numero)
print(raiz)
#>4.0
```

Também podemos usar o operador de apelido ```as``` para funções importadas individulamente com o uso do ```from```:

```python
from math import sqrt as raiz_quadrada
from math import degrees as converte_graus

numero = 25
raiz = raiz_quadrada(numero)
print("Raiz de", numero, "vale", raiz)
#>Raíz de 25 vale 5.0

angulo_radianos = 3.14
angulo_graus = converte_graus(angulo_radianos)
print(angulo_radianos, "radianos é o mesmo que", angulo_graus, "graus")
#>3.14 radianos é o mesmo que 179.9087476710785 graus
```

### Constantes

Constantes são um dos tipos de componentes que podem ser encontrados dentro de módulos. Como o nome já sugere, constantes são valores pré-definidos e imutáveis. Por exemplo, vejamos o módulo ```sys```, que possui funcionalidades que permitem um programa interagir mais intimamente com o interpretador Python. Algumas constantes de sistema encontradas nesse pacote são ```platform```, que guarda o nome da plataforma de sistema operacional que está executando o programa, e ```version```, que mostra a versão do interpretador em uso:

```python
import sys

print(sys.platform)
#>win32

print(sys.version)
#>3.7.7 (tags/v3.7.7:d7c567b08f, Mar 10 2020, 09:44:33) [MSC v.1900 32 bit (Intel)]
```

### Exemplos de módulos da biblioteca padrão

Dentre as dezenas de módulos da biblioteca padrão do Python, mencionaremos apenas 6 sendo que não cobriremos o conjunto de todas as suas funcionalidades. Como já mencionado no início da aula, seria necessário um livro inteiro para discutir cada funcionalidade individual. A lista compilada serve para criarmos familiaridade com o uso de módulos. Recomendamos também o uso constante da documentação oficial da linguagem, que em sua versão 3 pode ser acessada em [https://docs.python.org/pt-br/3/library/](https://docs.python.org/pt-br/3/library/).

Os módulos escolhidos foram ```math```, ```random```, ```sys```, ```textwrap```, ```time``` e ```os```. A Figura abaixo mostra, em diagrama de blocos como no primeiro exemplo da aula, as funções e constantes que abordaremos de cada módulo.

![Alguns módulos padrão do Python e algumas de suas funcionalidades.](https://i.imgur.com/mHxV3Wt.png)
#### ```math```: pacote matemático

```python
import math

# ------------------------
#         FUNÇÕES
# ------------------------

# math.ceil(x)
# - arrendonda o número 'x' para o primeiro inteiro maior ou igual a 'x'
# - em outras palavras, arredonda para cima
valor = 7.77
arredondado_cima = math.ceil(valor)
print(arredondado_cima)
#>8

# math.floor(x)
# - arrendonda o número 'x' para o primeiro inteiro menor ou igual a 'x'
# - em outras palavras, arredonda para baixo
valor = 11.33
arredondado_baixo = math.floor(valor)
print(arredondado_baixo)
#>11

# math.factorial(x)
# - retorna o fatorial do número 'x', que deve ser estritamente positivo
numero = 5
fatorial = math.factorial(numero)
print(fatorial)
#>120

# math.srqt(c)
# - retorna a raíz quadrada do número 'x'
numero = 36
raiz = math.sqrt(numero)
print(raiz)
#>6

# math.degrees(x)
# - converte o número 'x' em radianos para graus
angulo1 = 3.14
angulo_graus = math.degrees(angulo1)
print(angulo_graus)
#>179.9087476710785

# math.radians(x)
# - converte o número 'x' em graus para radianos
angulo2 = 45
angulo_radianos = math.radians(angulo2)
print(angulo_radianos)
#>0.7853981633974483

# math.sin(x)
# - calcula o seno do ângulo 'x' (deve ser passado em radianos)
angulo3 = 5.66
seno = math.sin(angulo3)
print(seno)
#>-0.5836246614030073

# math.cos(x)
# - calcula o cosseno do ângulo 'x' (deve ser passado em radianos)
angulo4 = 0.666
cosseno = math.cos(angulo4)
print(cosseno)
#>0.786299332640184

# math.tan(x)
# - calcula a tangente do ângulo 'x' (deve ser passado em radianos)
angulo5 = 1.11
tangente = math.tan(angulo5)
print(tangente)
#>2.014338214476828

# ------------------------
#        CONSTANTES
# ------------------------

# math.pi
# - o Número Pi até a 15ª casa decimal
print(math.pi)
#>3.141592653589793

# math.e
# - o Número de Euler até a 15ª casa decimal
print(math.e)
#>2.718281828459045

# math.inf
# - o maior número possível de ser guardado em um valor inteiro na memória
print(math.inf)
#>inf
```

#### ```random```: manipulação de números pseudo-aleatórios

```python
import random

# ------------------------
#         FUNÇÕES
# ------------------------

# random.randint(a, b)
# - retorna um número inteiro aleatório uniformente escolhido entre'a' e 'b'
num = random.randint(1, 10)
print(num)
#>8
num = random.randint(1, 10)
print(num)
#>10

# random.uniform(a, b)
# - retorna um número ponto-flutuante uniformement escolhido entre 'a' e 'b'
num2 = random.uniform(0, 5)
print(num2)
#>0.4732719074389541
num2 = random.uniform(0, 5)
print(num2)
#>2.2612863496330995

# random.choice(seq)
# - retorna um elemento escolhido aleatoriamente dentro da lista 'seq'
nomes = ["ednaldo", "birina", "fegue", "lenha"]
escolhido = random.choice(nomes)
print(escolhido)
#>birina
nomes = ["ednaldo", "birina", "fegue", "lenha"]
escolhido = random.choice(nomes)
print(escolhido)
#>lenha

# random.shuffle(seq)
# - embaralha os elementos da lista 'seq'
nomes = ["artur", "rodrigues", "rocha", "neto"]
print(nomes)
#>nomes = ["artur", "rodrigues", "rocha", "neto"]
random.shuffle(nomes)
print(nomes)
#>['rocha', 'rodrigues', 'neto', 'artur']

# random.sample(seq, k)
# - retorna uma lista com 'k' elementos escolhidos aleatoriamente em 'seq'
valores = [66, -2, 11, 5, 984, 0]
amostras = random.sample(valores, 3)
print(amostras)
#>[0, 5, 66]
amostras = random.sample(valores, 3)
print(amostras)
#>[984, 0, 11]
```

#### ```sys```: interface com o interpretador Python

```python
import sys

# ------------------------
#         FUNÇÕES
# ------------------------

# sys.exit()
# - desliga o interpretador e aborta imediatamente o programa
sys.exit()
# o programa morre aqui /\

# ------------------------
#        CONSTANTES
# ------------------------

# sys.argv
# - uma lista com valores passados na execução do programa via linha de comando
# - um programa em python pode ser executado com "python nome_programa.py" em um terminal
# - é possível passar valores, chamados argumentos, depois do nome do programa
# - o nome do programa sempre é o primeiro argumento
# - exemplo: "python nome_programa.py 12 ednaldo 24" possui 4 argumentos:
# - ["nome_programa.py", 12, "ednaldo", 24]
# - esses argumentos ficam salvos na constante sys.argv
# - imagine que você executou o programa exemplo.py e passou os argumentos 77 e artur:
print(sys.argv)
#> ["exemplo.py", 77, "artur"]

# sys.platform
# - retorna o código da plataforma aonde o interpretador está sendo executado
print(sys.platform)
#>win32

# sys.version
# - retorna a versão do interpretador em uso
print(sys.version)
#>3.7.7 (tags/v3.7.7:d7c567b08f, Mar 10 2020, 09:44:33) [MSC v.1900 32 bit (Intel)]
```

#### ```textwrap```: formatação de grandes strings

```python
import textwrap

# ------------------------
#         FUNÇÕES
# ------------------------

# textwrap.wrap(text, width=70)
# - fatia a string 'text' em pedaços (linhas) com no máximo 'width' caractéres
# - essa função toma cuidado de não dividir palavras em duas
# - o valor padrão de 'width', se não for especificado, é 70
mensagem = "Quando a indústria prospera, os patrões obtêm grandes lucros e não pensam em repartir com os operários. Mas durante a crise, os patrões tratam de despejar sobre os ombros dos operários os prejuízos."
linhas = textwrap.wrap(mensagem, 20)
for linha in linhas:
    print(linha)
#>Quando a indústria
#>prospera, os patrões
#>obtêm grandes lucros
#>e não pensam em
#>repartir com os
#>operários. Mas
#>durante a crise, os
#>patrões tratam de
#>despejar sobre os
#>ombros dos operários
#>os prejuízos.

# textwrap.shorten(text, width)
# - compacta a string 'text' até no máximo 'width' caractéres
# - caso 'text' seja maior que 'width', posiciona-se reticências ao final
aviso = "CUIDADO! Esta zona está em construção. Uso de material de proteção é obrigatório!"
aviso_curto = textwrap.shorten(aviso, 40)
print(aviso_curto)
#>CUIDADO! Esta zona está em [...]
```

#### ```time```: controle de tempo

```python
import time

# ------------------------
#         FUNÇÕES
# ------------------------

# time.sleep(secs)
# - pausa execução do programa por 'secs' segundos
# - no exemplo abaixo, o segundo print será executado 5 segundos depois do primeiro
print("Vou dormir...")
time.sleep(5)
print("Acordei!")
#>Vou dormir...
#>Acordei!

# time.time()
# - retorna a quantidade de segundos (fracionado) desde 1 de janeiro de 1970
# - muito usada para contar tempo entre um ponto e outro de um programa
t1 = time.time()
print(t1)
#>1593028886.0703971
```

#### ```os```: comunicação com sistema de arquivos

```python
import os

# ------------------------
#         FUNÇÕES
# ------------------------

# os.getcwd()
# - retorna o diretório de onde está sendo executado o interpretador
# - experimente e veja o resultado na sua máquina
diretorio = os.getcwd()
print(diretorio)
#>C:\\Users\\tutu\\Desktop\\curso_python

# os.listdir(path=".")
# - retorna uma lista com os nomes do conteúdo (arquivos e pastas) do diretório 'path'
# - se 'path' não for definido, assume-se ".", o que é mesmo que "diretório atual"
arquivos = os.listdir("C:\\Users\\tutu\\Desktop\\exemplo_pasta")
print(arquivos)
#>['database.txt', 'localconfig.txt', 'organizao-pedagogico-1.pdf', 'server-icon.png']

# os.mkdir(path)
# - cria uma pasta no caminho especificado por 'path'
os.mkdir("C:\\Users\\tutu\\Desktop\\nova_pasta_python")

# os.remove(path)
# - apaga o arquivo localizado em 'path'
os.remove("C:\\Users\\tutu\\Desktop\\exemplo_pasta\\database.txt")

# os.rmdir(path)
# - apaga a pasta localizada em 'path' e todo seu conteúdo
os.rmdir("C:\\Users\\tutu\\Desktop\\nova_pasta_python")
```

### Instalando pacotes da internet: o programa ```pip```

Quando instalamos o Python em nosso computador, ele inclui um programa separado que se comunica com o Gerenciador de Pacotes Python, um repositório na internet de módulos (também chamados de pacotes) criados por programadores ao redor do mundo. Esse programa se chama ```pip```.

Para usar o ```pip```, primeiro abra um terminal e navegue até o diretório de instalação do Python. Em muitas instalações do interpretador você não precisa navegar até o diretório, pois ele já trata de expor os programas ao caminho global do sistema, podendo portanto acessá-los de qualquer pasta. De um jeito ou de outro, você pode instalar um pacote rodando:

```
pip install <nome_do_pacote>
```

Para desinstalar um pacote, abra um terminal e faça:

```
pip uninstall <nome_do_pacote>
```

Para mostrar todos os pacotes já instalados, use:

```
pip list
```

Algumas instalações do Python fazem distinção entre os pacotes da versão 2 e da versão 3 da linguagem. Caso você não encontre o programa com nome ```pip```, ele pode estar instalado como ```pip3```. O uso é exatamente o mesmo.

#### Exemplo: instalando o pacote ```mouse```

Como demontração, vamos instalar o pacote ```mouse```, que permite automatizar movimento, cliques e outras manipulações com o ponteiro do mouse do computador. Abra o terminal, navegue até o diretório aonde o ```pip``` está instalado (se necessário) e execute:

```
pip install mouse
```

Agora, vamos escrever um programa de exemplo que move o mouse sozinho o ponteiro até a posição (700, 700) da tela. Vamos usar o modulo ```time``` para criar um pequeno suspense (:

```python
import mouse # o pacote que acabamos de instalar! agora ele está disponível para nós!
import time

print("Eu vou mexer seu mouse sozinho")
print("Solte ele agora para ver, eu espero...")
time.sleep(3)
print("Começando!")
mouse.move(700, 700, duration=2)
print("Viu? (:")
```
