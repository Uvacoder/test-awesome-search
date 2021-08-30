![light bulb icon](https://rawgit.com/AllThingsSmitty/css-protips/master/media/logo.svg)

CSS Protips [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
=======================================================================================================================================================================

Uma coleção de dicas para aumentar as tuas habilidades no CSS.

> Dá uma olhada em outras [listas fantásticas](https://github.com/sindresorhus/awesome/) mantidas por <span class="citation" data-cites="sindresorhus">\[@sindresorhus\]</span>(https://github.com/sindresorhus/).

Índice
------

-   [Protips](#protips)
-   [Suporte](#suporte)
-   [Contribuições](../../CONTRIBUTING.md)

Protips
-------

1.  [Usa um Reset CSS](#usa-um-reset-css)
2.  [Herda o `box-sizing`](#herda-o-box-sizing)
3.  [Use `unset` em vez de redefinir todas as propriedades](#use-unset-em-vez-de-redefinir-todas-as-propriedades)
4.  [Usa `:not()` para Aplicar/Remover Bordas](#usa-not-para-aplicarremover-bordas)
5.  [Verifique se a fonte está instalada localmente](#verifique-se-a-fonte-está-instalada-localmente)
6.  [Define o `line-height` no `body`](#define-o-line-height-no-body)
7.  [Alinha Elementos Verticalmente](#alinha-elementos-verticalmente)
8.  [Definir `:focus` para elementos de formulário](#definir-focus-para-elementos-de-formulário)
9.  [Listas Separadas por Vírgula](#listas-separadas-por-vírgula)
10. [Seleciona Itens Usando `nth-child` Negativo](#seleciona-itens-usando-nth-child-negativo)
11. [Ícones SVG](#Ícones-svg)
12. [Usa o Seletor “Lobotomized Owl”](#usa-o-seletor-lobotomized-owl)
13. [Sliders em CSS com `max-height`](#sliders-em-css-com-max-height)
14. [Tabelas com Células de Tamanho Igual](#tabelas-com-células-de-tamanho-igual)
15. [Esquece as “Margin Hacks”, use Flexbox](#esquece-as-margin-hacks-usa-a-flexbox)
16. [Usa Seletores de Atributo em Links Vazios](#usa-seletores-de-atributo-em-links-vazios)
17. [Estiliza Links “Default”](#estiliza-links-default)
18. [Div com Proporção de Tela Fixa](#div-com-proporção-de-tela-fixa)
19. [Estiliza Imagens Quebradas](#estiliza-imagens-quebradas)
20. [Usa `rem` para Definir Tamanhos Globais; Usa `em` para Definir Tamanhos Locais](#usa-rem-para-definir-tamanhos-globais-usa-em-para-definir-tamanhos-locais)
21. [Esconde Vídeos em Autoplay Que Não Estejam no modo Mudo](#esconde-vídeos-em-autoplay-que-não-estejam-no-mudo)
22. [Usa `:root` para uma Tipografia Flexível](#usa-root-para-uma-typografia-flexível)
23. [Defina `font-size` em Elementos de Formulário para uma Melhor Experiência Mobile](#defina-font-size-em-elementos-de-formulário-para-uma-melhor-experiência-mobile)
24. [Use eventos de ponteiro para controlar eventos do mouse](#use-eventos-de-ponteiro-para-controlar-eventos-do-mouse)
25. [Definir `display: none` em quebras de linha usadas como espaçamento](#definir-display-none-em-quebras-de-linha-usadas-como-espaçamento)

### Usa um Reset CSS

Reiniciar o CSS vai ajudar te a manter a consistência de estilo em diferentes navegadores com um ponto de partida limpo para elementos de estilo. Tu podes usar a biblioteca de reset CSS como [Normalize](http://necolas.github.io/normalize.css/), ou se preferires,adota uma abordagem mais simplificada.:

    *,
    *::before,
    *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

Agora os elementos estão sem margens, preenchimento e `box-sizing`.Permitindo-te gerir o layout com o teu CSS.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/kkrkLL)

**Nota:** Se tu seguires o guia [Herda o box-sizing](#herde-o-box-sizing) abaixo, podes optar por não incluir a propriedade `box-sizing` na tua redefinição de CSS.

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Herda o `box-sizing`

Faz com que o `box-sizing` seja herdado do `html`:

    html {
      box-sizing: border-box;
    }

    *,
    *::before,
    *::after {
      box-sizing: inherit;
    }

Assim fica mais fácil de alterar o `box-sizing` em plugins ou outros componentes que tenham um comportamento diferente.

#### [Passeata](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Use `unset` em vez de redefinir todas as propriedades

Ao redefinir as propriedades de um elemento, não é necessário redefinir cada propriedade individual:

    button {
      background: none;
      border: none;
      color: inherit;
      font: inherit;
      outline: none;
      padding: 0;
    }

Você pode especificar todas as propriedades de um elemento usando a abreviação `all`. Definir o valor como `unset` altera as propriedades de um elemento para seus valores iniciais:

    button {
      all: unset;
    }

**Nota:** a abreviação `all` e`unset` não é compatível com o IE11.

<sup>[voltar\ ao\ índice](#Índice)</sup>

### Usa `:not()` para Aplicar/Retirar Bordas

Ao invés de colocar a borda…

    /* adiciona a borda */
    .nav li {
      border-right: 1px solid #666;
    }

…para então retirar o último elemento…

    /* retira a borda */
    .nav li:last-child {
      border-right: none;
    }

…utiliza a *pseudo-class* `:not()` para aplicar a borda apenas nos elementos corretos:

    .nav li:not(:last-child) {
      border-right: 1px solid #666;
    }

O seletor CSS define a borda da maneira que um humano a descreveria.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/LkymvO)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Verifique se a fonte está instalada localmente

Você pode verificar se uma fonte está instalada localmente antes de buscá-la remotamente, o que também é uma boa dica de desempenho.

    @font-face {
      font-family: "Dank Mono";
      src:
        /* Full name */
        local("Dank Mono"),
        /* Postscript name */
        local("Dank Mono"),
        /* Otherwise, download it! */
        url("//...a.server/fonts/DankMono.woff");
    }

    code {
      font-family: "Dank Mono", system-ui-monospace;
    }

Dica de chapéu para Adam Argyle por compartilhar este protip e [exemplo](https://codepen.io/argyleink/pen/VwYJpgR).

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Define o `line-height` no `body`

Não precisas de adicionar o `line-height` para cada `<p>`, `<h*>`, *et al*. separadamente. Apenas adiciona ao `body`:

    body {
      line-height: 1.5;
    }

Desta forma elementos de texto vão herdar o `line-height` do `body`.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/VjbdYd)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Definir `:focus` para elementos de formulário

Os usuários de teclado com visão dependem do foco para determinar onde os eventos de teclado vão na página. Faça com que os elementos do formulário se foquem e sejam consistentes com a implementação padrão do navegador:

    a:focus,
    button:focus,
    input:focus,
    select:focus,
    textarea:focus {
      box-shadow: none;
      outline: #000 dotted 2px;
      outline-offset: .05em;
    }

#### [Passeata](https://codepen.io/AllThingsSmitty/pen/ePzoOP/)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Alinha Elementos Verticalmente

Que bruxaria é essa? Não é bruxaria!Tu realmente podes centralizar elementos verticalmente:

    html,
    body {
      height: 100%;
      margin: 0;
    }

    body {
      -webkit-align-items: center;
      -ms-flex-align: center;
      align-items: center;
      display: -webkit-flex;
      display: flex;
    }

…e também com CSS Grid:

    body {
      display: grid;
      height: 100vh;
      margin: 0;
      place-items: center center;
    }

Isto não resolveu o teu problema? O site CSS-Tricks tem [um guia completo](https://css-tricks.com/centering-css-complete-guide/) em como centralizar elementos com CSS.

**Aviso:** Fica atento aos [bugs](https://github.com/philipwalton/flexbugs#3-min-height-on-a-flex-container-wont-apply-to-its-flex-items) quando estás a utilizar a flexbox no IE11.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/GqmGqZ)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Listas Separadas por Vírgula

Transforma listas normais em listas separadas por vírgula:

    ul > li:not(:last-child)::after {
      content: ",";
    }

Utilize a *pseudo-class* `:not()` para evitar que a vírgula seja adicionada depois do último item.

**Aviso:** Tendo em conta acessibilidade esta dica pode não ser ideal, especialmente para utilizadores de leitores de tela. Além disso, copiar e/ou colar não funciona em conteúdo criado com CSS. Procede com cautela.

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Seleciona Itens Usando `nth-child` Negativo

Utilize `nth-child` negativo no CSS para selecionar itens de 1 a n.

    li {
      display: none;
    }

    /* mostrar itens de 1 a 3 */
    li:nth-child(-n+3) {
      display: block;
    }

Já que aprendeste um bocadinho sobre como usar a *pseudo-class* [using `:not()`](#use-not-to-applyunapply-borders-on-navigation), agora podes tentar:

    /* seleciona todos os itens, exceto o primeiro 3 e exibe-os */
    li:not(:nth-child(-n+3)) {
      display: none;
    }

Mais fácil que isto não há.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/WxjKZp)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Ícones SVG

Não há motivo nenhum para não usares ícones em SVG:

    .logo {
      background: url("logo.svg");
    }

A vantagem da SVG é que o ícone fica bom em qualquer resolução, além de ter suporte amplo em todos os browsers [desde o IE9](http://caniuse.com/#search=svg). Agora podes desfazer-te dos teus arquivos .png, .jpg, ou ainda .gif-jif-qissomano.

**Aviso:** Se tens botões feitos apenas com ícones SVG, a dica a seguir ajudará-te a manter a acessibilidade:

    .no-svg .icon-only::after {
      content: attr(aria-label);
    }

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Usa o Seletor “Lobotomized Owl”

O nome é super estranho (traduzido literalmente para:“coruja lobotomizada”), mas o seu uso do seletor universal (`*`) com o seletor adjacente (`+`) pode ser muito útil:

    * + * {
      margin-top: 1.5em;
    }

Neste exemplo, todos os elementos acompanhados de outros elementos recebem `margin-top: 1.5em`.

Para mais exemplos utilizando o seletor “lobotomized owl”, lê [o artigo escrito por Heydon Pickering](http://alistapart.com/article/axiomatic-css-and-lobotomized-owls) no site *A List Apart*.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/grRvWq)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Sliders em CSS com `max-height`

Cria *sliders* usando apenas CSS com `max-height` e `overflow-y: hidden`:

    .slider {
      max-height: 200px;
      overflow-y: hidden;
      width: 300px;
    }

    .slider:hover {
      max-height: 600px;
      overflow-y: scroll;
    }

O elemento expandirá-se ao valor definido no `max-height` no *hover* e terás um *slider* devido ao uso do overflow.

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Tabelas com Células de Tamanho Igual

Não há nada mais chato do que trabalhar com tabelas, mas agora podes usar `table-layout: fixed` para manter as células do mesmo tamanho:

    .calendar {
      table-layout: fixed;
    }

Tabelas sem dores de cabeça.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/jALALm)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Esquece as “Margin Hacks”, usa a Flexbox

Quando definires o espaçamento entre as colunas,deixa os seletores `nth-`, `first-`, e `last-child` de lado e usa a propriedade `space-between` do flexbox:

    .list {
      display: flex;
      justify-content: space-between;
    }

    .list .person {
      flex-basis: 23%;
    }

Assim as colunas ficam espaçadas uniformemente.

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Usa Seletores de Atributo em Links Vazios

Mostra links para `<a>` tags vazias que possuem o atributo `href`:

    a[href^="http"]:empty::before {
      content: attr(href);
    }

Mão na roda.

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/zBzXRx)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Estiliza Links “Default”

Define estilos para links “default”:

    a[href]:not([class]) {
      color: #008000;
      text-decoration: underline;
    }

Desta forma, links que foram inseridos por CMS – que normalmente não possuem o atributo `class` – vão ser estilizados sem comprometer outros links.

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Div com Proporção de Tela Fixa

Para criar uma div com proporção de tela fixa, tudo que você precisa fazer é adicionar `padding` (`top` ou `bottom`) a div pai:

    .container {
      height: 0;
      padding-bottom: 20%;
      position: relative;
    }

    .container div {
      border: 2px dashed #ddd;
      height: 100%;
      left: 0;
      position: absolute;
      top: 0;
      width: 100%;
    }

Se usares 20% no `padding` a altura da div vai ser igual a 20% de sua largura. Independente da largura do *viewport*, a div filho vai sempre manter a proporção de tela (100% / 20% = 5:1).

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/jALZvE)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Estiliza Imagens Quebradas

Faz com que imagens quebradas fiquem esteticamente mais agradáveis com um pouquinho de CSS:

    img {
      display: block;
      font-family: sans-serif;
      font-weight: 300;
      height: auto;
      line-height: 2;
      position: relative;
      text-align: center;
      width: 100%;
    }

Agora adiciona regras com *pseudo-elements* para mostrar uma mensagem e a URL da imagem quebrada:

    img::before {
      content: "Desculpe, a imagem abaixo não pode ser carregada :(";
      display: block;
      margin-bottom: 10px;
    }

    img::after {
      content: "(url: " attr(src) ")";
      display: block;
      font-size: 12px;
    }

Lê mais um pouco sobre como estilizar imagens quebradas no [artigo original](http://bitsofco.de/styling-broken-images/) por [Ire Aderinokun](https://github.com/ireade/).

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Usa `rem` para Definir Tamanhos Globais; Usa `em` para Definir Tamanhos Locais

Depois de definires o tamanho de fonte base na raíz (`html { font-size: 100%; }`), define o tamanho de fonte para elementos de texto utilizando `em`:

    h2 {
      font-size: 2em;
    }

    p {
      font-size: 1em;
    }

Então define o tamanho da fonte de módulos utilizando `rem`:

    article {
      font-size: 1.25rem;
    }

    aside .module {
      font-size: .9rem;
    }

Assim fica mais fácil de estilizar e manter cada módulo, além de ser flexível.

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Esconde Vídeos em Autoplay Que Não Estejam no Mudo

Ótima dica para uma *stylesheet* personalizada. Evita sobrecarregar o utilizador com sons de vídeos em autoplay. Se o som não estiver no mudo, esconde o vídeo:

    video[autoplay]:not([muted]) {
      display: none;
    }

E aqui está mais uma entre as muitas vantagens de usar a *pseudo-class* [`:not()`](#use-not-to-applyunapply-borders-on-navigation).

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Usa `:root` para uma Typografia Flexível

O tamanho de fonte de um site *responsive* deverá ser ajustável de acordo com cada *viewport*.Podes calcular o tamanho da fonte baseando-te na largura e na altura do *viewport* usando `:root`:

    :root {
      font-size: calc(1vw + 1vh + .5vmin);
    }

Desta forma,podes utilizar a unidade de medida `root em` baseada no valor calculado por `:root`:

    body {
      font: 1rem/1.6 sans-serif;
    }

#### [Passeata](http://codepen.io/AllThingsSmitty/pen/XKgOkR)

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Defina `font-size` em Elementos de Formulário para uma Melhor Experiência Mobile

Para evitar zoom indesejado em elementos de formulários de navegadores mobile (iOS Safari, *et al*) quando um `<select>` é selecionado, adicione `font-size` no seletor:

    input[type="text"],
    input[type="number"],
    select,
    textarea {
      font-size: 16px;
    }

:dancer:

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Usa eventos de ponteiro para controlar eventos do mouse

[Eventos de ponteiro](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events) permitem que você especifique como o mouse interage com o elemento que está tocando. Para desativar o evento de ponteiro padrão em um botão, por exemplo:

    .button-disabled {
      opacity: .5;
      pointer-events: none;
    }

É simples assim.

<sup>[Regressar\ ao\ índice](#Índice)</sup>

### Definir `display: none` em quebras de linha usadas como espaçamento

Como [Harry Roberts apontou](https://twitter.com/csswizardry/status/1170835532584235008), isso pode ajudar a impedir que os usuários do CMS usem quebras de linha extras para espaçamento:

    br + br {
      display: none;
    }

<sup>[Regressar\ ao\ índice](#Índice)</sup>

Suporte
-------

Versões atuais do Chrome, Firefox, Safari, Opera, Edge, e IE11.