# Introdução a Animações Web (2D)
## Conteúdo
0. [Introdução](#intro)  
    - Animações no nosso dia a dia
    - Na Web: A experiência que elas nos oferece
    - Métodos e formas
    - Sobre este tutorial
1. [Animações em HTML puro](#HTML)  
    - SVG  
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

Animações em HTML puro pode ser feitas de uma forma. Por meio de SVG e tags de animação. Controlando a forma, movimentos, cor e outras propriedades do SVG por meio das tags fornecidas por meio da SMIL (Synchronized Multimedia Integration Language).  
Vale dizer que os browsers da Microsoft e Opera não aceitam as tags SMIL. Portanto, se seu projeto tem foco em Microsoft Edge, Internet Explorer ou Opera, não use esse método.

## SVG  
### O que é SVG?
SVG (Scalable Vector Graphics) é um padrão criado pela W3C para a definição de imagens vetoriais usadas em páginas web. A sintaxe do SVG é muito semelhante ao do XML, além de trabalhar com componentes vetoriais como as curvas bezier e splines. Algumas das principais qualidades para o uso de imagens vetoriais na web é de serem muito leves e de serem facilmente escaláveis, ou seja, a imagem não perde a qualidade se for redimencionada, o que é ótimo para aplicações responsivas.  
Como o exemplo a seguir, essa é uma imagem estática feita em SVG em um programa de edição de imagem.  
    > botar imagem SVG aqui  
Essa imagem é na verdade um documento de tags assim como o XML e HTML  
    > botar código da imagem  
E com tags parecidas com as acima podemos animar elementos dentro de nossas imagens.  
Veremos agora com alguns exemplos de como animar essas imagens. Agora, se não está familirizado com tags SVG, recomendo fazer uma pausa nesse texto e ir entender um pouco, talvez criar algumas imagens por código ou até brincar com algum aplicativo de imagens vetoriais como o [Inkskape](https://inkscape.org/).  Eu devo explicar algum dos elementos aqui, mas de forma bem rasa para dar mais foco em como animar em si.


### Animações SVG
#### parte 1
Nessa parte vamos falar de 2 tags de animação: <b>```<animate>```</b> e <b>```<animateTransform>```</b>  
```<animate>```como o nome já diz é uma tag que anima algum elemento. No caso, essa tag irá animar um determinado atributo, indo de um valor para o outro em determinado periodo de tempo.  
```<animateTransform>``` efetua uma transformação, como uma rotação, translação, escala e assim vai.
Essas tags serão incluidas dentro de nossos elementos para indicar que esses lementos possuem tal propriedade de serem animadas naquele momento.
Aqui faremos uma bolinha quicar no chão uma vez e cair de forma inelastica após isso.  
*Não ligue (tanto) para o fato da animação não estar tão perfeita. Estou fazendo isso mais para mostrar as tags, como elas funcionam e como usalas.*
```HTML
<svg version="2.0" xmlns:"http://www.w3c.org/2000/svg" width="500" height="500" viewBox="0 0 500 500">

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
>Inserir link para o primeiro exemplo aqui  
``viewBox`` modula as proporções do documento pelos valores fornecidos, possibilitando o sistema de coordenadas caber em janelas de tamanhos diferentes. São definidos os tamanhos mínimos de x e y assim como o comprimento e a largura do viewBox. Para entender melhor [leia sobre no MDN](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/viewBox).  
``attributeName`` é o atributo que será alterado pelo tag, no caso de ``animateTransform`` o valor dessa tag será ``transform`` e será definido o tipo da transformação pelo atributo ``type``.  
``from`` e ``to`` os valores inicial e final da animação respectivamente. O valor podem ser de uma posição, cor, ângulo, etc.  
``begin`` e ``dur`` determina quando começar e quanto dura a animação. No caso de begin não ser declarado a animação por padrão começa em 0 segundos. Você pode definir ambos em segundos, minutos, milisegundos e mais. Para mais definições sobre tempo, veja a sintaxe de [tempos](https://svgwg.org/specs/animations/#ClockValueSyntax).  
``type``: Define para ``<animateTransform>`` o tipo de transformação a ser executada. No nosso caso foi o ``rotate``, mas outras estão disponíveis como ``translate``, ``rotate``, ``skewX`` e ``skewY``.  
``transform="rotate"`` tem algumas peculiaridades interessantes. Pois assim como você pode rotacionar diretamente colocar somente o ângulo (primeiro argumento) em ``from`` e ``to``, você pode incluir o centro de rotação daquele objeto (segundo e terceiro argumentos, ``x`` e ``y`` respectivamente). Caso não seja incluido o centro de rotação, será tomado como centro o a coordenada 0,0 do documento (o canto superior esquerdo).  
``fill="freeze"`` faz com que ao final da animação o objeto permaneça na posição final declarada.
#### parte 2
```HTML
<svg version="2.0" xmlns="http://www.w3c.org/2000/svg" width="700" height="700" viewBox="-100 -100 700 700">
  <path id="around" d="M10 250 A200 200 0 0 0 490 250 A200 200 0 0 0 10 250" fill="none" stroke="black"/>
  <circle id="earth" cx="" cy="" r="50" fill="blue"/>
  <circle cx="250" cy="250" r="100" fill="yellow"/>
  <animateMotion href="#earth" begin="0s" dur="10s" repeatCount="indefinite">
      <mpath href="#around"/>
  </animateMotion>
</svg>
```
Nesse exemplo é abordado o ``<animateMotion>``, aonde podemos associar um caminho para movimento de um objeto SVG. Nesse caso montamos um caminho com o comando ``path``, incluimos um id a ele (desculpe, sou ruim com nomes de id) e anexamos ao tag ``mpath`` por meio de um link ``href`` (se já usou HTML antes sabe aonde já viu isso). Assim a tag associa o caminho montado previamente para o movimento. Também mantive o valor de ``stroke`` para que fosse possível enxergar o nosso caminho.  
Note que nosso circulo com a ``ìd="earth"`` não tem os valores definidos para ``cx`` e ``cy``. Isso por que nossa tag de ``<animateMotion>`` vai definir esses valores para gente enquanto executa. Se definir os valores eles serão somados ao path e sua animação será deslocada.  
``repeatCount`` permite definir um valor para quantas vezes a animação será repetida. Use o valor ``indefinite`` para que a animação atue infinitamente.  
E para finalizar, note que as tags de animação não estão dentro das tags dos objetos. Isso para mostrar que é possível conectar as animações por meios de ``id``s e links ``href``. E não se esqueçam de usar ``#`` ao usar um link ``href``.  
Dessa vez alterei o ``viewBox`` para enquadrar melhor a tela do SVG e assim os circulos não serem "comidos" ao passar pelas bordas.  
Para esse exemplo eu somente usei ``path`` para criar dois arcos e formar uma circunferência. Saiba que há outros parametros para fazer curvas bem mais complexas dentro do path, como curvas de bezier. Dê uma olhada em [paths](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths) pela MDN.  
#### parte 3
#### vá além
Há muitas outras tags para animar um conteúdo em SMIL. Tags como ``<set>``,``<def>`` e ``<use>`` além de muitas outras são fornecidas para criar animações web e podem ser muito uteis em algum projeto. Você pode encontrar mais coisa sobre SVG e animações em SVG nos seguintes links  
- [A Compendium of SVG Information](https://css-tricks.com/mega-list-svg-information/)
- [SVG2 - W3C](https://www.w3.org/TR/SVG2/)
- [SVG Animation Level 2 - W3C(Draft)](https://svgwg.org/specs/animations/)
- [Registro de elementos(vão ter algumas coisa traduzidas para o português)](https://developer.mozilla.org/pt-BR/docs/Web/SVG/Element)
- [Structing, grouping, and referencing in SVG](https://www.sarasoueidan.com/blog/structuring-grouping-referencing-in-svg/) - Sara Soueidan tem muita coisa sobre SVG e vale a pena conferir
- [SVG can do that?! - Vídeo](https://www.youtube.com/watch?v=ADXX4fmWHbo) - Sarah Drasner, outra pessoa que tem muita coisa com SVG para conferir
- Qualuqer coisa além disso, pesquise no Google. Tem muita coisa interessante que você pode achar, até porque SVG é um assunto bem profundo e vasto.  

## conclusão
SVG é bem poderoso. Se continuar pesquisando vai ver que é um assunto bem vasto e extendido para muitas outras áreas, e tudo pode ser feito usando poucas tags. Mas também pode ser um pouco difícil de controlar, especialmente se manipular os valores diretamente sem ajuda de programas ou outras ferramentas.  
Veremos mais para frente que com outros recursos poderemos montar animações em SVG mais poderosas e mais facilmente manipuláveis. Assim como para essas ferramentas mostrar que SVG também é algo muito bem aproveitável para elas.

<h1 id="css">Animações em CSS "puro"</h1>

### O que é CSS?
CSS (Cascade Style Sheets) são, traduzindo ao pé da letra, folhas de estilo em cascata. O que elas fazem? Coisas bonitas. Elas fazem o "estilo" das páginas em HTML. Geralmente a ordem é: HTML é usado para estruturar a [DOM](https://www.w3.org/DOM/). CSS é usado para incluir cor, tipos, [box model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model) e outras coisas.

### Animações com CSS
Animações com CSS são bem fáceis de fazer e muito ricas em funcionalidades. Tudo isso graças a uma poderosa função (sim função) chamada ```@keyframes```. Ela permite que criemos, por meio de porcentegem ou ([outros termos](https://developer.mozilla.org/pt-BR/docs/Web/CSS/@keyframes#Syntax)) mudanças nas propriedades de um elemento da DOM. Basta criar o ``@keyframes`` com suas funcionalidades e aplicar em algum elemento declarando o nome dado a animação por meio de ``animation-name`` ou por meio de ``animation`` definindo também o tempo. Claro, há outros atributos para esta ultima tag, definindo delay, tempo de iteração, função de *timing* e muito mais.  
Além disso, oferece uma camada maior de interatividade, já que o próprio CSS permite reconhecer operações do mouse. Também temos funcionalidades 3D dentro do CSS3 que possibilitam animações ricas e estilos muito bonitos para páginas web.
<!--seria bom eu falar de -webkit- -moz- e -o- aqui acredito -->
#### parte 1
<!--algo mostrando boa parte das funcionalidades e tag names-->
#### parte 2
<!--fazer algo mais complexo, usando ainda curvas de timing e efeitos interessantes-->
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

### Bibliotecas
- #### velocity  
- #### greensock  
- #### snap  
- #### svgJS   
- #### vivid.js ??
- #### moJS
- #### anime  
- #### two  
    Eu tenho que incluir essa. Só pelo nome. Heh. Apesar de fazer coisas muito legais também.
- #### E muito mais  
    Acredite, já devem ter outras bibliotecas que nasceram até a publicação desse texto. Além das outras que já existem e eu não listei aqui.

<h1 id="jspluscssplussvg">JS + CSS + SVG</h1>  


<h1 id="wNext">Próximos passos</h1>

