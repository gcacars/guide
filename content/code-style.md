---
title: Estilo de codificação
order: 1
description: Orientações de estilo sugeridas para seu código.
discourseTopicId: 20189
---

Depois de ler este artigo, você saberá:
1. Por que é uma boa ideia ter um estilo consistente de codificação.
2. Qual o guia de estilo que nós recomendamos para código JavaScript
3. Como configurar o ESLint para checar seu estilo de codificação automaticamente.
4. Sugestões de estilos para padrões específicos do Meteor, como Métodos, publicações, e mais.

<h2 id="benefits-style">Benefícios de um estilo consistente de codificação</h2>

Horas incontáveis foram perdidas por desenvolvedores ao longo dos anos argumentando sobre aspas duplas vs. aspas simples, quando colocar colchetes, quantos espaços colocar, e todos os tipos de outras questões cosméticas de estilo. Todas essas são questões que têm na melhor das hipóteses uma relação tangencial à qualidade do código, mas são muito fáceis de haverem opiniões diferentes pois são muito visuais.

Enquanto não é necessariamente importante se seu código usa aspas simples ou dupla para strings literais, há enormes benefícios de se fazer a decisão uma vez e ter isso consistente através de toda sua organização. Os benefícios também sem aplicam às comunidades de desenvolvimento Meteor e Javascript como um todo.

<h3 id="easy-to-read">Código fácil de ler</h3>

Da mesma maneira que você não lê uma palavra por vez em sentenças em português, você não lê o código por um marcador de cada vez. A maioria apenas olha a forma de uma certa expressão, ou o jeito que ela brilha no seu editor, e entende o que faz. Se o estilo de cada pedaço do código é consistente, isso garante que os pedaços de código que se parecem os mesmos _são_ os mesmos - não há nenhum pontuação oculta ou pegadinhas que você não espera, indentação não é significativo, mas é útil para se ter todo seu código consistentemente indentado assim você não terá que ler todos os colchetes em detalhes para ver o que está acontecendo.

```js
// Este código engana porque eles parecem estar
// dentro da mesma condição
if (condicao)
  primeiraDeclaracao();
  segundaDeclaracao();
```

```js
// Bem melhor!
if (condicao) {
  primeiraDeclaracao();
}

segundaDeclaracao();
```

<h3 id="automatic-error-checking">Checagem de erro automática</h3>

Ter um estilo consistente significa que é fácil adotar ferramentas padrões para checar os erros. Por exemplo, se você adotar uma convenção de que você sempre deve usar `let` ou `const` ao invés de `var`, pode usar agora uma ferramenta para ter certeza que todas as variáveis estão da maneira esperada. Isso significa que você pode evitar erros onde as variáveis atuam de forma inesperada. E também, por forçar que todas as variáveis estejam declaradas antes de usar, você pode facilmente pegar erros de digitação antes mesmo de executar qualquer código!

<h3 id="deeper-understanding">Compreensão profunda</h3>

É difícil de aprender tudo sobre uma linguagem de programação de uma só vez. Por exemplo, programadores novatos no JavaScript tem uma guerra com a palavra `var` e o escopo da função. Usando um estilo de codificação recomendado pela comunidade com validação automática, pode avisá-lo sobre essas armadilhas de forma proativa. Quer dizer que você pode pular direto para a codificação sem aprender tudo antes do tempo sobre os detalhes do JavaScript.

Conforme você escreve mais código e em cima das regras de estilo recomendadas, você pode tomar isso como uma oportunidade para aprender mais sobre a sua linguagem de programação e como diferentes pessoas preferem usá-la.

<h2 id="javascript">Guia de estilos JavaScript</h2>

Aqui no Meteor, nós acreditamos fortemente que o JavaScript é a melhor linguagem para construir aplicações web, por várias razões. JavaScript está em constante aperfeiçoamento, e os padrões em torno do ES2015 realmente reuniu a comunidade JavaScript. Aqui vão nossas recomendações para usar hoje o JavaScript ES2015 no seu aplicativo.

![](images/ben-es2015-demo.gif)

> Exemplo de código refeito do JavaScript para o ES2015

<h3 id="ecmascript">Use o pacote `ecmascript`</h3>

