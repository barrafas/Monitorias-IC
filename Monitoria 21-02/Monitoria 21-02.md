# Monitoria 21/02 - Tag `<style>` e CSS


## Tópicos

-  Usando imagens da internet como source para tags img
-  Sintaxe do CSS interno à página HTML com a tag `<style>`
-  Conceito de classes e outros seletores para o CSS
-  Usando [google fonts](https://fonts.google.com/) ou importando fontes locais para a página
-  Criando uma `<nav>` com links na esquerda e na direita

## Usando imagens da internet como source para tags img

Apesar de podermos usar arquivos locais como fonte para as imagens que queremos usar em nosso site, em muitos casos isso acaba não sendo uma forma prática de trabalhar com essas imagens. Caso você queira enviar sua página HTML para alguém, por exemplo, você também seria forçado a enviar todas essas imagens locais para que a página seja renderizada corretamente no computador dessa pessoa.

Por isso, o HTML permite que você use o *endereço* de uma imagem que esteja sendo hospedada em um site na internet, sem que você precise baixá-la. Para isso, primeiro precisamos descobrir como conseguir esse endereço.

Praticamente qualquer imagem disponível na internet permite que você clique com o botão direito nela, e selecione a opção "Copiar endereço de imagem", ou "Copy image link", como mostrado a seguir:

![copy image link](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/copy%20image%20link.png)

Com esse endereço em mãos, basta usá-lo como o valor do atributo `src=` :

```html
<!DOCTYPE html>
<img src="https://upload.wikimedia.org/wikinews/en/7/7a/Minecraft_game_cover.jpeg" 
	 alt="imagem cover de minecraft"/>
```

## Sintáxe do CSS interno à página HTML com a tag `<style>`
Antes de começar a falar sobre a sintaxe CSS, acho importante mostrar primeiro a importância de utilizar desse recurso. Vamos ver a diferença entre uma página sem CSS, e essa mesma página com menos de 15 linhas de CSS escritas:

### Antes:
![series sem css](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/series%20sem%20css.png)
### Depois:
![series com css](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/series%20com%20css.png)
Como podem ver, o CSS é uma maneira extremamente prática de aplicar propriedades para seus elementos HTML. Com ele, é possível padronizar a formatação de imagens de uma página inteira, mudar a cor de todos os textos, entre diversas outras coisas.

Apesar de ser possível indicar os atributos CSS de forma *inline*, como um atributo de uma tag HTML específica, isso é **fortemente não recomendado**. Além de tornar o código mais difícil de ler, usar CSS de forma *inline* faz com que você tenha que repetir muito texto desnecessariamente. Caso você queira editar a aparência de um texto, você teria que editar cada tag relacionada à essa mudança, uma de cada vez.

Por isso, a boa prática da indústria front-end é escrever todo o código CSS em um arquivo separado. Entretanto, como isso não foi ensinado ainda, usaremos a tag `<style>` dentro do arquivo HTML, que possui a mesma sintaxe que esse arquivo CSS separado teria.

Vamos começar com o exemplo básico mostrado na comparação acima, onde iremos mudar a cor de fundo, a cor do texto, e o tamanho do texto da tag `<body>`. Além disso, queremos definir que todas as imagens dessa página tenham um tamanho de 160x160px, com uma borda azul ciano que tem um interior azul:

```html
<!DOCTYPE html>
<head>
 <meta charset="UTF-8"/>
 <title>Monitoria 21/02</title>
 <style>

 body {
	background-color: rgba(25, 5, 25, 1);
	color:rgba(255, 255, 255, 0.9);
    font-family: 'Roboto Condensed', sans-serif;
	font-size: 25px;
 } 

 img {
	border:solid 2px rgba(128, 255, 255, 0.8);
	height:160px;
	width:160px;
	padding:2px;
	background-color: blue;
 }
 </style>
</head>

<body>
  <article>
    <h2>Coisas que eu assisti</h2>
    <ul>
      <li>How I Met Your Mother (2 temporadas)</li>
      <li>ERASED</li>
      <li>Your name</li>
    </ul>
    </br>
    <img src="https://upload.wikimedia.org/wikipedia/pt/a/a5/How_I_Met_Your_Mother_season_1_DVD_Cover.jpg" alt="imagem cover de himym"/> 
    <img src="https://static.wikia.nocookie.net/animangademocracy/images/7/7e/Eraser.jpg/revision/latest?cb=20200920112104" alt="imagem cover de erased"/> 
    <img src="https://popcultura.com.br/wp-content/uploads/2017/10/poster-your-name.jpg" alt="imagem cover de your name"/>
  </article>
</body>
```

Sempre começamos abrindo a tag `<style>` na seção `<head>`, e dentro dela botamos todo o código CSS que queremos escrever. Nesse caso, queremos alterar a tag `<body>` e a tag `<img>`, então escrevemos os nomes dessas tags (que nesse contexto são chamados de "seletores"), juntos com `{}` para sinalizar o começo de um bloco. Dentro desse bloco, colocamos todas os atributos que queremos alterar, e finalizamos cada um desses atributos com um `;` no final.

Dessa forma, nós indicamos as regras gerais de estilo que essas tags terão quando a página for renderizada. 

## Conceito de classes e outros seletores para o CSS
Além de ser possível definir regras gerais para cada tag HTML, podemos ser um pouco mais específicos com essa estilização. O principal conceito que permitirá isso são as **classes**. 

Vamos tentar adicionar uma nova parte nessa página, onde indicaremos que jogos eu joguei nos últimos tempos. Entretanto, dessa vez eu quero que as imagens da arte de capa tenham uma altura de 240px. 

Para começar, precisamos atribuir uma classe para essas tags específicas. No nosso código HTML, adicionaremos novas tags `<img>` para os jogos, e dessa vez, escreveremos um atributo `class` para elas:

```html
<!DOCTYPE html>
  <article>
    <h2>Coisas que eu joguei</h2>
	<ul>
	  <li>Trails of Cold Steel I</li>
	  <li>The Binding of Isaac</li>
	  <li>Final Fantasy XIV Online</li>
	  <li>Minecraft</li>
	</ul>
    </br>
    <img class="jogos" src="https://s2.gaming-cdn.com/images/products/6430/orig/game-steam-the-legend-of-heroes-trails-of-cold-steel-cover.jpg" alt="imagem cover de cs1"/>
    <img class="jogos" src="https://cdn1.epicgames.com/dbf5337d024e457bac68f2059112da86/offer/EGS_TheBindingofIsaacRepentance_NicalisIncEdmundMcmillen_S2-1200x1600-eb480826546ffb2ed1560ceec262b615.jpg" alt="imagem cover de tboi"/>
    <img class="jogos" src="https://i.imgur.com/Lh7vqLN.jpg" alt="imagem cover de shb"/>
    <img class="jogos" src="https://upload.wikimedia.org/wikinews/en/7/7a/Minecraft_game_cover.jpeg" alt="imagem cover de minecraft"/>
  </article>
```

Agora, temos que essas imagens específicas são de uma classe arbitrária que nós criamos, chamada "jogos". Entretanto, isso por si só não irá mudar nada, elas continuarão se comportando como imagens quaisquer.

![jogos antes classe](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/jogos%20antes%20classe.png)

Para cumprir nosso objetivo, precisamos criar uma regra CSS própria para imagens que pertencem à essa classe. Para isso, usaremos o seletor `tag.classe`, como podemos ver a seguir:

```html
  <style>
  body {
    background-color: rgba(25, 5, 25, 1);
    color:rgba(255, 255, 255, 0.9);
	font-family: 'Roboto Condensed', sans-serif;
	font-size: 25px;
  }	

  img {
	border:solid 2px rgba(128, 255, 255, 0.8);
	height:160px;
	width:160px;
	padding:2px;
	background-color: blue;
  }
	
  img.jogos {
	height:240px;
  }
  </style>
```

Ao atualizar a página, temos...

![jogos com classe](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/jogos%20com%20classe.png)

Imagens com uma altura de 240px! É importante notar, também, que essa regra CSS não "desabilita" os atributos gerais de imagens definidos anteriormente. Tudo que ela faz é adicionar um atributo novo a aquelas que pertencem à tal classe. Nesse caso, como o atributo `height` já existia anteriormente, ele foi **sobreposto** pelo novo atributo definido.

No CSS, quanto **mais específico** for um seletor, **maior prioridade** ele terá. Por isso, a regra de altura para imagens da classe "jogos", que é definida pelo seletor `img.jogos`, irá sobrepor a altura de 160px, pois essa é definida pelo seletor `img`, que é mais geral.

### Outros seletores

Além de podermos usar classes para especificar nossos seletores, essa não é a única forma. Entre essas outras formas, as principais são:
- `tag1+tag2` -> Altera os atributos da `tag2` apenas quando ela foi escrita diretamente depois da `tag1`, veja o exemplo a seguir. Note que isso não é limitado para apenas duas tags, como em `tag1+tag2+tag3+tag4`.

	```html
<head>
  <style>
  h3+h2 {
	font-size: 70px;
  }
  </style>
</head>

<body>
  <h3>TesteH3</h3>
  <h2>TesteH2</h2>
  <!-- Apenas o H2 da linha acima terá o tamanho alterado -->
  <h3>TesteH3</h3>
  <h4>TesteH4</h4>
  <h2>TesteH2</h2>
</body>
```

![h3eh2](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/h3%2Bh2.png)

- `tag1 tag2` -> Altera os atributos da `tag2` apenas quando ela estiver dentro da `tag1`, veja o exemplo a seguir. Note que isso não é limitado para apenas duas tags, como em `tag1 tag2 tag3 tag4`.

	```html
<head>
  <style>
  article h2 {
	font-size: 70px;
  }
  </style>
</head>

<body>
  <h2>H2 Fora</h2>
  <article>
    <h2>H2 Dentro</h2>
    <!-- Apenas o H2 da linha acima terá o tamanho alterado -->
  </article>
</body>
```

![article h2](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/article%20h2.png)
- `tag1, tag2` -> Altera os atributos de tanto a `tag1` quanto a `tag2`. Note que isso não é limitado para apenas duas tags, como em `tag1, tag2, tag3, tag4`.
- `tag:hover` -> Altera os atributos da `tag` quando o mouse está sendo passado por cima dela.
- `tag:visited` -> Altera os atributos da `tag` quando o link ao qual ela se referia já foi visitado.

Caso tenha interesse em se aprofundar no tópico de seletores, eu recomendo o seguinte [link](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/Building_blocks/Selectors).

## Usando [google fonts](https://fonts.google.com/) ou importando fontes locais para a página

Para usar fontes do google fonts, o procedimento é bem simples. Primeiro, entre no site e selecione a fonte e o estilo que você queira usar:

![select style](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/select%20style.png)

Agora, aperte o botão no canto superior direito da tela, para abrir o painel lateral na direita:

![painel lateral](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/painel%20lateral.png)

Nele, você pode selecionar a opção `@import`, e copiar aquele código CSS que aparece abaixo. Agora, basta colocar isso nas primeiras linhas da sua tag `<style>` e chamar essa fonte usando a *font-family* indicada no painel. Nesse caso, ela se chama "Roboto Condensed". Essa é a fonte sendo usada na página HTML usada como exemplo nesse arquivo. 

Caso queira usar uma fonte local, a sintaxe é um pouco diferente. Primeiro, baixe a fonte que você desejar e coloque num diretório próximo ao da página. Depois disso, basta escrever as seguintes linhas CSS:

```css
@font-face {
 font-family: "nome desejado";
 src: url("path/ao/arquivo");
 }
```

Exemplo:


```css
@import url('https://fonts.googleapis.com/css2?family=Roboto+Condensed:wght@300&display=swap');

@font-face {
 font-family: "Mortal Kombat";
 src: url("mortal_kombat/mkmyth.ttf");
 }

body {
 background-color: rgba(25, 5, 25, 1);
 color:rgba(255, 255, 255, 0.9);
 font-family: 'Roboto Condensed', sans-serif;
 font-size: 25px;
}

h1 {
  font-family: "Mortal Kombat";
  font-size: 50px;
  letter-spacing: 2px;
  margin-bottom: 20px;
  margin-top: 20px;
}
```
```html
 <h1>Fonte do Mortal Kombat</h1>

 <p>O final <span style="color: green;">do segundo período</span> foi bem cansativo, e eu tava sem ter férias desde junho de 2020, então resolvi tirar essas férias para fazer absolutamente nada de útil e só relaxar a cabeça. </p>
```

![fonte do mortal combat](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/fonte%20do%20mortal%20kombat.png)

## Criando uma `<nav>` com links na esquerda e na direita

Esse tópico foi de grande interesse durante a monitoria, e não fui capaz de respondê-lo durante ela. Entretanto, pesquisei sobre o assunto e descobri uma maneira bem prática de conseguir uma barra de navegação com links em ambos os lados (apesar de eu não entender totalmente como ela funciona, parece ser uma gambiarra).

Primeiramente, vamos criar a estrutura HTML, que será dividida em duas listas distintas, uma para os links à esquerda, e outra para os links à direita:

```html
<nav class="nav">
<div class="nav-left">
  <ul>
    <li><a href="#">Esquerda I</a></li>
    <li><a href="#">Esquerda II</a></li>
  </ul>
</div>
<div class="nav-right">
  <ul>
    <li><a href="#">Direita I</a></li>
    <li><a href="#">Direita II</a></li>
  </ul>
</div>
</nav>
```

Agora, vamos editar o CSS:

```css
nav ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
}

/* list-style-type indica o elemento que acompanhará cada item da lista. Nesse caso, será nenhum;
   margin e padding iguais a 0 significa que não haverá nenhuma espaçamento adicional entre esse elemento e os outros ao seu redor;
   overflow: hidden impede que conteúdos que estejam "flutuando" colidam com elementos seguintes do HTML que não estejam flutuando; */

nav a {
  margin-left: 5px;
}

.nav-left {
  float: left;
}

.nav-left ul li {
  float: left;
}

.nav-right ul li {
  float: right;
}

/* A propriedade "float" faz com que o determinado elemento flutue em uma parte específica da tela */
```

Com esse CSS pronto, podemos recarregar a página e...

![página pronta](https://github.com/barrafas/Monitorias-IC/blob/main/Monitoria%2021-02/Imagens/p%C3%A1gina%20pronta.png)

Ela está pronta!
