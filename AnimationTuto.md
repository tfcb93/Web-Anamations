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

#### Eu peço que leia a introdução, se você é um daqueles que vai direto para os outros tópicos. Pode ser babozeira, mas deu trabalho escrever isso.
## Animações no nosso dia a dia
Animações são coisas presentes em nosso dia a dia. Não precisa ser um fã de animações(especialmente animações japonesas) como o autor desse tutorial para vê-las por ai. Comerciais, aberturas de programas de TV, vídeo clipes, comerciais, até a faixinha que diz o nome e a profissão de uma pessoa em um tele jornal. Animação está em muitas coisas.  
E esse efeito de botar imagem sobre imagem, criando a ilusão de movimento sobre os objetos, formas, linhas e outros elementos trás vida ao inanimado.  
Animação chama a atenção das pessoas, faz ela prestar atenção por mais tempo, e claro enriquece aplicações por seus detalhes. Repare nas telas de loading de um jogo, ou como o *fade-in* e *fade-out* em uma legenda de um jornal (ou como eu que noto as bolinhas do *"digitando"* em aplicativos de conversa).  Mesmo esses pequenos detalhes são importantes para a experiência do usuário.  
Gosto de pensar que com animação nós quebramos o limite do ser humano. Mesmo que de forma virtual podemos fazer bem rápido coisas que seriam fisicamente impossíveis de recriar pela ilusão ótima da animação. Por isso eu espero que nesse tutorial você consiga ter boas ideias para fazer animações fluidas e agradáveis. Mesmo que eu não aborde teoria, acredite no seu senso (e não fique com preguiça de fazer a ilusão ficar bonitinha).

## Na Web:
Bem, mas esse tutorial fala sobre animações web, certo? CERTÍSSIMO! Vamos abordar os métodos por meio de informações e códigos de exemplos como fazer tais animações para diversos propósitos.  
Porém na web temos que lidar com duas coisas muito importantes: Tempo e tamanho.  
Tempo pois ninguém quer animações de loading que duram horas, ninguém quer ver uma história de uma pessoa contada por minutos enquanto espera uma aplicação abrindo. Lembre quando foi jogar Half-Life (se nunca jogo eu recomendo jogar) e tentou tirar a animação inicial com aquela falação toda para finalmente chegar no laboratório. Chato, não é? Então em pouco tempo você tem que apresentar ao usuário algo que lhe seja agradável. Se a espera for longa, loops não tão repetitivos. Se for curta algo que ele repare e seja memorável.  
Mas tudo isso tem que ser feito de forma que seu arquivo fique leve. Imagine uma pessoa abrindo uma aplicação web. Uma tela branca sem nada por alguns segundos. Pesquisas apontam que usuários não ficam nem 5 segundos na maior parte das páginas da web(-procure o link para isso-). Então, pior ainda ter de esperar para finalmente ter um loading demorado e pesado, para ai sim ter a aplicação. NÃO! Saiba que animações web chega ao nível de kbytes e isso é importante para velocidades lentas de bandas e aparelhos com pouca memória. E sim, isso é possível.  
Claro que não precisa seguir isso sempre. Se seu projeto é ter uma animação linda, não importa tempo nem tamanho... só vai.  Pequeno teste para ver se setou o git

## Métodos e formas
Como deu para ver no sumário, pelo visto tem muitas formas de se fazer animações via web. Para dizer a verdade você pode esquecer tudo isso, fazer tutoriais de [After Effects](https://www.adobe.com/products/aftereffects.html) e usar o [Lootie](https://airbnb.design/lottie/) em seus projetos de animação. No fim passe no [SVGOMG](https://jakearchibald.github.io/svgomg/) e boa sorte (espero que tenha funcionado).  
Mas aqui vamos mostrar as formas na marra. Como fazer com código sua arte final. Saber o que está acontecendo de maneira entendível e fácil.  
O método é simples. Eu vou apresentar passo a passo cada uma das formas (que eu sei até então) de como animar para web. Você lê em seu ritmo e acompanha os exemplos.  
Eu quis adotar o modelo HTML, CSS E JS pois é assim que geralmente é feito o aprendizado sobre Web. Alguns ainda fazem de pular do HTML para o JS, mas... são alguns casos. Então resolvi colocar dessa mesma forma. Primeiro HTML, e somente ele, depois CSS e "somente ele" e por fim JS. No meio do caminho misturamos o que sabemos com mais exemplos (e mais textos longos que eu escrevo de madrugada e leio depois para saber se está bom). Esse método também é bom para aqueles que já sabem um ou outro tópico e querem pular direto para alguma outra parte. Vai que já aprendeu a animar em CSS, mas não sabe como fazer em SVG puro e seu chefe te pediu uma loading screen minuscula somente em SVG (acontece ué).

## Sobre este tutorial
Esse tutorial é indicado para aqueles que já viram HTML, CSS e JavaScript (os exemplos vão abordar o ECMAScript6). Se você não viu nenhum desses ou não está muito familiarizado com, eu recomendo dar uma olhada. Não precisa de ser um usuário avançado (não precisa manjar de react, redux, vue.js, etc etc). Eu tentarei ir direto aos detalhes importantes, mas não quero deixar buracos nas ideias por trás dos códgos. Mas saiba que se ainda não entende do assunto, pode tentar seguir o assunto em paralelo com o aprendizado das linguagens, se seu objetivo é só fazer animações web e não se aprofundar mais que isso(mas saiba que está deixando de ver muita coisa bacana assim).  
Outra coisa, esse tutorial não é nem um pouco formal, mas eu tento usar o português o melhor possível, além de medir as palavras para não causar confusão nem desconforto quanto a isso. Sujestões podem ser enviadas via: ou abrindo uma issue no github.  
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