ECMAScript, a linguagem padrão que todo navegador se baseia para implementar o JavaScript, mudou para lançamentos anuais de padrões. O padrão completo mais novo é o ES2015, que inclui algumas melhorias muito aguardadas e significativas para a linguagem JavaScript. O pacote `ecmascript` do Meteor compila esse padrão para o JavaScript regular que todos os navegadores possam entender, usando o [popular compilador Babel (em inglês)](https://babeljs.io/). É totalmente compatível com código "regular" do JavaScript, logo você não precisa usar nenhuma nova funcionalidade se não quiser. Colocamos muitos esforços em fazer funcionalidades avançadas do navegador como mapeamento do fonte trabalhar bem com esse pacote, assim você pode depurar o código usando suas ferramentas de desenvolvimento favoritas sem ter que ver alguma saída compilada.

O pacote `ecmascript` é incluído em todos novos aplicativos e pacotes por padrão, e compila todos arquivos com a extensão `.js` automaticamente. Veja a [lista de todas as funcionalidades suportadas pelo pacote ecmascript (em inglês)](https://docs.meteor.com/packages/ecmascript.html#Supported-ES2015-Features).

Para ter uma experiência completa, você também pode usar o pacote `es5-shim` que é incluído em todos os novos aplicativos por padrão. Isso quer dizer que você pode usar funcionalidade de execução como `Array#forEach` sem se preocupar quais navegadores suportam isso.

Todos os códigos de exemplo nesse guia e em futuros tutoriais do Meteor usuarão todas as novas funcionalidades do ES2015. Você pode ler mais sobre o ES2015 e como começar em nosso Blog do Meteor:

- [Começando com Meteor e ES2015 (em inglês)](http://info.meteor.com/blog/es2015-get-started)
- [Configurar o Sublime Text para o  ES2015 (em inglês)](http://info.meteor.com/blog/set-up-sublime-text-for-meteor-es6-es2015-and-jsx-syntax-and-linting)
- [Quanto custa o ES2015? (em inglês)](http://info.meteor.com/blog/how-much-does-es2015-cost)

<h3 id="style-guide">Siga um guia de estilo JavaScript</h3>

Recomendamos escolher e aderir a um guia de estilos JavaScript e aplicá-la com as ferramentas. Uma opção popular que recomendamos é o [Guia de estilos do Airbnb (em inglês)](https://github.com/airbnb/javascript) com as extensões do ES6 (e opcionalmente as extensões para o React). Uma versão do guia para o JavaScript anterior ao ES2015 está [disponível em português](https://github.com/armoucar/javascript-style-guide).

<h2 id="eslint">Verifique seu código com ESLint</h2>

"Code linting" (em inglês) é o processo de automaticamente verificar seu código por erros comuns ou problemas de estilo. Por exemplo, ESLint pode determinar se você cometeu um erro de digitação no nome de uma variável, ou alguma parte do seu código está inacessível por culpa de um `if` mal escrito.

Recomendamos usar a [configuração ESLint do Airbnb (em inglês)](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb) que verifica o guia de estilos do  Airbnb.

Abaixo, você pode encontrar instruções para configurar um linting automático em muitos estágios diferentes de desenvolvimento. Em geral, você deseja executar o linter o mais rápido possível, porque é a maneira mais rápida e mais fácil de identificar a digitação e pequenos erros.

<h3 id="eslint-installing">Instalando e executando o ESLint</h3>

Para configurar o ESLint na sua aplicação, você pode instalar os seguintes pacotes [npm](https://docs.npmjs.com/getting-started/what-is-npm):

```
meteor npm install --save-dev eslint-config-airbnb eslint-plugin-import eslint-plugin-meteor eslint-plugin-react eslint-plugin-jsx-a11y eslint
```

> Meteor vem com um npm junto, logo você pode digitar meteor npm sem se preocupar em instalá-lo. Se você desejar, você ainda pode usar a instalação global do comando npm.

Você pode adicionar ainda uma seção `eslintConfig` no seu `package.json` para especificar que você gostaria de usar a configuração do Airbnb, e para ativar o [ESLint-plugin-Meteor](https://github.com/dferber90/eslint-plugin-meteor). E ainda pode configurar qualquer regra adicional que você quiser alterar, como também adicionar um comando lint ao npm:

```
{
  ...
  "scripts": {
    "lint": "eslint .",
    "pretest": "npm run lint --silent"
  },
  "eslintConfig": {
    "plugins": [
      "meteor"
    ],
    "extends": [
      "airbnb",
      "plugin:meteor/recommended"
    ],
    "rules": {}
  }
}
```

Para executar o linter, você pode simplesmente digitar:

```bash
meteor npm run lint
```

Se você tiver erros do comando `meteor create meuapp` como:

```bash
/opt/www/sites/me/myapp/client/main.js
   1:26  error  Unable to resolve path to module 'meteor/templating'    import/no-unresolved
   2:29  error  Unable to resolve path to module 'meteor/reactive-var'  import/no-unresolved
  18:25  error  Invalid parameter name, use "templateInstance" instead  meteor/eventmap-params

/opt/www/sites/me/myapp/server/main.js
  1:24  error  Unable to resolve path to module 'meteor/meteor'  import/no-unresolved
```

então você pode silenciá-los adicionando à `rules` (regras) no `eslintConfig`, por exemplo:

```
{
  ...
  "eslintConfig": {
   ...
    "rules": {
      "meteor/eventmap-params": [
        2, { "templateInstanceParamName": "instance" }
      ],
      "import/no-unresolved": [
        2, { "ignore": ["^meteor/"] }
      ]
    }
  }
}
```


Para mais detalhes, leia as direções do [Começando (em inglês)](http://eslint.org/docs/user-guide/getting-started) do site do ESLint.

<h3 id="eslint-editor">Integrando com seu editor</h3>

Linting is the fastest way to find potential bugs in your code. Running a linter is usually faster than running your app or your unit tests, so it's a good idea to run it all the time. Setting up linting in your editor can seem annoying at first since it will complain often when you save poorly-formatted code, but over time you'll develop the muscle memory to just write well-formatted code in the first place. Here are some directions for setting up ESLint in different editors:


<h4 id="eslint-sublime">Sublime Text</h4>

You can install the Sublime Text packages that integrate them into the text editor. It's generally recommended to use Package Control to add these packages. If you already have that setup, you can just add the these packages by name; if not, click the instructions links:

* Babel (for syntax highlighting – [full instructions](https://github.com/babel/babel-sublime#installation))
* SublimeLinter ([full instructions](http://sublimelinter.readthedocs.org/en/latest/installation.html))
* SublimeLinter-contrib-eslint ([full instructions](https://github.com/roadhump/SublimeLinter-eslint#plugin-installation))

To get proper syntax highlighting, go to a .js file, then select the following through the *View* dropdown menu: *Syntax* -> *Open all with current extension as...* -> *Babel* -> *JavaScript (Babel)*. If you are using React .jsx files, do the same from a .jsx file. If it's working, you will see "JavaScript (Babel)" in the lower right hand corner of the window when you are on one of these files. Refer to the [package readme](https://github.com/babel/babel-sublime) for information on compatible color schemes.

A side note for Emmet users: You can use *\<ctrl-e\>* to expand HTML tags in .jsx files, and it will correctly expand classes to React's "className" property. You can bind to the tab key for this, but [you may not want to](https://github.com/sergeche/emmet-sublime/issues/548).

<h4 id="eslint-atom">Atom</h4>

Using ESLint with Atom is simple. Just install these three packages:

```bash
apm install language-babel
apm install linter
apm install linter-eslint
```

Then **restart** (or **reload** by pressing Ctrl+Alt+R / Cmd+Opt+R) Atom to activate linting.


<h4 id="eslint-webstorm">WebStorm</h4>

WebStorm provides [these instructions for using ESLint](https://www.jetbrains.com/webstorm/help/eslint.html). After you install the ESLint Node packages and set up your `package.json`, just enable ESLint and click "Apply". You can configure how WebStorm should find your `.eslintrc` file, but on my machine it worked without any changes. It also automatically suggested switching to "JSX Harmony" syntax highlighting.

![Enable ESLint here.](images/webstorm-configuration.png)

Linting can be activated on WebStorm on a project-by-project basis, or you can set ESLint as a default under Editor > Inspections, choosing the Default profile, checking "ESLint", and applying.

<h4 id="eslint-vscode">Visual Studio Code</h4>

Using ESLint in VS Code requires installation of the 3rd party [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) extension.  In order to install the extension, follow these steps:

1. Launch VS Code and open the quick open menu by typing `Ctrl+P`
2. Paste `ext install vscode-eslint` in the command window and press `Enter`
3. Restart VS Code


<h2 id="meteor-features">Meteor code style</h2>

The section above talked about JavaScript code in general - you can easily apply it in any JavaScript application, not just with Meteor apps. However, there are some style questions that are Meteor-specific, in particular how to name and structure all of the different components of your app.

<h3 id="collections">Collections</h3>

Collections should be named as a plural noun, in [PascalCase](https://en.wikipedia.org/wiki/PascalCase). The name of the collection in the database (the first argument to the collection constructor) should be the same as the name of the JavaScript symbol.

```js
// Defining a collection
Lists = new Mongo.Collection('Lists');
```

Fields in the database should be camelCased just like your JavaScript variable names.

```js
// Inserting a document with camelCased field names
Widgets.insert({
  myFieldName: 'Hello, world!',
  otherFieldName: 'Goodbye.'
});
```

<h3 id="methods-and-publications">Methods and publications</h3>

Method and publication names should be camelCased, and namespaced to the module they are in:

```js
// in imports/api/todos/methods.js
updateText = new ValidatedMethod({
  name: 'todos.updateText',
  // ...
});
```

Note that this code sample uses the [ValidatedMethod package recommended in the Methods article](methods.html#validated-method). If you aren't using that package, you can use the name as the property passed to `Meteor.methods`.

Here's how this naming convention looks when applied to a publication:

```js
// Naming a publication
Meteor.publish('lists.public', function listsPublic() {
  // ...
});
```

<h3 id="files-and-exports">Files, exports, and packages</h3>

You should use the ES2015 `import` and `export` features to manage your code. This will let you better understand the dependencies between different parts of your code, and it will be easy to know where to look if you need to read the source code of a dependency.

Each file in your app should represent one logical module. Avoid having catch-all utility modules that export a variety of unrelated functions and symbols. Often, this can mean that it's good to have one class, UI component, or collection per file, but there are cases where it is OK to make an exception, for example if you have a UI component with a small sub-component that isn't used outside of that file.

When a file represents a single class or UI component, the file should be named the same as the thing it defines, with the same capitalization. So if you have a file that exports a class:

```js
export default class ClickCounter { ... }
```

This class should be defined inside a file called `ClickCounter.js`. When you import it, it'll look like this:

```js
import ClickCounter from './ClickCounter.js';
```

Note that imports use relative paths, and include the file extension at the end of the file name.

For [Atmosphere packages](using-packages.html), as the older pre-1.3 `api.export` syntax allowed more than one export per package, you'll tend to see non-default exports used for symbols. For instance:

```js
// You'll need to destructure here, as Meteor could export more symbols
import { Meteor } from 'meteor/meteor';

// This will not work
import Meteor from 'meteor/meteor';
```

<h3 id="templates-and-components">Templates and components</h3>

Since Spacebars templates are always global, can't be imported and exported as modules, and need to have names that are completely unique across the whole app, we recommend naming your Blaze templates with the full path to the namespace, separated by underscores. Underscores are a great choice in this case because then you can easily type the name of the template as one symbol in JavaScript.

```html
<template name="Lists_show">
  ...
</template>
```

If this template is a "smart" component that loads server data and accesses the router, append `_page` to the name:

```html
<template name="Lists_show_page">
  ...
</template>
```

Often when you are dealing with templates or UI components, you'll have several closely coupled files to manage. They could be two or more of HTML, CSS, and JavaScript files. In this case, we recommend putting these together in the same directory with the same name:

```
# The Lists_show template from the Todos example app has 3 files:
show.html
show.js
show.less
```

The whole directory or path should indicate that these templates are related to the `Lists` module, so it's not necessary to reproduce that information in the file name. Read more about directory structure [above](structure.html#javascript-structure).

If you are writing your UI in React, you don't need to use the underscore-split names because you can import and export your components using the JavaScript module system.
