# Синтаксис и форматирование

* Для отступов используется 2 пробела
* Не должно быть пробелов и непечатаемых символов в конце строк и между строками
* Максимальная длина строки — 120 символов.
* Максимальное количество строк в одном файле — 350
* В конце файла обязательна пустая строка
* Использовать классы и атрубуты, а не id
* `!important` используется только для того, чтобы перебить значение `style`-атрибута.


### Используем максимально плоскую структуру, без лишней вложенности. Максимальная вложенность в Блоке - 2 уровня.

**Неправильно:**

```scss
.block {
    border: 1px solid red;

    &__list {
        list-style: none;

        &-item {
            padding: 10px;

            &--active {
                font-weight: bold;
            }
        }
    }
}
```

**Правильно:**

```scss
.block {
    border: 1px solid red;

    &__list {
        list-style: none;
    }

    &__list-item {
        padding: 10px;
    }

    &__list-item--active {
        font-weight: bold;
    }
}
```


### В коде не должно быть вендорных префиксов (есть исключения)

**Неправильно:**

```scss
a {
    -webkit-transition: color 0.3s;
    -moz-transition: color 0.3s;
    transition: color 0.3s;
}
```

**Правильно:**

```scss
a {
    transition: color 0.3s;
}
```

Вендорные префиксы допустимы только в том случае, если вариант без префикса отсутствует.

```scss
@mixin retina {
    @media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
        @content;
    }
}
```

### Селекторы, свойства, `@`-правила, названия переменных, миксины, функции, `#`-цвета — все записывается в нижнем регистре.

**Неправильно:**

```scss
$Color-Cod-Gray: #1A1A1A;

.Form {
    INPUT {
        color: $Color-Cod-Gray;
    }
}
```

**Правильно:**

```scss
$color-cod-gray: #1a1a1a;

.form {
    input {
        color: $color-cod-gray;
    }
}
```

### CSS-правила отделяются друг от друга пустой строкой.

**Неправильно:**

```scss
.header {
    position: relative;
    margin: 0 auto;
    padding: 15px;
    max-width: 1000px;
    background: url("../images/header.jpg") 50% 50% no-repeat;
    @include retina {
        background-image: url("../images/header@2x.jpg");
    }
    @media (min-width: 1000px) {
        padding-top: 30px;
        padding-bottom: 30px;
    }
}
```

**Правильно:**

```scss
.header {
    position: relative;
    margin: 0 auto;
    padding: 15px;
    max-width: 1000px;
    background: url('../images/header.jpg') 50% 50% no-repeat;

    @include retina {
        background-image: url('../images/header@2x.jpg');
    }

    @media (min-width: 1000px) {
        padding-top: 30px;
        padding-bottom: 30px;
    }
}
```

### Не должно быть более одной пустой строки подряд.

**Неправильно:**

```scss
.button {
    display: inline-block;


    &::before {
        content: '';
    }
}
```

**Правильно:**

```scss
.button {
    display: inline-block;

    &::before {
        content: "";
    }
}
```

### Между свойствами не должно быть пустых строк

**Неправильно:**

```scss
.button {
    display: inline-block;

    border: solid 1px $color-black;
    border-radius: 4px;

    padding: 5px 10px;

    font-family: $font-family-roboto;
    font-weight: 300;
    font-size: 16px;
    line-height: 1.5;

    text-align: center;
    text-decoration: none;

    cursor: pointer;
}
```

**Правильно:**

```scss
.button {
    display: inline-block;
    border: solid 1px $color-black;
    border-radius: 4px;
    padding: 5px 10px;
    font-family: $font-family-roboto;
    font-weight: 300;
    font-size: 16px;
    line-height: 1.5;
    text-align: center;
    text-decoration: none;
    cursor: pointer;
}
```

### При перечислении селекторов каждый записывается на отдельной строке.

**Неправильно:**

```scss
.prev, .next {
    position: absolute;
    top: 50%;
}
```

**Правильно:**

```scss
.prev,
.next {
    position: absolute;
    top: 50%;
}
```

### Перед `{` ставится один пробел, а после — один перенос строки.

**Неправильно:**

```scss
.header{
    position: relative;
}

.banner  {
    max-width: 1000px;
}

.footer
{
    margin-top: 15px;
}

.container {

    margin: 0 auto;
}
```

**Правильно:**

```scss
.header {
    position: relative;
}

.banner {
    max-width: 1000px;
}

.footer {
    margin-top: 15px;
}

.container {
    margin: 0 auto;
}
```

### Перед `}` не должно быть пустых строк.

**Неправильно:**

```scss
a {
    text-decoration: none; }

p {
    margin: 15px 0;

}
```

**Правильно:**

```scss
a {
    text-decoration: none;
}

p {
    margin: 15px 0;
}
```

### Перед `:` и `,` не должно быть пробелов, а после ставится один пробел.

**Неправильно:**

```scss
.container {
    padding  :  0 15px;
    max-width:  1000px;
    background: none;
}

.button {
    box-shadow: inset 0 0 2px 1px $color-black ,0 5px 4px 0 rgba($color-black, 0.25);
    transition: color 0.3s , opacity 0.3s;
}
```

**Правильно:**

```scss
.container {
    padding: 0 15px;
    max-width: 1000px;
    background: none;
}

.button {
    box-shadow: inset 0 0 2px 1px $color-black, 0 5px 4px 0 rgba($color-black, 0.25);
    transition: color 0.3s, opacity 0.3s;
}
```

### После открывающей и до закрывающей скобки не должно быть пробелов.

**Неправильно:**

