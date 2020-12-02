# Estudo documento sobre SASS


## Propriedade Aninhadas

```
nav {
  font: {
    family: ...
    style: ...
    size: ...
  }
}
```

## Variáveis

```
$width: 100%;

nav {
  width: $width;
}
```

**Boas práticas:**
*Separar palavras por - ou —*

## Interpolação

```
p {
  $font-size: 12px;
  $line-height: 30px;
  font: #{$font-size}/#{$line-height};
}
```

Compilado:
```
p {
  font: 12px/30px;
}
```
__________________________________________________________________________________________


```
$nome: destaque;
$attr: border;

p.#{$name} {
  #{#attr}-color:blue;
}
```

Compilado:
```
p.destaque {
  border-color: blue;
  }
```

## Extend

```
.error {
  border: ...
  background-color: ...
}

.attention {
  ...
}

.seriousError {
  @extend.error;
  @extend.attention;
  border-width: 3px;
}
```
__________________________________________________________________________________________

```
a:hover {...}

.hoverlink{
  @extend a:hover{};
  color: white;
}
```

## Operações

Adição => + <br />
Subtração => - <br />
Multiplicação => * <br />
Divisão => / <br />
Módulo => % <br />

**Símbolo de - pode significar:**
- Subtração
- Número Negativo
- Operador de negação unário (-$var)
- Identificador (font-size);
  - _Ex.: font-size: 5px -2; //3px;_

## Mixins

Permite definir estilos que podem ser reutilizados em toda a folha de estilo; <br />
Não agrupa blocos de código; <br />
Faz algo, porém sem retorno. <br />

```
@mixin border-radius($radius) {
  border-radius: $radius;
  -webkit...
  -moz...
  -ms...
}

.box {
  @include border-radius(10px;)
}

@mixin titulo($size, $color:blue) {
  color: $color;
  font-size: $size;
}

h1 {
  @include titulo(14px;)
}

h2 {
  @include titulo(14px, green;)
}
```

Lista em Mixin
```
@mixin padding ($values ...) {
  padding: $values;
}

p {
  @include padding (10px 20px 30px 40px);
}
```

## Functions

```
@function calc-fluid ($target, $container) {
  @return ($target/$container) * 100%;
}
```

SCSS
```
div {
  width: calc-fluid (400,1000);
}
```

Compilado:
```
div{
  width: 40%;
}
```

## Placeholder

Agrupa blocos de código; <br />
Semelhante a classe; <br />
Não são compilados; <br />
São utilizados para reaproveitar blocos estáticos de código, já os mixins são esperados para serem utilizados em blocos dinâmicos que sempre recebem valores diferentes.

```
%center {
  display: block;
  margin: 0 auto;
}

div {
  @extend %center;
}
```

Compilado:
```
div {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
```