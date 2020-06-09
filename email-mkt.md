<h1 align="center">
    <img alt="E-mail" src="https://cdn4.iconfinder.com/data/icons/ionicons/512/icon-email-512.png" width="100" />
    <br>
    E-mai Marketing l Responsivo.
</h1>

Documentação com o passo-a-passo de como criar um e-mail marketing básico, (sem o uso de media queries) que é responsivo.
> **PS**: créditos para o artigo original, onde me baseio → [Artigo Original](https://webdesign.tutsplus.com/tutorials/creating-a-future-proof-responsive-email-without-media-queries--cms-23919) 
> Se tiver qualquer dúvida que vá além do que está nessa documentação, por favor visite o artigo original.
> Tradução e documentação: Davi Baptista.

### Conteúdo
1. [Criando o index](#primeiro-passo)
2. [Estilos iniciais](#estilos-iniciais)
3. [Criando o container externo](#criando-o-container-externo)
4. [Adicionando uma imagem ocupando toda largura](#adicionando-uma-imagem-ocupando-toda-largura)
5. [Adicionando um Single Column Layout](#adicionando-um-single-column-layout)
6. [Adicionando um Two-column Layout*](#adicionando-um-two-column-layout)
7. [Adicionando um Three-column Layout](#adicionando-um-three-column-layout)
8. [Three-column Layout com várias linhas](#three-column-layout-com-várias-linhas)
9.  [Transformando o CSS para Inline](#transformando-o-css-para-inline)


# 1. Primeiro Passo

Criar um arquivo em branco, salve como **index.html**, então copie e cole esse código ↓
``` html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <!--[if !mso]><!-->
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <!--<![endif]-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title></title>
    <link rel="stylesheet" type="text/css" href="styles.css" />
    <!--[if (gte mso 9)|(IE)]>
    <style type="text/css">
        table {border-collapse: collapse;}
    </style>
    <![endif]-->
</head>
<body>
    <center class="wrapper">
        <div class="webkit">
            [conteúdo aqui]
        </div>
    </center>
</body>
</html>
```
### O que cada coisa faz?

- ``` <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />``` → faz com que todos os caracteres especiais do Unicode sejam suportados no documento.

- ``` <meta http-equiv="X-UA-Compatible" content="IE=edge" /> ``` →  é usado para que a versão mobile do e-mail funcione em Windows Phone.

- ```<title></title>``` → Foi incluído, embora seja melhor deixar sem. A tag title é necessária para ter um XHTML válido, mas em alguns clientes nativos de e-mail Android, eles mostram o title no topo do e-mail, o que não é o ideal.

- Entre ```<!--[if (gte mso 9)|(IE)]>``` e ```<![endif]-->``` ficam condições CSS para que tudo funcione no Outlook.

- No body, tem uma tag ```<div class="webkit">``` para versões anteriores do WebKit-powered mail clients (só o  Apple Mail 6 pra trás, e o Outlook 2011).

# 2. Estilos iniciais

Crie um arquivo .CSS em branco, e cole esse código ↓
``` css
body {
    margin: 0 !important;
    padding: 0;
    background-color: #ffffff;
}
table {
    border-spacing: 0;
    font-family: sans-serif;
    color: #333333;
}
td {
    padding: 0;
}
img {
    border: 0;
}
div[style*="margin: 16px 0"] { 
    margin:0 !important;
}
.wrapper {
    width: 100%;
    table-layout: fixed;
    -webkit-text-size-adjust: 100%;
    -ms-text-size-adjust: 100%;
}
.webkit {
    max-width: 600px;
    margin: 0 auto;
} 
```
### O que estamos fazendo?

- Zerando margins e paddings no body, tabela e células de tabela e zerando qualquer borda que pudesse aparecer em imagens linkadas.


# 3. Criando o container externo

Vamos começar com um dos **"blocos"** mais importantes: uma conditional table pro Outlook que fica escondida dos outros clientes de e-mail. Precisamos fazer isso porque vamos usar a propriedade `max-width` que o Outlook não suporta. Então precisamos criar tabelas especiais para o Outlook com a largura extada de pixels pra conter tudo no Outlook.
<img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/23919/image/004.svg">
No **index.html**, vamos deletar o `[conteúdo aqui]` e cole esse código ↓

``` html
<!--[if (gte mso 9)|(IE)]>
<table width="600" align="center">
<tr>
<td>
<![endif]-->
<table class="outer" align="center">
<tr>
        <td>
            [conteúdo aqui]
        </td>
    </tr>
</table>
<!--[if (gte mso 9)|(IE)]>
</td>
</tr>
</table>
<![endif]-->
``` 
**PS:** As tabelas especiais não tem estilo. Vou usar a Campaign Monitor’s inliner tool,  [inliner.cm](http://inliner.cm/), que já estiliza as tabelas especiais também. Se usar uma ferramenta diferente, adicione  `cellpadding="0" cellspacing="0" border="0"`  nas tabelas especiais.

Dentro da tabela especial, temos  `<table class="outer">`  que é nosso **Container Externo** para todos os clientes menos o Outlook.

Queremos que o **Container Externo** ocupe 100% em telas pequenas mas em telas maiores queremos que ocupe no máximo 600px de largura. Então vamos "setar" a largura pra 100% e dar um max-width de 600px.
<img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/23919/image/005.svg">
Então cole esse código no seu arquivo .css ↓
```css
.outer {
	Margin: 0 auto;
    width: 100%;
    max-width: 600px;
}
```
O `Margin: 0 auto;`  está "setado" aqui pra centralizar nossa tabela no Yahoo do Chrome. Dica: Com a letra maiúscula, o `Margin`  também funciona no Outlook.com, mais sobre em → [Wiktor’s comment on this blog post](https://www.campaignmonitor.com/blog/post/3921/outlook.com-drops-margin-and-float-support-entirely).

Agora que temos nossa estrutura externa, vamos colocar conteúdo.

## 4.  Adicionando uma imagem ocupando toda largura

Adicione a classe `full-width-image` ao `td` dentro da tabela `.outer` e então substitua [content goes here] com a tag de imagem, pra que então sua tabela toda se pareça com isso:
```html
<table class="outer" align="center">
    <tr>
        <td class="full-width-image">
            <img src="exemplo.jpg" width="600" alt="" />
        </td>
    </tr>
</table>
```
Especificamos a largura em pixels da nossa imagem no HTML pra que o Outlook mostre corretamente, mas nós vamos sobrepor isso com uma largura de 100% no CSS pra que ele redimensione livremente nos outros clientes:
```css
.full-width-image img {
    width: 100%;
    max-width: 600px;
    height: auto;
}
```

Também estamos "setando" a max-width pra ficar igual a largura em pixels que setamos no HTML (600px) porque o Windows Phone não funciona direito quando a max-width é setada em 100%. Colocamos a height em auto pra ter certeza de que ela não fique desproporcional em lugar nenhum. (Mais sobre  [imagens](https://webdesign.tutsplus.com/tutorials/creating-a-future-proof-responsive-email-without-media-queries--cms-23919#comment-2074740905)).

Pronto. Agora da pra ver a imagem se redimensionando do tamanho que seu viewport estiver.

## 5.  Adicionando um Single Column Layout

Adicione outra `tr`  a tabela `.outer` com esse código ↓
```html
<tr>
<td class="one-column">
        <table width="100%">
            <tr>
                <td class="inner contents">
                    <p class="h1">Lorem ipsum dolor sit amet</p>
                    <p>Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Praesent laoreet malesuada cursus. Maecenas scelerisque congue eros eu posuere. Praesent in felis ut velit pretium lobortis rhoncus ut erat.</p>
                </td>
            </tr>
        </table>
    </td>
</tr>
```
E adicione esse estilo ao seu CSS:
```css
.inner {
padding: 10px;
}
p {
    Margin: 0;
}
a {
    color: #ee6a56;
    text-decoration: underline;
}
.h1 {
    font-size: 21px;
    font-weight: bold;
    Margin-bottom: 18px;
}
.h2 {
    font-size: 18px;
    font-weight: bold;
    Margin-bottom: 12px;
}
 
/* One column layout */
.one-column .contents {
    text-align: left;
}
.one-column p {
    font-size: 14px;
    Margin-bottom: 10px;
}
```
Você pode ver que a tag  `<p>` foi usada com várias classes para estilizar o texto. Eu uso  `<p class="h1">`  ao invés de  `<h1>`  porque o Outlook.com tem alguns estilos no h1, h2 e h3 que sempre sobrescrevem o seu.

No CSS acima setamos `10px` de padding pra nossa coluna, resetamos as margins no  `<p>`, setamos uns estilos básicos pros links e as classes .h1 e .h2 , então nos asseguramos que os conteúdos da nossa coluna estão alinhados a esquerda com parágrafos estilizados.

## 6.  Adicionando um Two-column Layout*
*que vai ser centralizado quando diminuir.
<img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/23919/image/006.svg">
Primeiro adicione essa nova `tr` a tabela `.outer`. Ela vai ter um `td` com a classe `.two-column` e, dentro disso, uma tabela especial pro Outlook com duas colunas de 50% de largura.
```html
<tr>
<td class="two-column">
        <!--[if (gte mso 9)|(IE)]>
        <table width="100%">
        <tr>
        <td width="50%" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td><td width="50%" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td>
        </tr>
        </table>
        <![endif]-->
    </td>
</tr>
```
Essas colunas especiais são importantes, porque sem elas o Outlook não vai deixar as duas tabelas uma do lado da outra. Como o Outlook não suporta o `max-width` também, essas colunas ajudam a restringir cada coluna ao tamanho certo.
<img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/23919/image/007.svg">
Substitua cada `[coluna aqui]` com esse código ↓
```html
<div class="column">
<table width="100%">
        <tr>
            <td class="inner">
                [conteúdo aqui]
            </td>
        </tr>
    </table>
</div>
```
A forma que vamos fazer as duas colunas ficarem lado a lado no desktop, mas centralizarem no mobile, é usando uma combinação de `text-align: center` e `display: inline-block`. Todos elementos inline e inline-block obedecem a propriedade do text-align. Então, se nós colocarmos nossas tabelas numa div que está setada em inline-block, conseguimos facilmente setar seu alinhamento quando elas diminuem configurando a propriedade text-align no seu container. Você pode escolher left, center ou right text alignment, e seus blocos inline-block vão obeder. 

Você pode simplesmente setar a própria tabela para ser `display: inline-block`, mas só se você não for colocar mais tabelas dentro dela. As coisas podem começar a se comportar estranho se você coloca tabelas dentro de tabelas com inline-block, então se precisar colocar, sempre se assegure que o container inline-block é uma div.

Então vamos estilizar nosso `td` com a classe `.two-column`  com o alinhamento desejado. Também vamos adicionar `font-size: 0`  para se livrar de qualquer espaço entre nossas colunas dentro dessa célula.
```css
/*Two column layout*/
.two-column {
text-align: center;
font-size: 0;
}
```
Agora vamos estilizar nossa `div` inline-block que se comporta como nossa coluna:
```css
.two-column .column {
width: 100%;
max-width: 300px;
display: inline-block;
vertical-align: top;
}
```
Estamos usando uma width de 100% com uma max-width de 300px pra que essa coluna tenha 100% de largura em viewports que são menores que 300px.

Você pode setar seu `vertical-align` para o que você quiser: top, center ou bottom. Note que você pode ter muitas `tr` dessas divs dentro da mesma célula e o vertical alignment vai sempre definir o vertical alignment numa base linha por linha. Tenha certeza que qualquer um que você escolha, seja igual ao  `valign`  setado na tabela especial do Outlook, porque o Outlook não suporta  `vertical-align`. Se você tiver tendo problemas de alinhamneto no Outlook, provavelmente é isso.
Agora vamos adicionar uma tabela com duas linhas para cada coluna. Fazemos isso para que quando o layout mudar no mobile, cada imagem tem seu texto correspondente abaixo dela.

Vamos substituir nosso  `[conteúdo aqui]`  com esse código ↓
```html
<table class="contents">
    <tr>
            <td>
                    <img src="images/two-column-01.jpg" width="280" alt="" />
            </td>
    </tr>
    <tr>
            <td class="text">
                    Maecenas sed ante pellentesque, posuere leo id, eleifend dolor. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. 
            </td>
    </tr>
</table>
```
Cada coluna tem 300px de width com 10px de padding de cada lado, deixando 280px para nossa imagem.

Vamos estilizar a classe `.contents`  dando uma width de 100% ↓
```css
.contents {
width: 100%;
}
```
Então vamos estilizar nosso two-column layout e setar nosso font size e text-alignment, tendo certeza que nossas imagens vão ter 100% de largura, e pra dar um padding no texto abaixo da imagem:
```css
.two-column .contents {
font-size: 14px;
    text-align: left;
}
.two-column img {
    width: 100%;
    max-width: 280px;
    height: auto;
}
.two-column .text {
    padding-top: 10px;
}
```
Agora você deve ter um two-column layout que se adequa apropriadamente quando você deixa seu viewport menor que 300px.

## 7.  Adicionando um Three-column Layout

De novo vamos criar colunas uma do lado das outra que se adequam ao mobile usando uma combinação de  `text-align: center`  e `display: inline-block`.

Vamos usar  `text-align: center`  para que as colunas se centralizem,mas você pode sempre usar left ou right text alignment. Abaixo tem um exemplo de como o alinhamento centralizado ou a esquerda dos elementos vai ficar quando redimensionado:
<img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/23919/image/008.svg">
Exemplo de como três colunas vão se redimensionar, usando  `text-align: center`  no container.
<img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/23919/image/009.svg">
Exemplo de como três colunas vão se redimensionar, usando  `text-align: left`  no container.

Vamos repetir o processo da two-column process com mais uma coluna. Adicione a nova linha a tabela `.outer`. (Normalmente prefiro usar largura em porcentagem para as células das minhas tabelas especiais Outlook, mas nesse caso é mais fácil setar a largura de cada para 200.)
```html
<tr>
<td class="three-column">
        <!--[if (gte mso 9)|(IE)]>
        <table width="100%">
        <tr>
        <td width="200" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td><td width="200" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td><td width="200" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td>
        </tr>
        </table>
        <![endif]-->
    </td>
</tr>
```
Agora adicionamos o seguinte CSS para dar um padding adicional para essa linha. Vamos setar os estilos para as div columns que vamos adicionar, que vão ter 200px de width nesse caso.
```css
/*Three column layout*/
.three-column {
    text-align: center;
    font-size: 0;
    padding-top: 10px;
    padding-bottom: 10px;
}
.three-column .column {
    width: 100%;
    max-width: 200px;
    display: inline-block;
    vertical-align: top;
}
.three-column .contents {
    font-size: 14px;
    text-align: center;
}
.three-column img {
    width: 100%;
    max-width: 180px;
    height: auto;
}
.three-column .text {
    padding-top: 10px;
}
```
Agora vamos colocar nossas colunas substituindo `[coluna aqui]` com uma div cada:
```html
<div class="column">
    <table width="100%">
        <tr>
            <td class="inner">
                <table class="contents">
                    <tr>
                        <td>
                            <img src="images/three-column-01.jpg" width="180" alt="" />
                        </td>
                    </tr>
                    <tr>
                        <td class="text">
                            Scelerisque congue eros eu posuere. Praesent in felis ut velit pretium lobortis rhoncus ut erat.
                        </td>
                    </tr>
                </table>
            </td>
        </tr>
    </table>
</div>
```
Agora você deve ter seu three-column layout, que se ajusta de acordo com o viewport.

Pelo fato desse layout ter um número ímpar de colunas, Pode acontecer de você ficar com duas colunas em cima,e uma embaixo. Isso pode ficar muito bom se for feito um design adequado, mas também pode parecer um pouco desbalanceado. Grande parte do tempo a melhor forma de resolver isso é usando left alignment, ou usar multiplas linhas com três colunas.

## 8.  Three-column Layout com várias linhas
Quando você quiser adicionar mais linhas no seu layout com múltiplas colunas, você pode adicionar quantos elementos inline-block para um único container cell quanto quiser. Dessa forma, quando o viewport fica muito "apertado" para caberem todas as colunas, elas simplesmente se encaixam da melhor forma no espaço disponível.
<img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/23919/image/010.svg">
Enquanto você não precisa separar as linhas de divs na maioria dos clients, você precisa adicionar `<tr>`s adicionais para sua tabela especial pro Outlook.
<img src="https://cms-assets.tutsplus.com/uploads/users/30/posts/23919/image/011.svg">
É assim que as tabelas especiais funcionam no Outlook para deixar as linhas e colunas separadas.

Vamos começar criano uma nova linha na nossa tabela `.outer` com a classe  `.three-column`. Aqui temos uma nova linha com trê colunas, com uma tabela especial dentro. Você vai ver que tem três colunas no nossa tabela especial e então nós terminamos a linha das tabelas especiais com  `</tr>`  e criamos um novo  `<tr>`, quem tem outras três celulas de 200px de width.
```html
<tr>
<td class="three-column">
        <!--[if (gte mso 9)|(IE)]>
        <table width="100%">
        <tr>
        <td width="200" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td><td width="200" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td><td width="200" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td>
        </tr>
        <tr>
        <td width="200" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td><td width="200" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td><td width="200" valign="top">
        <![endif]-->
        [coluna aqui]
        <!--[if (gte mso 9)|(IE)]>
        </td>
        </tr>
        </table>
        <![endif]-->
    </td>
</tr>
```
Então vamos uma div como essa abaixo para cada célula especial, substituindo `[coluna aqui]` com o código abaixo ↓
```html
<div class="column">
    <table width="100%">
        <tr>
            <td class="inner contents">
                <p class="h2">Heading</p>
                <p>Class eleifend aptent taciti sociosqu ad litora torquent conubia</p>
                <p><a href="#">Leia Mais</a></p>
            </td>
        </tr>
    </table>
</div>
```
Agora se você redimensionar sua janela, você vai ver as tabelas preenchendo os espaços corretamente. Três colunas vão se reduzir para duas colunas com três linhas, até elas colapsarem finalmente para uma coluna com seis linhas.

## 9.  Transformando o CSS para Inline

Se sua plataforma de enviar emails não cuida do "inlining" pra você, então você vai ter que fazer isso manualmente. Primeiro, delete a tag link `<link rel="stylesheet" type="text/css" href="styles.css" />` no `<head>` do seu document e substitua com `<style type="text/css">`. Copie o conteúdo do seu style.css e cole embaixo disso, então feche a tag style com `</style>`. Por fim, copie e cole seu arquivo HTML todo no [inliner.cm](http://inliner.cm/) e espere pelos resultados. Depois de processado, copie o conteúdo e pronto!

É isso.
