## AULA 11: Arquivos

Imagine todos os tipos de arquivos que manipulamos diariamente: documentos, imagens, músicas, vídeos, planilhas, jogos, para citar apenas alguns! Essa pequena reflexão já deve ser suficiente para mostrar o quanto eles são importantes em computação. Mas apenas a informação armazenada não é importante: precisamos de um programa que as manipule, visualize e seja lá quais outras tarefas queremos fazer. É aí que nós, programadores, entramos.

### Uma definição histórica

Arquivos não são novidades trazidas com o computador digital. O ser humano cria arquivos desde que ele desenvolveu as primeiras formas de linguagem há milhares de anos. Ao registrar sua vida e seus conhecimentos nas paredes das cavernas, cascas de árvore, placas de pedra, rolos de papel, couro de animais e livros, o homem já "arquivava" dados e informações para serem preservados bem depois que ele já não estivesse vivo.

Em resumo, arquivos são nada mais que registros de informações. O meio usado para guardá-las pode variar, mas em computação nós temos uma abstração única: o disco.

Chamamos de disco o dispositivo de persistência de dados do computador. Persistência significa que, ao desligarmos o computador, aqueles dados não serão perdidos. Damos esse nome por motivos históricos, já que os primeiros dispositivos eram discos magnéticos lidos através de um sensor que varria os dados enquanto o disco girava. Mesmo hoje com outras tecnologias mais eficazes, o termo disco continua sendo usado como coringa para se referir a qualquer dispositivo de armazenamento persistente: HDs, pendrives, CDs, SSDs, etc.

O disco é também conhecido como "memória secundária", pois sua função é apenas armazenar dados. A "memória principal" é aquela aonde os dados são armazenados temporariamente para serem manipulados, mas que se perdem assim que desligamos a máquina. O tipo de memória principal mais comum é a RAM.

Em resumo: um **arquivo** é uma região em **disco** onde podemos ler e gravar informações.

O sistema operacional do computador é responsável por gerenciar os arquivos do sistema. Quando queremos manipular arquivos em nossos programas, usamos funções que conversam com o sistema operacional pedindo permissão para abrir, ler, gravar e fechar arquivos. Python abstrái todas as rotinas intermediárias necessárias e disponibiliza para nós funções fáceis de serem usadas.

### Tarefas básicas de manipulação de arquivos

Sempre que manipulamos arquivos, devemos nos atentar a uma sequência de tarefas essenciais: **abrir**, **usar**, **fechar**. Cada tarefa possui uma ou mais funções associadas:

