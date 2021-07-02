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
1. [Extends e Placeholder](#extends-placeholder)

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
  ```
  $cor-principal: #7a59e4; 
  $cor-secundaria: #121214;

  header{
    background: $cor-principal;
    color: #cor-secundaria;
  }```
  

<a id="comandos"></a>
## 4 - Comandos
- Em seu ambiente você precisará executar alguns comandos para facilitar o desenvolvimento. Acesse sua pasta de estilos css e execute:
    ```
    sass nomeDoSeuArquivoScss.scss:nomeDoSeuArquivoCss.css
    ```
    O código acima precisa ser executado via linha de comando para toda e qualquer nova alteração feita no css. O que daria um belo de um trabalho, por isso o Sass proveu um comando chamado **watch** para compilar automaticamente toda vez que seu código é salvo, sem a necessidade de ir toda vez ao terminal e executar o comando. Execute uma única vez:
    ```
    sass watch nomeDoSeuArquivoScss.scss:nomeDoSeuArquivoCss.css
    ```
    Consulte outros comandos na documentação oficial. [Sass Command-Line Interface](https://sass-lang.com/documentation/cli)

<a id="mixins"></a>
## 5 - Mixins