## EXTRA: Instalando Python do zero e usando pip

### Download

O site oficial é python.org, onde você encontra várias opções de download. Na aba Download você encontra um botão para a versão mais recente da linguagem. Uma vez baixado, o processo de instalação é bem simples; a única atenção aqui é não esquecer de marcar a opção "Add Python 3.x to PATH" (o 'x' muda de versão em versão, não importa). Depois de marcar essa opção, bastar escolher "Install Now" e esperar o processo acabar.

![Instalação](https://i.imgur.com/X9vTnTq.png)

Ao final, você pode abrir um terminal (basta procurar por cmd.exe na busca do Menu Iniciar) e experimentar os comando _python_ (abre o interpretador) e _pip_ (o gerenciador de pacotes).

![Teste](https://i.imgur.com/FGOoeyp.png)
### Instalando pacotes via pip direto no Mu

O Python organiza os pacotes e módulos no que ele chama de "ambiente" (em inglês é _environment_). Por padrão, se você tentar instalar algum pacote via pip configurado nos passos anteriores, esse pacote será colocado no ambiente padrão do Python, e não no ambiente do nosso editor escolhido, o Mu. Por sorte, é possível especificar o ambiente aonde se quer instalar o pacote. O comando básico de instalação de um pacote via pip é:

```
pip install <nome_pacote>
```

Podemos adicionar mais um parâmetro nesse comando para dizer aonde instalar:

```
pip install <nome_pacote> --target <pasta_pkgs_outro_canto>
```

Para facilitar a nossa vida, o Mu é instalado em uma pasta de sistema genérica e fácil de localizar. A pasta "pkgs" dele fica em "%localappdata%\Mu\pkgs". Como exemplo, vamos supor que queremos instalar o pacote **mouse** no ambiente do Mu. Modificando o comando acima, temos:

```
pip install mouse --target "%localappdata%\Mu\pkgs"
```

E pronto! Agora o módulo **mouse** está disponível em programas escritos no Mu. E o mais legal: esse processo pode ser repetido para qualquer outro pacote.
