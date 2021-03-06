# Monitoria 14/02 - Dúvidas de HTML

## Tópicos

-  Comportamento da tag `<details>` e sua interação com `<summary>`
-  Discussão sobre [legibilidade do código e indentação dentro de tags](https://www.w3schools.com/html/html5_syntax.asp)

## Código

Esse arquivo HTML está disponível no repositório para que vocês possam baixar e editar caso queiram!

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>Aula de monitoria 14/02</title>
</head>


<body>
<article>
  <h1>Comportamento da tag details</h1>

  <details>
    <!--Caso não tenha uma tag summary, o título
    padrão será "details"-->
    <summary>Titulo do detalhe</summary>
    <p>Conteúdo do detalhe</p>
  </details>
</article>

<article>
  <h1>Guia de estilo de código HTML</h1>

  <p>Sempre mantenha legibilidade em mente,
  evite escrever textos longos em uma única linha
  e não tenha medo de quebrá-lo em várias, pois
  a página irá renderizá-lo normalmente.</p>
  
  <p>Sempre use !DOCTYPE html no começo da página,
  e tenha a tag de title e meta charset dentro
  da head. Mesmo não sendo necessário, sempre 
  escreva o corpo do código dentro da tag body, 
  e sempre feche todas as tags que você abrir.</p>

  <p>Tente manter um padrão estrutural na sua
  página, usando tags para "compartimentar" seu
  texto, como a tag article ou section. Dessa forma, 
  será muito mais simples estilizar seu HTML com CSS
  futuramente.</p>

  <p>Para indentar seu código, use dois espaços ao
  invés de apertar TAB para melhorar a legibilidade
  e evitar que o código pareça uma cobra se rastejando
  de um lado pro outro.</p>

  <p>Use indentação e linhas em branco com
  moderação, pois tornarão seu código mais difícil
  de ser lido caso forem usadas com excesso.</p>

  <p>Caso queira se aprofundar mais no assunto,
  visite <a href="https://www.w3schools.com/html/html5_syntax.asp">
  essa página</a> do W3Schools.</p>
</article>
</body>


</html>


```
