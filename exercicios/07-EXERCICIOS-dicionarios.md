## EXERCÍCIOS 07: Dicionários

**7.1:** Carregue seu programa com o dicionário abaixo:

```python
coef = {"a" : 2, "b" : -1, "c" : 3}
```

Usando o operador de acesso ```[]``` e o dicionário ```coef```, encontre o valor de ```x``` tal que ```x = (2a + 5c) / b```.

**7.2:** Carregue seu programa com o dicionário abaixo:

```python
contatos = {
    "Marcos" : "marcos_bezzera@bol.com.br",
    "Maria" : "marysilva_@google.com",
    "Carol" : "mckarol2@yahoo.com.br",
    "Pedro" : "petterpotter@altavista.com",
    "Jefferson" : "jeff77@msn.com"
}
```

Percorra o dicionário mostrando a mensagem ```O email de {FULANO} é {EMAIL}```,  tal que {FULANO} e {EMAIL} são as chaves e valores do dicionário, respectivamente.

**7.3:** Usando dicionários, escreva um programa que gera listas de compras; salve o nome dos produtos e as quantidades de cada um a serem compradas. A lista de compras deve começar vazia e ser populada com 5 itens entrados via teclado. Ao final, mostre o contéudo da lista de compras.

**7.4:** Usando dicionários, escreva um programa que guarda os 5 números favoritos de 3 pessoas. Construa o dicionário via teclado ou de maneira estática. Ao final, mostre, para cada pessoa:

- a soma dos números favoritos
- o maior número favorito
- o menor número favorito

**7.5:** Você foi contratado para elaborar o sistema _log_ de um sistema. A primeira coisa que você fez foi procurar na internet o que é um _log_ e encontrou essa descrição:

> **_Log_**, **_SysLog_** ou **_Arquivo de Log_** são expressões para descrever o processo de registro de eventos de um sistema. _Logs_ guardam informações sobre acontecimentos do sistema, como quando um erro ocorreu, quando um driver foi carregado ou quando um usuário entrou/saiu do sistema.

De posse dessa descrição, projete um dicionário que guarda múltiplos eventos de um sistema. Cada evento deve ser registrado como ```eventN```, on ```N``` é um número inteiro começando por zero. Cada evento deve ter três campos: data e hora que aconteceu, tipo de evento e descrição mais detalhada. A nomenclatura das chaves e a definição dos tipos de dados guardados é responsabilidade do projetista (você, no caso).