![Tarefas básicas com arquivos](https://i.imgur.com/iAwLeD3.png)

Veremos como usar cada uma das funções de arquivo nos tópicos a seguir. Lembrando que funções que iniciam com ponto ```.``` são chamadas de métodos e são invocadas a partir de variáveis especiais chamadas de objetos.

### Abrindo e fechando arquivos: as funções ```open()``` e ```.close()```

Precisamos de duas coisas para acessar arquivos: o **nome** do arquivo e um **modo** de acesso. Com essas duas informações em mãos, podemos usar a função ```open()``` do Python para abrir um arquivo. Ela trata de pedir permissão ao sistema operacional para usarmos o arquivo. A função ```open()``` retorna um objeto que representa o arquivo que acabamos de abrir e com ele seremos capaz de manipular seu contéudo em nosso programa.

Uma vez que não precisamos mais usar o arquivo, devemos fechá-lo usando a função ```.close()```. Fechar um arquivo é importantíssimo, pois essa é a maneira que temos de avisar o sistema operacional que já terminamos de usá-lo e assim ele pode liberar quaisquer recursos de sistema que estejam em uso.

O exemplo mais simples possível que apenas abre um arquivo e depois o fecha é:

```python
arquivo = open("dados.txt", "rt")
# instruções que manipulam o arquivo...
arquivo.close()
```

Vamos agora detalhar os parâmetros da função ```open()```.

O **nome do arquivo** é o seu identificador único. É o "caminho" dentro do sistema que aponta onde no disco aqueles dados se encontram. Pode ser o caminho completo (usando todos os diretórios desde da origem até o arquivo) ou apenas o caminho relativo (a partir do diretório onde está localizado o programa). Esse parâmetro é sempre uma string. No exemplo acima, passamos ```"dados.txt"``` pois imaginamos que o arquivo está no mesmo diretório que o programa, assim não é necessário especificar o caminho completo.

O **modo de acesso** diz o que queremos fazer com o arquivo, seja leitura, escrita ou atualização, além do tipo de dado armazenado, texto ou binário. Abordaremos em nosso curso apenas arquivos de tipo texto. O exemplo anterior abriu o arquivo ```"dados.txt"``` em modo de leitura em texto. O parâmetro modo também é uma string. A tabela a seguir mostra os códigos de cada modo de acesso possível:

| **Modo** | **Operações**                                 |
|----------|-----------------------------------------------|
| ```r```  | leitura                                       |
| ```w```  | escrita (apaga conteúdo se existir)           |
| ```a```  | escrita (preserva conteúdo, escreve no final) |
| ```+```  | atualização (leitura e escrita)               |

Além do caractere de modo, devemos usar o código de tipo de arquivo:

- ```t```: arquivos de texto
- ```b```: arquivos em binário

Portanto, se quisersmos abrir um arquivo para leitura em texto, usaremos o código ```"rt"```; atualização em binário seria ```"+b"``` e escrita em texto ficaria ```"wt"```, por exemplo. A ordem dos códigos de modo e tipo não importa. Qualquer combinação é possível. Se o modo de arquivo não for especificado, a função ```open()``` usará ```"rt"``` como valor padrão.

### Para facilitar: ```.write()``` é o mesmo que ```print()```

Ambas as funções servem para _escrever_ strings. A diferença é que uma escreve em arquivo, a outra no console.

### Para facilitar: ```.read()/.readline()``` é o mesmo que ```input()```

Ambas as funções servem para _ler_ strings. A diferença é que uma lê de um arquivo, a outra do console.

### Escrevendo em arquivos: a função ```.write()```

Usamos a função ```.write()``` para escrever dados em um arquivo. Ela é chamada pelo objeto que representa o arquivo onde queremos escrever e seu parâmetro é um string com aquilo que deve ser escrito. Por exemplo, vamos criar um arquivo chamado ```"nome.txt"``` em modo de escrita em texto e escrever a string ```Ednaldo Pereira``` nele:

```python
arquivo = open("nome.txt", "wt")
arquivo.write("Ednaldo Pereira")
arquivo.close()
```

Após a execução, você perceberá que um arquivo foi criada no mesmo diretório do seu programa. Abra-o usando o Editor de Texto do seu sistema operacional e verifique que seu conteúdo é:

>Ednaldo Pereira

Cada novo conteúdo escrito será posicionado ao final do arquivo. No exemplo abaixo, queremos escrever múltiplas linhas no arquivo ```"nomes.txt"```, mas você verá que não conseguiremos:

```python
# VERSÃO 01
arquivo = open("nomes.txt", "wt")
arquivo.write("Ednaldo Pereira")
arquivo.write("Birina")
arquivo.write("Fleig")
arquivo.write("Chico Melancia")
arquivo.close()
```

Se abrirmos ```"nomes.txt"``` no Editor de Texto, veremos:

>Ednaldo PereiraBirinaFleigChico Melancia

Se quiseremos escrever mais de uma linha no arquivo, precisamos especificar o caractere de nova-linha ```\n``` ao final da string escrita, senão os conteúdos serão postos em sequência:

```python
# VERSÃO 02
arquivo = open("nomes.txt", "wt")
arquivo.write("Ednaldo Pereira\n")
arquivo.write("Birina\n")
arquivo.write("Fleig\n")
arquivo.write("Chico Melancia\n")
arquivo.close()
```

Agora o conteúdo de ```"nomes.txt"``` está correto:

>Ednaldo Pereira
>Birina
>Fleig
>Chico Melancia

É comum queremos escrever conteúdos gerados algoritmicamente em um arquivo. Por exemplo, digamos que nosso programa gera um arquivo com a sequência de números de 1 a 10. Podemos implementá-lo usando um laço ```for``` usando a função ```range()``` e escrever número a número com a ajuda da função ```.write()```:

```python
arquivo = open("numeros.txt", "wt")

for num in range(1, 11):
    arquivo.write(str(num) + "\n")

arquivo.close()
```

Depois de executarmos o programa acima, o arquivo ```"numeros.txt"``` deverá ter o seguinte conteúdo:

>1
>2
>3
>4
>5
>6
>7
>8
>9
>10

### Lendo arquivos: as funções ```.read()``` e ```.readline()```

Vamos imaginar um arquivo texto com o seguinte conteúdo:

>Ola, Mundo!

Experimente criá-lo usando o Editor de Texto do seu sistema operacional. Salve-o com o nome ```"ola.txt"```. Agora, no mesmo diretório onde você salvou o arquivo texto, crie um programa Python com o código abaixo:

```python
arquivo = open("ola.txt", "rt")
conteudo = arquivo.read()
print(conteudo)
arquivo.close()
```

Execute o programa. Você deverá ver no console:

```
Ola, Mundo!
```

Abrimos o arquivo no modo de leitura em texto usando o modo ```"rt"```. Assim, o arquivo foi aberto e pronto para ser lido. A função ```.read()``` lê o conteúdo completo de um arquivo e o armazena numa variável.

Se por um acaso nosso arquivo fosse chamado ```linhas.txt``` e tivesse um conteúdo maior, como:

>Essa eh a primeira linha do arquivo.
>Agora a segunda!
>Por fim, a terceira.

Mudando apenas o nome do arquivo a ser aberto:

```python
arquivo = open("linhas.txt", "rt")
conteudo = arquivo.read()
print(conteudo)
arquivo.close()
```

A saída também muda:

```
Essa eh a primeira linha do arquivo.
Agora a segunda!
Por fim, a terceira.
```

Mais uma vez: a função ```.read()``` carrega o conteúdo completo. Se o objetivo fosse ler linha por linha, usamos a função ```.readline()```. Cada vez que a chamamos ela carrega a próxima linha do arquivo. Se não houver mais linhas para ler, ```.readline()``` retorna uma string vazia.

```python
arquivo = open("linhas.txt", "rt")

linha = arquivo.readline()
print(linha)
#>Essa eh a primeira linha do arquivo.
#>

linha = arquivo.readline()
print(linha)
#>Agora a segunda!
#>

linha = arquivo.readline()
print(linha)
#>Por fim, a terceira.
#>

arquivo.close()
```

Na grande maioria das vezes nós não sabemos quantas linhas possui o arquivo, portanto não há como contar quantas vezes precisamos chamar a função ```.readline()```. Mas Python facilita nossa vida ao nos permitir percorrer um arquivo usando um laço do tipo ```for```, pois o objeto que representa oarquivo aberto em modo texto é enxergado como uma "lista de linhas". Podemos reescrever o programa acima de maneira mais elegante assim:

```python
arquivo = open("linhas.txt", "rt")

for linha in arquivo:
    print(linha)

arquivo.close()
#>Essa eh a primeira linha do arquivo.
#>
#>Agora a segunda!
#>
#>Por fim, a terceira.
#>
```

Note que, em ambos os casos, uma linha em branco foi impressa a cada chamada da função ```print()```. Isso acontece porque as linhas carregadas já trazem consigo no final o caractére de nova linha. Como ```print()``` insere um nova-linha também, a saída aparece espaçada duas vezes.

### Arquivos texto: nada mais que manipulação de strings

Vamos supor que temos o mesmo arquivo ```"numeros.txt"``` gerado em um exemplo anterior, contendo os números de 1 a 10. Se quisermos pegar esses valores e mostrar os seus dobros, poderíamos fazer:

```python
arquivo = open("numeros.txt", "rt")

for linha in arquivo:
    num = int(linha)
    print(2*num)

arquivo.close()
#>2
#>4
#>6
#>8
#>10
#>12
#>14
#>16
#>18
#>20
```

Note que apenas precisamos abrir o arquivo em modo de leitura em texto, percorrer cada linha e convertê-las em inteiro usando ```int()```.

Em outro exemplo, imagine que temos um arquivo ```"contatos.txt"``` onde cada linha possui o nome de um contato pessoal:

>ednaldo
>fleig
>chico
>birina
>lenin

Vamos imaginar que queremos criar um outro arquivo chamado ```"contatos_grande.txt"``` que vai guardar os mesmo contatos, só que em caixa-alta. O programa que faz isso deve abrir os dois arquivos, uma para leitura e outro para escrita, e converter os nomes usando o método ```.upper()```:

```python
contatos = open("contatos.txt", "rt")
grande = open("contatos_grande.txt", "wt")

# percorre linhas no arquivo sendo lido
for linha in contatos:
    # converte linha lida para caixa-alta
    nome_grande = linha.upper()
    # escreve linha convertida no outro arquivo
    grande.write(nome_grande)

# fecha ambos arquivos
contatos.close()
grande.close()
```

Perceba que, em ambos os exemplos, a manipulação do arquivo foi uma manipulação de strings feita de maneira um pouco diferente. E de fato, usar arquivos texto nada mais é que manipular strings, a única diferença é de onde elas vem. Portanto, tenha em mente que seus conhecimentos de string devem estar em dia quando for usar arquivo texto.
## EXERCÍCIOS 11: Arquivos

**11.01:** Escreva um programa que gere um arquivo com os números pares de 1 a 100.

**11.02:** Escreva um programa que lê números digitados pelo usuário até que ele entre o valor zero. Gere um arquivo com os números entrados. O zero não deve fazer parte dos números escritos.

**11.03:** Escreva um programa que lê números digitados pelo usuário até que ele entre o valor zero. Escreva os números pares em um arquivo chamado ```pares.txt``` e o ímpares em um segundo arquivo chamado ```impares.txt```. Assim como na questão anterior, o zero não deve fazer parte de nenhum dos arquivos.

**11.04:** Escreva um programa que lê strings quaisquer geradas pelo usuário. Gere um arquivo onde cada linha deve ter os seguintes valores separados por vírgula:

```
<string>,<tamanho_da_string>
```

_Exemplo:_

```
meu nome eh artur,17
ednaldo,7
vladmir lenin,13
```

**11.05:** Escreva um programa que gera listas telefônicas em arquivos de texto. Cada linha do arquivo deve ter o nome do contato, número de telefone e email, todos separados por vírgula:

```
<nome>,<telefone>,<email>
```

Monte a lista com dados entrados via teclado.

**11.06:** Baixe o arquivo [numeros.txt](https://raw.githubusercontent.com/keizerzilla/curso-python-notas/master/dados/numeros.txt). Cada linha desse programa guarda um número inteiro. Escreva um programa que leia esses números e que mostra no console a raíz quadrada de cada um.

**11.07:** Baixe o arquivo [meus_contatos.txt](https://raw.githubusercontent.com/keizerzilla/curso-python-notas/master/dados/meus_contatos.txt). Esse arquivo é um programa de lista de contatos no mesmo formato do que você gerou no exercício 11.05. Aqui o trabalho é de leitura da lista: escreva um programa que leia esse arquivo e mostre no console as informações de nome, número de telefone e email. O visual da apresentação deve ser definido por você (seja criativo!).

**11.08:** Baixe o arquivo [embaralhado.txt](https://raw.githubusercontent.com/keizerzilla/curso-python-notas/master/dados/embaralhado.txt). Esse é um arquivo texto com 1000 linhas. Escreva um programa que encontra a string ```EdnaldoPereira```, que está escondida dentro do arquivo. O programa deve informar o número da linha onde a string foi achada.

