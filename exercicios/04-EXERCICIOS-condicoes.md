## EXERCÍCIOS 04: Condições

A lista de exercícios propostos abaixo é a mais extensa até o momento. Não há, intencionalmente, um aumento no nível de dificuldade a cada programa. Portanto, caso você tenha dúvidas: 1) use o nosso espaço no servidor para pedir ajuda e 2) não fique estancado em um programa e tente resolver outro.

Alguns programas necessitam de uma lógica não explicitada no enunciado. Use quaisquer conhecimentos prévios seus ou pesquise na internet para descobrir as peças que faltam para estes casos. Use nosso espaço para pedir ajuda aos colegas, mas atenção: para você que vai prestar ajuda, não dê a resposta já em código! Explique a lógica que falta, mas deixe a parte da implementação (ou seja, a transformação em código) para o colega que pediu ajuda!

_**DIVIRTA-SE!**_

**4.1:** Escreva um programa que leia três números e que imprima o maior deles.

**4.2:** Escreva um programa que leia três números e que imprima o maior e o menor deles.

**4.3:** Como técnico de informática do departamento de trânsito estadual, você recebeu a tarefa de escrever o protótipo do novo sistema de multas. Escreva um programa que pergunte a velocidade do carro do usuário. Caso ultrapasse 80 km/h, exiba uma mensagem avisando o usuário que ele foi multado e o valor da multa, calculada como R$ 5,00 por km acima de 80.

**4.4:** Você foi contratado pelo setor financeiro de uma empresa. A empresa promoverá aumentos de salário a todos os empregados. Foi requisitado um programa que calcula o valor desse aumento, que é calculado com base no salário atual. Para salários superiores a R$ 1.250,00, o aumento será de 10%. Para inferiores ou iguais a este valor, 15%.

**4.5:** Uma empresa de ônibus interestadual precisa de um programa que calcula o preço de uma viagem com base na distância percorrida. O programa deve perguntar a distância, em km, de uma viagem e calcular o seu preço, cobrando R$ 0,50 por km para viagens de até 20 km e R$ 0,45 para viagens mais longas.

**4.6:** Escreva um programa que leia dois números e que pergunte qual operação aritmética você deseja realizar. As operações possíveis são adição (+), subtração (-), multiplicação (*) e divisão (/). Exiba o resultado da operação realizada.

**4.7:** Escreva um programa que calcula a conta de energia elétrica de um dado endereço. O programa deve perguntar quantos kWh foram consumidos e qual a categoria do endereço: residencial, comercial ou industrial. Use a tabela abaixo, que relaciona categoria e consumo, para saber o preço por kWh consumido:

| CATEGORIA   | CONSUMO (kWh) | PREÇO   |
|-------------|---------------|---------|
| Residencial | até 500       | R$ 0,40 |
|             | acima de 500  | R$ 0,65 |
| Comercial   | até 1000      | R$ 0,55 |
|             | acima de 1000 | R$ 0,60 |
| Industrial  | até 5000      | R$ 0,55 |
|             | acima de 5000 | R$ 0,60 |

**4.8:** Escreva um programa que leia um número e que diz se ele é par ou ímpar (DICA: operador aritmético ```%```).

**4.9:** Escreva um programa que leia um número e que diz se ele é positivo ou negativo.

**4.10:** Escreva um programa que leia as 3 notas parciais de um aluno ao longo de uma disciplina. Depois, calcule a média dessas 3 notas. Por fim, o programa deve mostrar se o aluno foi aprovado (média maior que 7), reprovado (média menor que 7) e, caso aprovado, se foi com louvor (média maior que 9).

**4.11:** Escreva um programa que leia um número e exiba o dia da semana correspondente (1- Domingo, 2- Segunda, etc). Se o número for inválido, o programa deve avisar o usuário do erro.

**4.12:** Escreva um programa que leia as 4 notas parciais de um aluno ao longo de uma disciplina. Depois, calcule a médias dessas 4 notas. Depois, exiba o conceito alcançado com base na média a partir da tabela abaixo:

| MÉDIA            | CONCEITO |
|------------------|----------|
| entre 9.0 e 10.0 | A        |
| entre 7.5 e 9.0  | B        |
| entre 6.0 e 7.5  | C        |
| entre 4.0 e 6.0  | D        |
| entre zero e 4.0 | E        |

**4.13:** Escreva um programa que leia um ano (ex: 1917) e que informe se este é ou não bissexto.

**4.14:** Faça um programa que avalia o nível de suspeita de um indivíduo com relação a um crime. O programa deve fazer as seguintes perguntas:

> 1- Telefonou para a vítima?
>
> 2- Esteve no local do crime?
>
> 3- Mora próximo da vítima?
>
> 4- Devia para a vítima?
>
> 5- Já trabalhou com a vítima?

Ao final, o programa deve exibir uma classificação do indivíduo. Caso 2 respostas forem positivas, ele deve ser classificado como "SUSPEITO". Entre 3 e 4 respostas positivas, "CÚMPLICE". Se as 5 forem positivas, "ASSASSINO". Caso contrário, ele será classificado como "INOCENTE".
