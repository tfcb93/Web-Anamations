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
Sem mais delongas, vamos ao que interessa. APRENDER! :D

<h1 id="HTML">Animações em HTML puro</h1>

Animações em HTML puro pode ser atingida de uma forma. Por meio de SVG e tags de animação. Controlando a forma, movimentos, cor e outras propriedades do SVG por meio das tags fornecidas por meio da SMIL (Synchronized Multimedia Integration Language).

## SVG  
### O que é SVG?
SVG (Scalable Vector Graphics) é um padrão criado pela W3C para a definição de imagens vetoriais usadas em páginas web. A sintaxe do SVG é muito semelhante ao do XML, além de trabalhar com componentes vetoriais como as curvas bezier e splines. Algumas das principais qualidades para o uso de imagens vetoriais na web é de serem muito leves e de serem facilmente escaláveis, ou seja, a imagem não perde a qualidade se for redimencionada, o que é ótimo para aplicações responsivas.

### Animações SVG

<h1 id="css">Animações em CSS "puro"</h1>

### O que é CSS?
CSS (Cascade Style Sheets) são, traduzindo ao pé da letra, folhas de estilo em cascata. O que elas fazem? Coisas bonitas. Elas fazem o "estilo" das páginas em HTML. Geralmente a ordem é: HTML é usado para estruturar a [DOM](https://www.w3.org/DOM/). CSS é usado para incluir cor, tipos, [box model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model) e outras coisas.

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
    Eu tenho que incluir essa. Só pelo nome. Heh. Apesar de fazer coisas muito legais também.
- #### E muito mais  
    Acredite, já devem ter outras bibliotecas que nasceram até a publicação desse texto. Além das outras que já existem e eu não listei aqui.

<h1 id="jspluscssplussvg">JS + CSS + SVG</h1>  


<h1 id="wNext">Próximos passos</h1>

