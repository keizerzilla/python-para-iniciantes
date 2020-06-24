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

![Alguns módulos padrão do Python e algumas de suas funcionalidades.](https://i.imgur.com/t0NfRFk.png)
### ```math```: pacote matemático

```python
```

### ```random```: manipulação de números pseudo-aleatórios

```python
```

### ```sys```: interface com o interpretador Python

```python
```

### ```textwrap```: formatação de grandes strings

```python
```

### ```time```: controle de tempo

```python
```

### ```os```: comunicação com sistema de arquivos

```python
```


