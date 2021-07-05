# Guia Prático do Pre-Processador SASS

> **Nota:** Este guia assume que você usa [VSCode Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer), [NodeJs](https://nodejs.org/en/) ou algum servidor de teste semelhante.

## Lista de Conteúdos
1. [Instalação](#instalacao)
1. [Extensão](#extensao-file)
1. [Variáveis](#variaveis)
1. [Comandos](#comandos)
1. [Mixins](#mixins)
1. [Aninhameno](#aninhamento)
1. [@import](#import)
1. [Color Functions](#color-functions)
1. [Comnetários](#comentarios)
1. [Extend e Placeholder](#extend-placeholder)

<a id="instalacao"></a>
## 1 - Instalação
- **Primeiro passo,** verifique a versão do Ruby: 

    Linux: ```$ ruby --version```\
    Windows: ```ruby -v```

    > Em caso de problemas, execute a linha abaixo:   
    Instalar Ruby no Linux: ```$ sudo apt-get install ruby-full```\
    Instalar Ruby no Windows: [Download - Ruby Installer](https://rubyinstaller.org/downloads/) 
    
    Em seguida execute o comando de sua  preferência, abaixo.

    - Linux:
    ```$ sudo gem install sass```
    - Node Linux:
    ```$ npm install -g sass```
    - Windows:
    ```choco install sass```
    - Homebrew (Mac OSX):
    ```brew install sass/sass/sass```

<a id="extensao-file"></a>
## 2 - Extensão   
- Os arquivos SASS são compatíveis com a extensão **.scss**.\
  **Exemplo:**
  ```
  style.scss
  header.scss
  main.scss
  ```

<a id="variaveis"></a>
## 3 - Variáveis
- O uso das variáveis é feito pelo sinal de Dólar ```$```. Assim como uma variável em linguagem de programação que armazena um valor e pode ser reutilizado em diversos lugares do código.\
**Exemplo:**

  ```SCSS
  $cor-principal: #7a59e4; 
  $cor-secundaria: #121214;

  header{
    background: $cor-principal;
    color: $cor-secundaria;
  }
  ```

<a id="comandos"></a>
## 4 - Comandos
- Em seu ambiente você precisará executar alguns comandos para facilitar o desenvolvimento. Acesse sua pasta de estilos css e execute:

    ```Shell
    sass nomeDoSeuArquivoScss.scss:nomeDoSeuArquivoCss.css
    ```
    O código acima precisa ser executado via linha de comando para toda e qualquer nova alteração feita no css. O que daria um belo de um trabalho, por isso o Sass proveu um comando chamado **watch** para compilar automaticamente toda vez que seu código é salvo, sem a necessidade de ir toda vez ao terminal e executar o comando. Execute uma única vez:

    ```Shell
    sass watch nomeDoSeuArquivoScss.scss:nomeDoSeuArquivoCss.css
    ```
    Consulte outros comandos na documentação oficial. [Sass Command-Line Interface](https://sass-lang.com/documentation/cli)

<a id="mixins"></a>
## 5 - Mixins
- Inicie criando um Mixin.

  ```SCSS
  @mixin fonte-personalizada{
    font-size: 30px;
    font-weight: 500;
    font-family: sans-serif;
  }
  ```
  Por fim, importe o Mixin dentro da classe desejada da seguinte forma: @include + o nome do Mixin.
  ```SCSS
  .titulo-principal{
    @include fonte-personalizada;
  }
  ```

<a id="aninhamento"></a>
## 6 - Aninhamento
- Talvez, uma das maiores "trabalheiras" do css seja referenciar classe dentro de classe. Tipo:

  ```CSS
    nav .menu-topo li a{}
    header nav ul li a{}
  ```
  Welcome to the **NESTING!!!** 😍\
  Nesting é uma forma de aninhar o código tornando-o mais legível. Veja o código abaixo.

  ```SCSS
    .menu-topo{
      width: 100%;
      display: block;
      
      li{
        background: #eee;

        a{
          text-decoration: none;

          &:hover{
            color: #ff0000;
          }
        }
      }
    }
  ```

Note o uso do ``&``. Ele serve para referenciar o pai dele, no caso **a**.

<a id="import"></a>
## 7 - Import
- Precisa fazer o import de outros arquivos dentro do seu código? Use o import para chamar, porém sem a extensão **.scss**.

```SCSS
  @import "cores";  //cores.scss => cores
  @import "header"; //header.scss => header
  @import "main";   //main.scss => main
  @import "footer"; //footer.scss => footer
```

<a id="color-functions"></a>
## 8 - Color Functions
- Chega de Color Picker, as [Color Functions](https://sass-lang.com/documentation/modules/color) são mão na roda. Aumente ou diminua o brilho de uma cor, passando os segunites parâmetros **Cor** e **Valor**.

  ```SCSS
  color: lighten(#0078d7, 15%);
  color: darken(#990000,	36);
  ```
  Existem muitas outras formas, usos e funções, consulte a documentação oficial.


<a id="comentarios"></a>
## 9 - Comentários
- Evite que comentários do seu código fiquem visíveis a todos com o cometário de linha **//**.

```SCSS
//Comentário não visível na hora de compilar código
$cor-principal: #9db0c4;
```

<a id="extend-placeholder"></a>
## 10 - Extend e Placeholder

```SCSS
  //Criação do Placeholder
  %espacamento-superior{
    margin-top: 20px;
    padding-top: 10px;
  }

  //Uso dentro da classe
  .menu-principal{
    @extend %espacamento;
  }
```