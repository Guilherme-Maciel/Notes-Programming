# CSS

Created: December 25, 2020 4:03 PM
Tags: css, front

[Diary](https://www.notion.so/Diary-581788013e264fceab54cae30ac99c31)

[DOCUMENTAÇÃO](https://developer.mozilla.org/pt-BR/docs/Web/CSS)

- ÍNDICE

# ADICIONANDO CSS

## INLINE

style=""

## HTML TAG

```html
<style></style>
```

## LINK HTML

```html
<link rel="stylesheet" type="text/css" href="../css/styles.css">
```

cria-se um arquivo CSS; no topo do documento coloca-se:

```css
/*Busca de uma fonte google online por meio do @import dentro do documento css*/
@import url('[https://fonts.googleapis.com/css2?family=Baloo+Tammudu+2&display=swap](https://fonts.googleapis.com/css2?family=Baloo+Tammudu+2&display=swap)');ESPECIFICIDADE
```

# VALOR DE UM SELETOR

mesmo se estiver na ultima linha, perderá pelo seletor maior

- Universal (*) = 0
- Elemento, pseudo-element = 1
- Class = 10
- ID = 100
- Inline = 1000 -> style=""

Quando mais classes você tiver em um elemento, soma-se todas quando estilizar no css, podendo superar um ID por exemplo

# DEVTOOLS

- `f12` no chrome
- `styles → computed`
- ordem vem de baixo para cima

# VENDOR PREFIXES

[WEBSITE1](https://ireade.github.io/which-vendor-prefix/), [WEBSITE2](https://caniuse.com/)

- permite que browsers adicionem features; uso de novidades

```css
- webkit-background-clip: text; /* Chrome, safare, ios, android*/
- moz-background-clip: text; /* Mozila */
- ms-background-clip: text; /* Internet explorer */
- o-background-clip: text; /* Opera */
```

# UNIDADES DE MEDIDA

## REM

```css
/* REM */
:root{
font-size: 10px;
}
#container .div{
widht: 10rem; /*Busca referência no :root, 10 x 10 = 100px */
height: 10rem;
}

```

## EM

```css
/* EM */
#container{
font-size: 12px;
}
#container .div{
widht: 10em; /*Busca referência no elemento pai (#container), 10 x 10 = 120px */
height: 10em;
}
```

## VH e VW

```css
/* VH e VW - View Height e View Widht */
#container .div{
widht: 10vw; /*Busca referência no navegador e monitor correspondente 100vw = 100% */
height: 10vh; /*Busca referência no navegador e monitor correspondente 100vh = 100% */
}
```

# SELECTORS

## GLOBAL

## ELEMENTS

## CLASS

## ID

## ATTRIBUTE

## PSEUDO-CLASS

## PSEUDO-ELEMENTS

```css
.button-select button:first-child{ /*aplica ao primeiro filho do .button-select*/
border:none
}

.input-block input:valid{ /*após o campo ser preenchido o input ficará vermelho*/
background-color: red;
}
```

## >

```css
.div > img{ /* Busca a primeira img dentro de .div */
width: 10px;
height: 10px;
}
```

## +

```css
fieldset + fieldset { /* aplica propriedade ao fieldset abaixo de outro*/
border: none;
}

```

# SCROLL

# ATRIBUTOS

## BACKGROUND

```css
/*Modifica o tamanho do background*/
background-size: contain;
```

# SHORTHANDS

- Resume as propriedades;
- Estão no topo da hierarquia de seus atributos. Um font é mais forte que font-size, weight...

```css
backgroud: color url(image) repeat position;

Font: style weight size/height family

border: ;

flex: ;

animation: ;
```

# ELEMENTOS

## SCROLL

```css
.element{
overflow: auto; /*Habilita scroll caso necessário*/
}

/*
estilização do scroll do site
*/

body::-webkit-scrollbar {
    width: 12px;               /* width of the entire scrollbar */
  }
  
  body::-webkit-scrollbar-track {
    background: none;        /* color of the tracking area */
  }
  
  body::-webkit-scrollbar-thumb {
    background-color: rgb(88, 88, 88);;    /* color of the scroll thumb */
    border-radius: 20px;       /* roundness of the scroll thumb */
    border: 3px solid rgb(88, 88, 88);  /* creates padding around scroll thumb */
  }
```

# DISPLAY

## FLEX

```css
#container .div{
display: flex; /* PROPRIEDADE FLEXIVEL PARA OS ELEMENTOS FILHOS */
align-items: center; /* CENTRALIZA AS FRAÇÕES NO EIXO Y*/
justify-content: center;  /* CENTRALIZA AS FRAÇÕES NO EIXO X */
gap: 2px; /* Espaço entre os itens do elemento pai */
}

flex-direction: column; /* muda a orientação de linha para coluna */
```

## GRID

```css
#container .div {
display: grid;
grid-template-columns: 1fr 1fr; /* DIVIDE AS FRAÇÕES EM COLUNAS */
align-items: center; /* CENTRALIZA AS FRAÇÕES NO EIXO Y*/
}

/* É possível escolher a área do elemento com o grid-area: */

#container .div {
display: grid;
grid-template-columns: repeat(4, 1fr); /* DIVIDE AS FRAÇÕES EM COLUNAS */
grid-template-areas: "a b c d"; /* Nomeia as 4 frações */
align-items: center; /* CENTRALIZA AS FRAÇÕES NO EIXO Y*/
}

#container .div .elm1{
grid-area: b;
}
#container .div .elm2{
grid-area: c;
}
#container .div .elm3{
grid-area: d;
}
```

## BLOCK

```css
#container .div p {
display: block;  /* ELEMENTO OCUPA TODO O ESPAÇO DA LINHA */
}
```

## INLINE

```css
#container .div p {
display: inline;  /* ELEMENTO PERMITE OUTROS ELEMENTOS INLINE AO LADO */

```

# FUNÇÕES

## RGB

## CALC

# AT-RULES

Associado ao comportamento do CSS; inicia com @

## @import

Inclui CSS externo

## @media

Regras condicionais para dispositivos diferentes

## @font-face

Inclui fontes externas

## @keyframes

Cria animações

# SOLUÇÕES

## MUDAR CONTEÚDO COM HOVER

```css
#container #content main .table-row span.order-track::after{
    content: '#';
}

#container #content main .table-row span.order-track:hover::after{
    font-size: 16px;
    content: '▶';
}
```

## SHAKING INPUT

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Shake Input</title>
    <style>
        input:invalid{
            animation: shake 300ms;
            border: red;
        }

        @keyframes shake{
            25% { transform: translateX(4px);}
            50% { transform: translateX(-4px);}
            75% { transform: translateX(4px);}
        }
    </style>
</head>
<body>
    <div class="content">
    <form action="">
        <input type="text" pattern="[a-z]*">
    </form>
    </div>
    
</body>
</html>
```

## GLASS EFFECT

```css
background: rgba(255,255,255,0.1);
backdrop-filter: blur(10px);
-webkit-backdrop-filter: blur(10px);
```

## ELLIPSIS FOR LONG TEXT

```html
<div class="text">
Texto longo, muito longo, longo demais, mds, que longo, muito longo
</div>
<style>
.text {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis
}
</style>
```
