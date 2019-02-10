---
id: add-react-to-a-website
title: Adicione o React a um site
permalink: docs/add-react-to-a-website.html
redirect_from:
  - "docs/add-react-to-an-existing-app.html"
prev: getting-started.html
next: create-a-new-react-app.html
---

Use o React o quanto precisar, sendo pouco ou muito.

React foi projetado desde o início para adoção gradual, e **você pode usar o React o quanto precisar, sendo pouco ou muito**. Talvez você só queira adicionar alguns "pontos de interatividade" a uma página existente. Os componentes React são uma ótima maneira de fazer isso.

A grande maioria dos sites não são, e não precisam ser, single-page apps. Você pode usar o React em uma pequena parte do seu site com **poucas linhas de código e nenhuma ferramenta de build**. Você também pode expandir gradualmente sua presença ou mantê-lo contido em alguns widgets dinâmicos.

---

- [Adicione o React em Um Minuto](#adicione-o-react-em-um-minuto)
- [Opcional: Experimente o React com JSX](#opcional-experimente-o-react-com-jsx) (sem empacotador necessário!)

## Adicione o React em Um Minuto {#adicione-o-react-em-um-minuto}

Nesta seção, mostraremos como adicionar um componente React a uma página HTML existente. Você pode usar seu próprio site ou criar um arquivo HTML vazio para praticar.

Não será necessário usar alguma ferramenta complicada ou instalar algo -- **para completar essa seção, você só precisa de uma conexão de internet e um minuto de seu tempo.**

Opcional: [Faça o download do exemplo completo (2KB zipado)](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605/archive/f6c882b6ae18bde42dcf6fdb751aae93495a2275.zip)

### Passo 1: Adicionar um contêiner DOM ao HTML {#passo-1-adicionar-um-conteiner-dom-ao-html}

Primeiramente, abra a página HTML que você deseja alterar. Adicione uma tag `<div>` vazia para marcar o local onde você deseja exibir algo com o React. Por exemplo:

```html{3}
<!-- ... HTML existente ... -->

<div id="like_button_container"></div>

<!-- ... HTML existente ... -->
```

Nós atribuimos a esta `<div>` um atributo HTML `id` único. Isso nos permitirá encontrá-lo no código JavaScript e mais tarde exibir um componente React dentro dele.

>Dica
>
>Você pode colocar um "contêiner" como este `<div>` em **qualquer lugar** dentro da tag `<body>`. Você pode ter vários contêineres DOM independentes em uma página. Eles geralmente são vazios -- o React vai substituir qualquer conteúdo existente dentro deles.

### Passo 2: Adicionar as Tags Script {#passo-2-adicionar-as-tags-script}

A seguir, adicione três tags `<script>` em sua página HTML logo antes do fechamento da tag `</body>`:

```html{5,6,9}
  <!-- ... HTML qualquer ... -->

  <!-- Adicionar o React. -->
  <!-- Nota: ao fazer o deploy, substitua "development.js" por "production.min.js". -->
  <script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>

  <!-- Adicione nosso componente React. -->
  <script src="like_button.js"></script>

</body>
```

As duas primeiras tags adicionam o React. A terceira irá adicionar o código de seu componente.

### Passo 3: Criar um Componente React {#passo-3-criar-um-componente-react}

Crie um arquivo chamado `like_button.js` próximo a sua página HTML.

Abra **[este código inicial](https://cdn.rawgit.com/gaearon/0b180827c190fe4fd98b4c7f570ea4a8/raw/b9157ce933c79a4559d2aa9ff3372668cce48de7/LikeButton.js)** e copie o conteúdo no arquivo que você criou.

>Dica
>
>Esse código define um componente React chamado `LikeButton`. Não se preocupe se você ainda não entendeu -- mais tarde vamos cobrir os blocos de contrução do React em nosso [tutorial](/tutorial/tutorial.html) e em nosso [guia dos conceitos principais](/docs/hello-world.html). Por enquanto, vamos apenas fazer funcionar!

Depois **[do código inicial](https://cdn.rawgit.com/gaearon/0b180827c190fe4fd98b4c7f570ea4a8/raw/b9157ce933c79a4559d2aa9ff3372668cce48de7/LikeButton.js)**, adicione essas duas linhas no final do arquivo `like_button.js`:

```js{3,4}
// ... o código inicial que você copiou ...

const domContainer = document.querySelector('#like_button_container');
ReactDOM.render(e(LikeButton), domContainer);
```

Essas duas linhas de código encontram a `<div>` que adicionamos em nosso HTML no primeiro passo, e então mostrará o componente React dentro dele.

### E é Isso Aí! {#e-e-isso-ai}

Não existe quarto passo. **Você acabou de adicionar seu primeiro componente React ao seu site.**

Confira nas próximas seções para mais dicas de como integrar o React.

**[Veja o código fonte completo do exemplo](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605)**

**[Faça o download do exemplo completo (2KB zipado)](https://gist.github.com/gaearon/6668a1f6986742109c00a581ce704605/archive/f6c882b6ae18bde42dcf6fdb751aae93495a2275.zip)**

### Dica: Reutilize um Componente {#dica-reutilize-um-componente}

Normalmente, você pode querer exibir seus componentes React em vários lugares em sua página HTML. Aqui está um exemplo que exibe o botão "Like" três vezes e passa alguns dados para ele:

[Veja o código fonte completo do exemplo](https://gist.github.com/gaearon/faa67b76a6c47adbab04f739cba7ceda)

[Faça o download do exemplo completo (2KB zipado)](https://gist.github.com/gaearon/faa67b76a6c47adbab04f739cba7ceda/archive/9d0dd0ee941fea05fd1357502e5aa348abb84c12.zip)

>Nota
>
>Essa estratégia é mais útil quando as partes da página com React estão isoladas uma das outras. Dentro do código do React, é mais fácil de usar [composição de componentes](/docs/components-and-props.html#composing-components).

### Dica: Minifique o JavaScript para Produção {#dica-minifique-o-javascript-para-production}

Antes de realizar o deploy de seu site para produção, lembre-se que o código JavaScript não minificado pode deixar sua página significamente mais lenta para seus usuários.

Se você já minifica os scripts da sua aplicação, **seu site estará pronto para produção** se você garantir que o HTML carregue a versão do React terminando em `production.min.js`:

```js
<script src="https://unpkg.com/react@16/umd/react.production.min.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js" crossorigin></script>
```

Se você não possui uma etapa de minificação para seus scripts, [aqui está um jeito de configurá-lo](https://gist.github.com/gaearon/42a2ffa41b8319948f9be4076286e1f3).

## Opcional: Experimente o React com JSX {#opcional-experimente-o-react-com-jsx}

Nos exemplos acima, nós contamos apenas com recursos que são nativamentes suportados pelos navegadores. E é por isso que usamos uma chamada de função JavaScript para informar ao React o que exibir:

```js
const e = React.createElement;

// Exibe um "Like" <button>
return e(
  'button',
  { onClick: () => this.setState({ liked: true }) },
  'Like'
);
```

Portanto, o React também oferece a opção de usar o [JSX](/docs/introducing-jsx.html) como alternativa:

```js
// Exibe um "Like" <button>
return (
  <button onClick={() => this.setState({ liked: true })}>
    Like
  </button>
);
```

Esses dois blocos de código são equivalentes. Enquanto o **JSX é [completamente opcional](/docs/react-without-jsx.html)**,
These two code snippets are equivalent. While **JSX is [completely optional](/docs/react-without-jsx.html)**, muita pessoas acham útil para escrever código de UI -- junto com React e com outras bibliotecas.

Você pode testar com JSX usando [esse conversor online](http://babeljs.io/repl#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=Q&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&sourceType=module&lineWrap=true&presets=es2015%2Creact%2Cstage-2%2Cstage-3&prettier=true&targets=Node-6.12&version=6.26.0&envVersion=).

### Experimente Rapidamente JSX {#experimente-rapidamente-jsx}

A maneira mais rápida de experimentar o JSX em seu projeto é adicionando essa tag `<script>` em sua página:

```html
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

Agora você pode usar o JSX in qualquer tag `<script>` somente adicionando o atributo `type="text/babel"` a ele. Aqui está [um exemplo de arquivo HTML com JSX](https://raw.githubusercontent.com/reactjs/reactjs.org/master/static/html/single-file-example.html) em que você pode efetuar o download e testar.

Essa abordagem é boa para aprender e criar demostrações simples. Portanto, o site fica lento e **não fica adequado para produção**. Quando você estiver pronto para seguir em frente, remova essa nova tag `<script>` e os atributos `type="text/babel"` que você adicionou. Em vez disso, na seção a seguir você ira configurar um pré-processador JSX para converter todas suas tags `<script>` automaticamente.

### Adicionar JSX a um Projeto {#adicionar-jsx-a-um-projeto}

Adicionar JSX a um projeto não requer ferramentas complicadas, como um empacotador ou um servidor de desenvolvimento. Essencialmente, adicionar JSX **é como adicionar um pré-processador CSS.** O único requisito e possuir o [Node.js](https://nodejs.org/) instalado em seu computador.

No terminal, vá para a pasta do seu projeto e cole esses dois comandos:

1. **Passo 1:** Execute `npm init -y` (se falhar, [aqui está uma correção](https://gist.github.com/gaearon/246f6380610e262f8a648e3e51cad40d))
2. **Passo 2:** Execute `npm install babel-cli@6 babel-preset-react-app@3`

>Dica
>
>Estamos **usando npm aqui somente para instalar o pré-processador do JSX;** você não precisará dele para mais nada. Tanto o React quanto o código da aplicação pode continuar sem mudanças nas tags `<script>`.

Parabéns! Você acabou de adicionar uma **configuração JSX pronta para produção** em seu projeto.


### Executar o Pré-processador JSX {#executar-o-pre-processador-jsx}

Crie uma pasta chamada `src` e execute no terminal esse comando:

```
npx babel --watch src --out-dir . --presets react-app/prod
```

>Nota
>
>`npx` não é um erro de digitação -- é um [é uma ferramenta de executar pacotes que vem com npm 5.2+](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b).
>
>Se você ver uma mensagem de erro dizendo "You have mistakenly installed the `babel` package", você pode ter perdido [o passo anterior](#adicionar-jsx-a-um-projeto). Execute o passo anterior na mesma pasta e tente novamente.

Não espere o comando finalizar -- esse comando inicia um watcher automatizado para o JSX.

Se você criar um arquivo chamado `src/like_button.js` com esse **[este código JSX inicial](https://cdn.rawgit.com/gaearon/c8e112dc74ac44aac4f673f2c39d19d1/raw/09b951c86c1bf1116af741fa4664511f2f179f0a/like_button.js)**, o watcher criará um `like_button.js` pré-processado com o código JavaScript adequado para o navegador. Quando você edita o arquivo com JSX, a transformação será executada automaticamente.

De bônus, isso também permite que você use recursos modernos do JavaScript, como classes, sem se preocupar com a incompatibilidade de navegadores antigos. A ferramenta que acabamos de usar é chamada de Babel, e você pode aprender mais sobre ele [em sua documentação](http://babeljs.io/docs/en/babel-cli/).

Se você se sentir confortavel com ferramentas de build e deseja que eles façam mais por você, [a próxima seção](/docs/create-a-new-react-app.html) descreve alguma das mais populares e acessíveis ferramentas. Caso contrário, essas tags scripts irão funcionar perfeitamente.
