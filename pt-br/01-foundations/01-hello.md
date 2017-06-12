# Olá, Mundo!

## Instalação do Elm

Vá para http://elm-lang.org/install e baixe o instalador apropriado para o seu sistema.

## Nossa Primeira Aplicação em Elm

Vamos escrever nossa primeira aplicação em Elm. Crie uma pasta para sua aplicação. Nesta pasta execute o seguinte comando no terminal:

```bash
elm package install elm-lang/html
```

Isto vai lhe informar que é necessário instalar pacotes adicionados, qual é o plano de upgrade proposto e pede para você confirmar este plano.
Se a sua versão do Elm for 0.18.0, o plano de upgrade vai incluir os pacotes elm-lang/core, elm-lang/html e elm-lang/virtual-dom.

A instalação vai criar um arquivo _elm-package.json_ e uma pasta _elm-stuff_ no diretório do seu projeto e então instalar os módulos especificados no plano de upgrade. Seus módulos ficam dentro da pasta _elm-stuff_, enquanto que suas especificações ficam salvas no arquivo _elm-package.json_.

Agora crie um arquivo `Hello.elm` com o seguinte código:

```elm
module Hello exposing (..)

import Html exposing (text)


main =
    text "Olá Mundo!"
```

Pelo terminal, vá para a pasta de seu projeto e execute o comando:

```bash
elm reactor
```

A seguinte mensagem deve aparecer:

```
elm reactor 0.18.0
Listening on http://localhost:8000/
```

Abra o caminho `http://localhost:8000/` no seu navegador e clique no arquivo `Hello.elm`. Então a mensagem `Olá, Mundo!` deve ser exibida no seu navegador.

Note que você pode ver um alerta sobre uma _missing type annotation_ ("Anotação de tipo ausente") para `main`. Por enquanto ignore este alerta, vamos falar sobre anotações mais tarde.

Vamos ver o que acontece dentro do arquivo:

### Declaração do Módulo

```
module Hello exposing (..)
```

Todo módulo em Elm deve começar com uma declaração de módulo. Neste caso o nome do módulo é chamado `Hello`. A comunidade Elm possui a convenção de colocar o mesmo nome para o arquivo e módulo. Desta forma, o arquivo `Hello.elm` contém o módulo ` module Hello`.

A parte `exposing (..)` especifica quais funções e tipos do módulo são expostos para outros módulos que venham a importar este arquivo no futuro. Neste caso, expomos tudo com `(..)`.

### Imports

```
import Html exposing (text)
```

Em Elm você precisa declarar os __módulos__ a serem importados explicitamente. Neste caso queremos o módulo __Html__. 

Este módulo oferece diversas funções para se trabalhar com HTML. Neste exemplo usamos a função `.text`, por isso a declaramos para o namespace atual com `exposing`.

### Main

```
main =
    text "Hello"
```

Aplicações de Front-End feitas em Elm iniciam em uma função chamada `main`. `main` é um afunção que retorna um elemento a ser renderizado no navegador. Neste caso ela retorna um elemento Html (criado através da função `text`).

### Elm reactor

O Elm __reactor__ cria um servidor que compila os arquivos Elm sob demanda no momento da exibição. O __reactor__ é útil para o desenvolvimento de aplicaçes sem se preocupar com a configuração de um processo de build. Porém o __reactor__ possui limitações, o que nos vai levar a adotar um processo de build diferente no futuro.