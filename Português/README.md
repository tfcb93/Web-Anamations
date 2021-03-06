# Introdução a Animações Web (2D)
## Conteúdo
0. [Introdução](#intro)  
    - Animações no nosso dia a dia
    - Sobre este tutorial
1. [Animações em HTML puro](#HTML)  
    - O que é SVG  
    - Animações SVG  
2. [Animações em CSS "puro"](#CSS)
    - Sobre CSS  
    - Animações CSS  
3. [CSS + SVG](#cssplussvg)  
    - Introdução
    - Exemplos
4. [Animações em JS "puro"](#JS)  
    - Sobre JS  
    - Canvas  
    - Web Animation API (WAAPI)  
        - O que é WAAPI  
        - Diferenças entre SVG e WAAPI  
    - Bibliotecas  
5. [JS + CSS + SVG](#jspluscssplussvg)  
    - Introdução  
    - Exemplos  
6. [Próximos passos](#wNext)  
    - The 2 ways  
        - The hard way  
        - The easy way  
    - WebGL  
    - ThreeJS
    - PixiJS  


<h1 id='intro'>Introdução</h1>

Animações são muito presentes em nosso dia a dia. E saiba que não precisa ser um fã de desenhos animados para encontrar animações por ai. Comerciais, aberturas de programas de TV, vídeo clipes, e até mesmo aquela faixa informando o nome e a profissão de uma pessoa em um tele jornal. Tudo isso é animado de alguma forma.   
Animações chamam a atenção das pessoas, fazem elas prestar atenção por mais tempo, e claro enriquece aplicações. Repare nas telas de loading de um jogo, ou em efeitos de *fade-in* e *fade-out* em transições, botões animados, [*drawers*](https://material.io/guidelines/patterns/navigation-drawer.html#navigation-drawer-specs), [FABs](https://material.io/guidelines/components/buttons-floating-action-button.html) e até mesmo as bolinhas da mensagem de *"digitando"* em aplicativos de conversa.  Esses pequenos detalhes são importantes para a experiência do usuário.  
E claro que a *world wide web* não podia ficar de fora. Principalmente nos dias atuais da *Web 2.0* aonde aplicações inteiras rodam na tela do browser de seu computador sem precisar instalar nada.  
Para web é muito importante respeitar dois fatores: Tempo e tamanho.  
<b>Tempo:</b> Dependendo do seu projeto você deverá fazer alguma animação muito rápida. As vezes milésimos de segundo, seja para mostrar ao usuário um *feedback* de um botão, seja para mostrar uma animação em loop de uma tela de loading que será "apagada" de sua tela quando sua aplicação carregar. Outras aplicações podem exigir animações mais longas, como telas de *on boarding*, interações com a aplicação e *sprites* em jogos. Tudo isso depende do seu propósito.  
<b>Tamanho:</b> Ao contrário de aplicações desktop que podem abusar de recursos nos computadores atuais, não podemos levar isso em consideração com relação a web. Por mais que seu browser esteja instalado em seu computador, não podemos esquecer que nem todos os usuários dependem de conexões banda larga de alta velocidade. Também temos outros usuários que preferem usar as aplicações web no celular ou tablet, que não possuem tantos recursos quanto um *notebook* ou *desktop* atual. Animações web devem ser leves em tamanho, chegando a pesar kbytes (claro, dependendo do propósito).  
Também temos outros fatores como nível de detalhes, identidade visual, fluidez e muito mais, mas lembre de quando for trabalhar com web, são muito importantes <b>tempo</b> e <b>tamanho</b>. Encontre o equilíbrio entre esses dois e os outros fatores e procure fazer elas o melhor possível dentro de sua aplicação.

## Este tutorial
Esse tutorial é indicado para aqueles que já viram HTML, CSS e JavaScript (os exemplos vão abordar o ECMAScript6). Se você não viu nenhum desses ou não está muito familiarizado com, eu recomendo dar uma olhada e se acostumar com a sintaxe. No entanto, não precisa ser um usuário avançado.
Além disso, como deu para ver no sumário, tem muitas formas de fazer animações web. Uma não listada, porém bem interessante seria fazer tutoriais de [After Effects](https://www.adobe.com/products/aftereffects.html), usar o [Lootie](https://airbnb.design/lottie/) nos projetos de animação e no fim passar no [SVGOMG](https://jakearchibald.github.io/svgomg/). Se quiser tentar, boa sorte (espero que tenha funcionado, pois nunca tentei).  
Aqui vamos mostrar do jeito tradicional. Como fazer com código as animações. Saber o que está acontecendo de maneira entendível e fácil.  
O método será: Uma apresentação inicial sobre o que é cada uma das APIs, ferramentas e etc. Depois indo passo a passo fazendo uma animação usando as tags apresentadas. No fim postarei algumas páginas com documentação, referências e sites interessantes com tutoriais e outros conteúdos.  
Quis adotar a ordem HTML, CSS e JS pois é assim que geralmente é feito o aprendizado sobre Web. Então resolvi colocar dessa mesma forma. Esse método também é bom para aqueles que já sabem um ou outro tópico e querem pular direto para alguma outra parte.
Outra coisa, esse tutorial não é nem um pouco formal, mas eu tento usar o português o melhor possível, além disso, sujestões podem ser enviadas abrindo uma issue no github.  
Você é bem-vindo em escolher o editor online (ou fazer em sua própria máquina) a sua escolha. Os exemplos estarão disponíveis no codepen assim como na pasta de exemplos desse curso.
Sem mais delongas, vamos ao que interessa. APRENDER! :D

<h1 id="HTML">Animações em HTML puro</h1>

Animações em HTML puro pode ser feitas de uma forma: por meio de SVG e tags de animação. Controlando a forma, movimentos, cor e outras propriedades do SVG pelas tags fornecidas na SMIL (Synchronized Multimedia Integration Language), podemos fazer as imagens SVG ganharem mais vida.  
Vale dizer que os browsers da Microsoft e Opera não aceitam as tags SMIL. Portanto, se seu projeto tem foco em Microsoft Edge, Internet Explorer ou Opera, não use esse método.

## SVG  
### O que é SVG?
SVG (Scalable Vector Graphics) é um padrão criado pela W3C para a definição de imagens vetoriais usadas em páginas web. A sintaxe do SVG é muito semelhante ao do XML, além de trabalhar com componentes vetoriais como as curvas bezier e splines. Algumas das principais qualidades para o uso de imagens vetoriais na web é de serem muito leves e de serem facilmente escaláveis, ou seja, a imagem não perde a qualidade se for redimencionada, o que é ótimo para aplicações responsivas.  
Como o exemplo a seguir, essa é uma imagem estática feita em SVG em um programa de edição de imagem.   
<img src="../Imagens/hearts.svg" width="250px"/>  
Essa imagem é na verdade um documento de tags assim como o XML e HTML  
```HTML
<svg id="Camada_1" data-name="Camada 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 137.07 115.59">
    <defs>
        <style>
            .cls-1{fill:red;}.cls-2{fill:#42b1e2;}
        </style>
    </defs>
    <title>hearts</title>
    <path class="cls-1" d="M118.39,80.43A31.07,31.07,0,0,0,74.45,36.49,31.07,31.07,0,0,0,30.51,80.43l43.94,44.35Z" transform="translate(-21.41 -27.39)"/>
    <path class="cls-2" d="M149.38,98.63a31.07,31.07,0,0,0-43.94-43.94A31.07,31.07,0,0,0,61.5,98.63L105.44,143Z" transform="translate(-21.41 -27.39)"/>
</svg>
```
E com tags parecidas com as acima podemos animar elementos dentro de nossas imagens.  
Veremos agora com alguns exemplos de como animar essas imagens. Agora, se não está familirizado com tags SVG, recomendo fazer uma pausa nesse texto e ir entender um pouco, talvez criar algumas imagens por código ou até brincar com algum aplicativo de imagens vetoriais como o [Inkskape](https://inkscape.org/). O foco desse tutorial são animações então será mais abordada as tags do SMIL.


### Animações SVG
#### parte 1
Nessa parte vamos falar de 2 tags de animação: <b>```<animate>```</b> e <b>```<animateTransform>```</b>  
```<animate>```como o nome já diz é uma tag que anima algum elemento. No caso, essa tag irá animar um determinado atributo, indo de um valor para o outro em determinado periodo de tempo.  
```<animateTransform>``` efetua uma transformação, como uma rotação, translação, escala e assim vai.
Essas tags serão incluidas dentro de nossos elementos para indicar que estes possuem tal propriedade de serem animadas.
Aqui faremos um retângulo quicar no chão uma vez e cair de forma inelastica após isso.  
*Não ligue (tanto) para o fato da animação não estar tão perfeita. Estou fazendo isso mais para mostrar as tags, como elas funcionam e como usa-las.*
```HTML
<svg version="2.0" xmlns:"http://www.w3.org/2000/svg" width="500" height="500" viewBox="0 0 500 500">

  <rect id="block" x="50" y="50" width="10" height="10">

    <animate attributeName="y" from="50" to="500" begin="1s" dur="1s" fill="freeze"/>
    <animate attributeName="y" from="490" to="400" begin="2.001" dur="0.2s"/>
    <animate attributeName="y" from="400" to="490" begin="2.201s" dur="0.2s"  fill="freeze"/>

    <animateTransform attributeName="transform" type="rotate" from="0 55 55" to="180 55 495" begin="1s" dur="1s" />
    <animateTransform attributeName="transform" type="rotate" from="180 55 495" to="270 55 400" begin="2.001s" dur="0.2s" />
    <animateTransform attributeName="transform" type="rotate" from="0 55 400" to="180 55 495" begin="2.201s" dur="0.2s" />
  </rect>
</svg>
```
<p data-height="265" data-theme-id="0" data-slug-hash="wyBWvP" data-default-tab="html,result" data-user="thiagoborges533" data-embed-version="2" data-pen-title="Tutorial SVG 1" class="codepen">See the Pen <a href="https://codepen.io/thiagoborges533/pen/wyBWvP/">Tutorial SVG 1</a> by Thiago Borges (<a href="https://codepen.io/thiagoborges533">@thiagoborges533</a>) on <a href="https://codepen.io">CodePen</a>.</p>

Apresentando algumas tags. ``viewBox`` modula as proporções do documento pelos valores fornecidos, possibilitando o sistema de coordenadas caber em janelas de tamanhos diferentes. São definidos os tamanhos mínimos de x e y assim como o comprimento e a largura do viewBox. Para entender melhor [leia sobre no MDN](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/viewBox).  
``attributeName`` é o atributo que será alterado pelo tag, no caso de ``animateTransform`` o valor dessa tag será ``transform`` e será definido o tipo da transformação pelo atributo ``type``.  
``from`` e ``to`` os valores inicial e final da animação respectivamente. O valor podem ser de uma posição, cor, ângulo, etc.  
``begin`` e ``dur`` determina quando começar e quanto dura a animação. No caso de begin não ser declarado a animação por padrão começa em 0 segundos. Você pode definir ambos em segundos, minutos, milisegundos e mais. Para mais definições sobre tempo, veja a sintaxe de [tempos](https://svgwg.org/specs/animations/#ClockValueSyntax).  
``type``: Define para ``<animateTransform>`` o tipo de transformação a ser executada. No nosso caso foi o ``rotate``, mas outras estão disponíveis como ``translate``, ``rotate``, ``skewX`` e ``skewY``.  
``transform="rotate"`` tem algumas peculiaridades interessantes. Pois assim como você pode rotacionar diretamente colocando somente o ângulo (primeiro argumento) em ``from`` e ``to``, você pode incluir o centro de rotação daquele objeto (segundo e terceiro argumentos, ``x`` e ``y`` respectivamente). Caso não seja incluido o centro de rotação, será tomado como centro a coordenada 0,0 do documento (o canto superior esquerdo).  
``fill="freeze"`` faz com que ao final da animação o objeto permaneça na posição final declarada.  
Ah sim, e se a animação não for associada à alguma ``id`` ou não for encapsulada dentro do elemento, ela afetara o documento todo.

#### parte 2
```HTML
<svg version="2.0" xmlns="http://www.w3.org/2000/svg" width="700" height="700" viewBox="-100 -100 700 700">
  <path id="around" d="M10 250 A200 200 0 0 0 490 250 A200 200 0 0 0 10 250" fill="none" stroke="black"/>
  <circle id="earth" cx="" cy="" r="50" fill="blue"/>
  <circle cx="250" cy="250" r="100" fill="yellow"/>
  <animateMotion href="#earth" begin="0s" dur="10s" repeatCount="indefinite">
      <mpath href="#around"/>
  </animateMotion>
</svg>
```
<p data-height="265" data-theme-id="0" data-slug-hash="rJMKzE" data-default-tab="html,result" data-user="thiagoborges533" data-embed-version="2" data-pen-title="Tutorial SVG 2" class="codepen">See the Pen <a href="https://codepen.io/thiagoborges533/pen/rJMKzE/">Tutorial SVG 2</a> by Thiago Borges (<a href="https://codepen.io/thiagoborges533">@thiagoborges533</a>) on <a href="https://codepen.io">CodePen</a>.</p>

Nesse exemplo é abordado o ``<animateMotion>``, aonde podemos associar um caminho para movimento de um objeto SVG. Nesse caso montamos um caminho com o comando ``path``, incluimos um id a ele (desculpe, sou ruim com nomes de id) e anexamos ao tag ``mpath`` por meio de um link ``href`` (se já usou HTML antes sabe aonde já viu isso). Assim a tag associa o caminho montado previamente para o movimento. Também foi mantido o valor de ``stroke`` para que fosse possível enxergar o nosso caminho.  
Note que nosso circulo com a ``ìd="earth"`` não tem os valores definidos para ``cx`` e ``cy``. Isso por que nossa tag de ``<animateMotion>`` vai definir esses valores para gente enquanto executa. Se definir os valores eles serão somados ao path e sua animação será deslocada.  
``repeatCount`` permite definir um valor para quantas vezes a animação será repetida. Use o valor ``indefinite`` para que a animação atue infinitamente.  
E para finalizar, note que as tags de animação não estão dentro das tags dos objetos. Isso para mostrar que é possível conectar as animações por meios de ``id``s e links ``href``. E não se esqueçam de usar ``#`` ao usar um link ``href``.  
Dessa vez alterei o ``viewBox`` para enquadrar melhor a tela do SVG e assim os circulos não serem "comidos" ao passar pelas bordas.  
Para esse exemplo eu somente usei ``path`` para criar dois arcos e formar uma circunferência. Saiba que há outros parametros para fazer curvas bem mais complexas dentro do path, como curvas de bezier. Dê uma olhada em [paths](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths) pela MDN.  
#### parte 3
```HTML
<svg version="2.0" xmlns="http://www.w3c.org/2000/svg" width="500" height="500" viewBox="0 0 500 500">
  <g id="group">
    <circle id="ball" cx = "100" cy="100" r ="10" fill="orange"/>
    <rect id="sqr" x="90" y="90" width="10" height="10" fill="blue"/>
    <rect id="rect" x="110" y="90" width="10" height="20" fill="red"/>
  </g>
  <animateTransform href="#group" attributeName="transform" type="translate" from="0 0" to="395 0" dur="3s"/>
  <animateTransform href="#ball" attributeName="transform" type="translate" from="395 0" to="245 -100" begin="3s" dur="1s" fill="freeze"/>
  <animateTransform href="#sqr" attributeName="transform" type="translate" from="395 0" to="245 400" begin="3s" dur="1s" fill="freeze"/>
  <discard href="#rect" begin="3s"/>
  <set href="#ball" attributeName="fill" to="green"/>
</svg>
```
<p data-height="265" data-theme-id="0" data-slug-hash="xYEzXG" data-default-tab="html,result" data-user="thiagoborges533" data-embed-version="2" data-pen-title="Tutorial SVG 3" class="codepen">See the Pen <a href="https://codepen.io/thiagoborges533/pen/xYEzXG/">Tutorial SVG 3</a> by Thiago Borges (<a href="https://codepen.io/thiagoborges533">@thiagoborges533</a>) on <a href="https://codepen.io">CodePen</a>.</p>


Aqui temos nossa última animação. Nela a gente mostra algumas tags já apresentadas, mas outras um tanto novas.  
``<g>`` permite agrupar elementos. Nesse caso agrupamos um circulo e 2 retângulos. Assim podemos aplicar animações em todos os elementos. Fazemos isso com nossa primeira animação, aonde ela sai da origem definida pelos nossos objetos e translada em x mais alguns pixel até chegar ao limite do ``viewBox``. Quero mais uma vez atentar aos valores de ``from`` e ``to`` que são somados ao x e y de nossos elementos.  
Ao atingir o viewBox note que um dos elementos do grupo some. Isso acontece pois aos 3 segundos a tag ``<discard>`` é ativada, eliminando nosso elemento com ``ìd="#rect"``. Note que o elemento é destruido depois de um tempo dado, não se algo acontecer. Isso permite enganar fazendo um efeito de destruição por impacto, mas não é perfeito. Para entender mais sobre o ``<discard>`` dê uma olhada no documento sobre animações SVG da W3, clicando [aqui](https://svgwg.org/specs/animations/#DiscardElement).  
Também gostaria que notasse que ``<circle>`` está com ``fill`` para a cor laranja. Porém em nossa animação ela está verde. Isso graças à tag ``<set>`` que pode definir o valor de um atributo. Também pode ler mais sobre o ``<set>`` [aqui](https://svgwg.org/specs/animations/#SetElement).

#### vá além
Há muitas outras tags para animar um conteúdo em SMIL. Tags como ``<def>`` e ``<use>``, filtros, máscaras e clips, além de muitas outras são fornecidas para criar animações web e podem ser muito uteis em algum projeto. Você pode encontrar mais coisa sobre SVG e animações em SVG nos seguintes links  
- [A Compendium of SVG Information](https://css-tricks.com/mega-list-svg-information/)
- [Documentação do SVG2 - W3C](https://www.w3.org/TR/SVG2/)
- [Documentação do SVG Animation Level 2 - W3C (Draft)](https://svgwg.org/specs/animations/)
- [Registro de elementos (terá algumas coisa traduzidas para o português)](https://developer.mozilla.org/pt-BR/docs/Web/SVG/Element)
- [Structing, grouping, and referencing in SVG](https://www.sarasoueidan.com/blog/structuring-grouping-referencing-in-svg/) - Sara Soueidan tem muita coisa sobre SVG e vale a pena conferir.
- [SVG can do that?! - Vídeo](https://www.youtube.com/watch?v=ADXX4fmWHbo) - Sarah Drasner, outra pessoa que tem muita coisa com SVG para conferir.
- Qualuqer coisa além disso, pesquise no Google. Tem muita coisa interessante que você pode achar, até porque SVG é um assunto bem profundo e vasto.  
- Também recomendo dar uma olhada em [Masks](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Clipping_and_masking) e [Filters](https://www.w3.org/TR/SVG/filters.html). São de grande ajuda em certas animações.

## conclusão
SVG é bem poderoso. Mesmo com poucas tags apresentadas é possível fazer muita coisa, basta entender como usar. Se continuar pesquisando vai ver que é um assunto bem vasto e extendido para muitas outras áreas. Saiba que também pode ser um pouco difícil de controlar as animações, especialmente se manipular os valores diretamente sem ajuda de programas ou outras ferramentas.  
Veremos mais para frente que com outros recursos poderemos montar animações em SVG mais ricas e mais facilmente manipuláveis.

<h1 id="css">Animações em CSS "puro"</h1>

### O que é CSS?
CSS (Cascade Style Sheets) são, traduzindo ao pé da letra, folhas de estilo em cascata. O que elas fazem? Coisas bonitas. Elas fazem o "estilo" das páginas em HTML. Geralmente a ordem é: HTML é usado para estruturar a [DOM](https://www.w3.org/DOM/). CSS é usado para incluir cor, tipos, [box model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model) e outras coisas.

### Animações com CSS
Animações com CSS são bem fáceis de fazer e muito ricas em funcionalidades. Tudo isso graças a uma poderosa função (sim função) chamada ```@keyframes```. Ela permite que criemos, por meio de porcentegem ou ([outros termos](https://developer.mozilla.org/pt-BR/docs/Web/CSS/@keyframes#Syntax)) mudanças nas propriedades de um elemento da DOM. Basta criar o ``@keyframes`` com suas funcionalidades e aplicar em algum elemento declarando o nome dado a animação por meio de ``animation-name`` ou por meio de ``animation`` definindo também o tempo. Claro, há outros atributos para esta ultima tag, definindo delay, tempo de iteração, função de *timing* e muito mais.  
Além disso, oferece uma camada maior de interatividade, já que o próprio CSS permite reconhecer operações do mouse. Também temos funcionalidades 3D dentro do CSS3 que possibilitam animações ricas e estilos muito bonitos para páginas web.
<!--seria bom eu falar de -webkit- -moz- e -o- aqui acredito -->
#### parte 1
Para a parte um vamos montar uma tela de loading aonde elementos "saltam" na tela. Com isso veremos alguns dos elementos de animação em CSS.
<!--algo mostrando boa parte das funcionalidades e tag names-->
#### parte 2
Vamos nesse tutorial fazer um botão. Quando pressionado o botão  
<!--fazer algo mais complexo, usando ainda curvas de timing e efeitos interessantes-->
#### Ease e elementos animaveis
Nem tudo pode ser animado em CSS, somente parte dos elementos podem. [Nessa lista](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties) você pode ver quais elementos podem ser animados pelos ``@keyframes`` do CSS.  
Para certas animações iremos querer movimentos mais complexos, como um começo e encerramento mais lentos e o meio mais rápido. Para isso podemos usar funções de timing mais complexas como curvas de bezier, controlando de forma mais complexa o tempo e podemos criar efeitos mais ricos em nossas animações.
#### parte 3
<!--Mostrar algo em CSS 3D seria legal-->
#### va além

### conclusão

<h1 id="cssplussvg">CSS + SVG</h1>


<h1 id="JS">Animações em JS "puro"</h1>

### O que é JS?  
JS, ou JavaScript, ou ECMAScript e uma linguagem de programação interpretada/compilada pelo seu navegador por meio de um motor.  
Não sério, se não sabe só leia sobre [V8](https://developers.google.com/v8/) ou [SpiderMonkey](https://developer.mozilla.org/pt-BR/docs/Mozilla/Projects/SpiderMonkey), e também [babel](https://babeljs.io/). Não precisa saber tudo, mas é bom entender o que faz aquele arquivo .js ser entendido e executado em sua página.  
E essa mesma linguagem é muito poderosa e pode fazer coisas que CSS ou SMIL fazem com poucas linhas de código. E algumas vezes conseguem se manter leves também.

### JS puro?

### Canvas

### Web Animation API
Uma API nativa dos browsers para comportar animações como as animações CSS, porém com as facilidades de usar javascript. Por enquanto a API não está implementada na maioria dos browsers, e nos poucos que estão, não são 100% de suas funções que estão implementadas. Porém aguarde que esta poderá ser uma forte API para criar animações web, e o melhor de tudo é que elas poderão ser feitas out-of-the-box, sem precisar importar nenhuma outra biblioteca. O que podemos dizer sobre ela é:  
- pegue o elemento que deseja e aplique ``animate()``. Esta função recebe uma lista de objetos e um valor como parametros. O primeiro parametro é a lista de obejtos que serão animados e seus respectivos valores. Os objetos são como os nomes dados nas propriedades do CSS. O segundo parametro é o valor do tempo em milisegundos para o evento desejado.
- Um dos benefícios de se trabalhar com Web Animations API é a simplicidade de manipular valores e trabalhar com JavaScript para manipular e interagir com os objetos a serem animados.
- ``getAnimations()`` retorna uma lista com todas as animações de um objeto, incluindo as animações CSS. Permitindo também manipular as animações mesmo que definidas pelas folhas de estilo.
- Uma boa lida sobre o assunto pode ser feita no CSS-trick em: [CSS Animations VS. Web Animations](https://css-tricks.com/css-animations-vs-web-animations-api/).

### Bibliotecas
- #### velocity  
- #### greensock  
- #### react-motion
    - React-motion é uma API para utilizar a elegância da componentização do React. Ele é muito bom para criar animação em cima de componentes de interface com o usuário. Por outro lado pode ser um pouco difícil de entender e com poucos tutoriais a disposição.
- #### svgJS   
- #### moJS  
- #### anime  
- #### two  
    Eu tenho que incluir essa. Só pelo nome. Heh. Apesar de fazer coisas muito legais também.
- #### E muito mais  
    Acredite, já devem ter outras bibliotecas que nasceram até a publicação desse texto. Além das outras que já existem e eu não listei aqui.

<h1 id="jspluscssplussvg">JS + CSS + SVG</h1>  


<h1 id="wNext">Próximos passos</h1>