```scss
a[ href ] {
    color: darken( $color-blue, 10% );
    cursor: pointer;
}
```

**Правильно:**

```scss
a[href] {
    color: darken($color-blue, 10%);
    cursor: pointer;
}
```

### Перед и после операторов (`+`, `-`, `*`, `/`) и комбинаторов (`+`, `>`, `~`) ставится один пробел.

**Неправильно:**

```scss
.sidebar {
    width: calc((100%- 30px)/2);

    >a {
        display: block;
    }
}
```

**Правильно:**

```scss
.sidebar {
    width: calc((100% - 30px) / 2);

    > a {
        display: block;
    }
}
```

### Строки и пути записываются в одинарных кавычках.

**Неправильно:**

```scss
li {
    list-style: none;

    &::before {
        content: '';
        display: inline-block;
        vertical-align: middle;
        width: 10px;
        height: 10px;
        background-image: url(../images/point.png);
    }
}
```

**Правильно:**

```scss
li {
    list-style: none;

    &::before {
        content: '';
        display: inline-block;
        vertical-align: middle;
        width: 10px;
        height: 10px;
        background-image: url('../images/point.png');
    }
}
```


### Значения атрибутов записываются в двойных кавычках.

**Неправильно:**

```scss
a[target=_blank]::after {
    content: "";
    display: inline-block;
    width: 15px;
    height: 15px;
    background-image: url("../images/new-page.png");
}
```

**Правильно:**

```scss
a[target="_blank"]::after {
    content: '';
    display: inline-block;
    width: 15px;
    height: 15px;
    background-image: url("../images/new-page.png");
}
```

### Названия шрифтов записываются в одинарных кавычках, за исключением ключевых слов.

**Неправильно:**

```scss
$font-family-roboto: Roboto, sans-serif;

.button {
    font-family: $font-family-roboto;
}
```

**Правильно:**

```scss
$font-family-roboto: 'Roboto', sans-serif;

.button {
    font-family: $font-family-roboto;
}
```

### Псевдоэлементы записываются с помощью `::`.

**Неправильно:**

```scss
.list {
    &__item {
        &:before {
            content: "";
            display: inline-block;
            vertical-align: middle;
            border-radius: 50%;
            width: 8px;
            height: 8px;
            background-color: currentColor;
        }
    }
}
```

**Правильно:**

```scss
.list {
    &__item {
        &::before {
            content: '';
            display: inline-block;
            vertical-align: middle;
            border-radius: 50%;
            width: 8px;
            height: 8px;
            background-color: currentColor;
        }
    }
}
```

### Не должно быть дублирующихся свойств.

**Неправильно:**

```scss
.button {
    display: inline-block;
    border: solid 1px $color-black;
    border-radius: 4px;
    padding: 5px;
    font-family: $font-family-roboto;
    font-weight: 300;
    font-size: 16px;
    line-height: 1.5;
    text-align: center;
    text-decoration: none;
    cursor: pointer;
    border: none;
}
```

**Правильно:**

```scss
.button {
    display: inline-block;
    border: none;
    border-radius: 4px;
    padding: 5px;
    font-family: $font-family-roboto;
    font-weight: 300;
    font-size: 16px;
    line-height: 1.5;
    text-align: center;
    text-decoration: none;
    cursor: pointer;
}
```

### `font-weight` записывается в числовом формате.

**Неправильно:**

```scss
b {
    font-weight: bold;
}
```

**Правильно:**

```scss
b {
    font-weight: 700;
}
```

### У нулевых значений не указываются единицы измерений (кроме времени).

**Неправильно:**

```scss
.button {
    margin: 0px auto;
    padding: 5px 0px 6px;
}
```

**Правильно:**

```scss
.button {
    margin: 0 auto;
    padding: 5px 0 6px;
}
```

### Для чисел в интервале `(-1, 1)` указывается ведущий ноль.

**Неправильно:**

```scss
a {
    transition: color .3s;
}
```

**Правильно:**

```scss
a {
    transition: color 0.3s;
}
```

### Вместо именованных цветов используется `#`-запись.

**Неправильно:**

```scss
$color-black: black;
```

**Правильно:**

```scss
$color-black: #000;
```

### Для записи `#`-цвета следует использовать сокращенный вариант, если это возможно.

**Неправильно:**

```scss
$color-black: #000000;
```

**Правильно:**

```scss
$color-black: #000;
```

### Для записи цвета в RGB или HSL формате, используем запись без запятых

**Неправильно:**

```scss
background-color: rgb(0, 0, 0);
background-color: rgba(0, 0, 0, 0.5);
```

**Правильно:**

```scss
background-color: rgb(0 0 0);
background-color: rgb(0 0 0 / 0.5);
background-color: rgb(0 0 0 / 50%);
```

### При записи `rgba`-цвета задается `#`-значением или переменной.

**Неправильно:**

```scss
.overlay {
    background-color: rgba(0, 0, 0, 0.5);
}
```

**Правильно:**

```scss
.overlay {
    background-color: rgba($color-black, 0.5);
}
```

# `@extend`

Вместо директивы `@extend` следует использовать `@mixin`.

# Порядок правил

* CSS-переменные.
* `$`-переменные.
* `@include` без контента
* Свойства
* `&::before`
* `&::after`
* Различные селекторы
* `&:link`
* `&:visited`
* `&:focus`
* `&:hover`
* `&:active`
* `&:first-child`
* `&:last-child`
* `&:nth-child()`
* `&[attr]`
* `&.modifier`
* `&--modifier`
* `@include` с контентом
* `@media`
