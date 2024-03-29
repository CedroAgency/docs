# Миксины

Если на сайте имеется какой-либо шаблонный блок или компонент (кнопка, карточка, статья), который встречается более
одного раза, то его следует вынести в отдельный миксин.

**Неправильно:**

```jade
.products
    .product
        a.product__image(href="/product/1")
            img(src="/images/image-1.jpg" alt="")
        a.product__title(href="/product/1")
            | Название товара
        .product__description
            | Описание товара
        .product__price
            | 12345
        a.product__link(href="/product/1")
            | Подробнее

    .product
        a.product__image(href="/product/2")
            img(src="/images/image-2.jpg" alt="")
        a.product__title(href="/product/2")
            | Название товара
        .product__description
            | Описание товара
        .product__price
            | 67890
        a.product__link(href="/product/2")
            | Подробнее
```

**Правильно:**

Создаем миксин

```jade
mixin product(props = {})
    .product&attributes(attributes)
        a.product__image(href=props.href)
            img(src=props.image alt="")
        a.product__title(href=props.href)= props.title
        .product__description= props.description
        .product__price= props.price
        a.product__link(href=props.href)
            | Подробнее
```

Подключаем миксин в `components.pug`:

```jade
include block/card
include block/product
```

После можно использовать созданный миксин на любой странице:

```jade
.products
    +product({
        href: '/product/1',
        image: '/images/image-1.jpg',
        title: 'Название товара',
        description: 'Описание товара',
        price: 12345
    })

    +product({
        href: '/product/2',
        image: '/images/image-2.jpg',
        title: 'Название товара',
        description: 'Описание товара',
        price: 67890
    })
```


В миксины всегда передаём объект `props` и прокидываем атрибуты на основной блок:
```jade
mixin block(props = {})

    .block&attributes(attributes)
```

# Синтаксис и форматирование
Между большими блоками кода следует оставлять одну пустую строку или дополнять комментарием

**Неправильно** (нет пустых строк):

```jade
.products
    .product
        img.product__image(src="images/products/1.png" alt="")
        .product__title
            | Название товара
        .product__description
            | Описание товара
        .product__price
            | 12345
.navigation
    a.navigation__link(href="/catalog?page=2")
        | Следующая страница
```

**Неправильно** (слишком много пустых строк):

```jade
.products

    .product
        img.product__image(src="images/products/1.png" alt="")

        .product__title
            | Название товара

        .product__description
            | Описание товара

        .product__price
            | 12345


.navigation
    a.navigation__link(href="/catalog?page=2")
        | Следующая страница
```

**Правильно:**

```jade
.products
    .product
        img.product__image(src="images/products/1.png" alt="")
        .product__title Название товара
        .product__description Описание товара
        .product__price 12345

.navigation
    a.navigation__link(href="/catalog?page=2")
        | Следующая страница
```

# Однострочная вложенность

Как правило теги вкладываются с отступом на разных строках:

```jade
ul
    li
        a(href="/page/1")
            | 1
    li
        a(href="/page/2")
            | 2
    li
        a(href="/page/3")
            | 3
```

Но в случае, **если** строк в файле довольно много и их сокращение **увеличивает читаемость**, то допустимо
использовать однострочную запись:

```jade
ul
    li: a(href="/page/1") 1
    li: a(href="/page/2") 2
    li: a(href="/page/3") 3
```

В иных случаях не следует использовать такой способ записи.

# Самозакрывающиеся теги

Самозакрывающиеся теги (`img`, `meta`, `link`) определяются автоматически, поэтому не следует указывать это явно.

# Классы

Классы записываются сразу после тега:

```jade
ul.navigation
    li.navigation__item
```

Если у элемента не указан тег, то он принимается за `div` (по этой причине не следует явно указывать тег `div`):

```jade
.container
    .block
```

Будет преобразовано в:

```html
<div class="container">
    <div class="block"></div>
</div>
```

Атрибут `class` используется только в том случае, если он задается с помощью переменной или через условие:

```jade
- page = 'index'

.menu
    a.menu__item(class={'menu__item--active': page === 'index'} href='/')
        | Главная страница
    a.menu__item(class={'menu__item--active': page === 'catalog'} href='/catalog')
        | Каталог
    a.menu__item(class={'menu__item--active': page === 'contacts'} href='/contacts')
        | Контакты
```

# Идентификаторы

Идентификатор записывается после класса или тега.

**Неправильно:**

```jade
ul#top-menu.menu
```

**Правильно:**

```jade
ul.menu#top-menu

// или так
.menu#top-menu

// или так
#top-menu
```


# Атрибуты

Атрибуты записываются в круглых скобках после указания тега, класса и/или идентификатора.

```jade
form(action="/login.php" method="post")
    input(type="email" name="email" placeholder="E-mail")
    input(type="password" name="password" placeholder="Пароль")
    button(type="submit") Войти
```

Не следует дублировать запись атрибутов.

**Неправильно:**

```jade
img(src="images/photo.jpg")(alt="")
```

**Правильно:**

```jade
img(src="images/photo.jpg" alt="")
```

# Кавычки

Для указания значения атрибутов используются двойные кавычки.

**Неправильно:**

```jade
input(type='text' name='name')
```

**Правильно:**

```jade
input(type="text" name="name")
```

# Разделение атрибутов

Атрибуты разделяются одним пробелом.

**Неправильно:**

```jade
img(src="images/logo.png", srcset="images/logo@2x.png 2x", alt="")
```

**Правильно:**

```jade
img(src="images/logo.png" srcset="images/logo@2x.png 2x" alt="")
```

# Нестандартные атрибуты

Атрибуты, в названии которых используются нестандартные символы (`(`, `)`, `[`, `]`, `:`, `@`) записываются в одинарных
кавычках.

**Неправильно:**

```jade
// Не скомпилируется
button(type="button" (click)="send()") Отправить
```

```jade
button(type="button" v-on:click="send()") Отправить
```

```jade
button(type="button" @click="send()") Отправить
```

**Правильно:**

```jade
// Не скомпилируется
button(type="button" '(click)'="send()") Отправить
```

```jade
button(type="button" 'v-on:click'="send()") Отправить
```

```jade
button(type="button" '@click'="send()") Отправить
```

# Многострочная запись атрибутов

Если атрибутов слишком много и/или длина строки превышает установленный предел, то следует записать каждый атрибут
в отдельной строке:

```jade
input(
    type="text"
    name="name"
    placeholder="Имя"
    maxlength="20"
    required
    autocomplete="on"
)
```

# Использование переменных в атбирутах

В значение атрибута можно передать переменную или любое JS-выражение:

```jade
img(src=`images/image-${image.number}.jpg` alt=image.description)
```

По умолчанию значения атрибутов экранируются.

```jade
.pagination(v-if="items.length > 5")
```

Будет преобразовано в:

```html
<div class="pagination" v-if="items.length &gt; 5"></div>
```

Отключить экранирование значения атрибута можно заменив `=` на `!=`.

```jade
.pagination(v-if!="items.length > 5")
```

Будет преобразовано в:

```html
<div class="pagination" v-if="items.length > 5"></div>
```

# JSON

JSON в атрибуте записывается в виде JS-объекта, а не строки.

**Неправильно:**

```jade
.slider(data-options="{autoplay: true, arrows: false, fade: true}")
```

**Правильно:**

```jade
.slider(data-options={
    autoplay: true,
    arrows: false,
    fade: true
})

// или так
.slider(
    data-options={
        autoplay: true,
        arrows: false,
        fade: true
    }
)
```

# Атрибут style

Атрибут style также при необходимости можно записать в виде JS-объекта.

```jade
.element(
    style={
        '-webkit-transform': 'rotate(45deg)',
        'transform': 'rotate(45deg)'
    }
)
```

# Использование `&attributes`

`&attributes` используется либо в миксинах, либо в том случае, если необходимо задать множество атрибутов элемента с помощью
переменной.

**Неправильно:**

```jade
a(href="/")&attributes({target: '_blank'})
    | На главную
```

**Правильно:**

```jade
a(href="/" target="_blank")
    | На главную
```

```jade
- attrs = {class: 'no-js', lang: 'ru'}

doctype html
html&attributes(attrs)
    head
    body
```

```jade
mixin button()
    button.button&attributes(attributes)
        block

+button().button--large(type="submit")
    | Войти
```

# Вывод текста

Текст следует выводить на следующей строке с помощью символа `|`, если текста много и это улучшит читаемость

**Неправильно:**

```jade
.product
    img.product__image(src="images/products/1.png" alt="")
    .product__title Название товара
    .product__description Lorem Ipsum is simply dummy text of the printing and typesetting industry typesetting industry.
    .product__price 12345
```

**Правильно:**

```jade
.product
    img.product__image(src="images/products/1.png" alt="")
    .product__title Название товара
    .product__description
        | Lorem Ipsum is simply dummy text of the printing and typesetting industry typesetting industry.
    .product__price 12345
```

В случае, **если** строк в файле довольно много и их сокращение **увеличивает читаемость**, то допустимо использовать
однострочную запись.

# Использование JS в Pug

Pug позволяет использовать JS в шаблонах:

```jade
// Однострочная запись
- let title = 'Title'
- let description = 'Description'
- const ROOT_PATH = './'

// Многострочная запись
-
    let attrs = {
        class: 'no-js',
        lang: 'ru'
    }

    let url = '#'
```

Не следует использовать эту возможность для создания условий и циклов, так как в Pug уже имеются специальные
конструкции.

# Вывод переменных

Существует два варианта вывода переменных — экранированный и неэкранированный:

```jade
// Экранированный
.product
    .product__title= title
    .product__description= description
    .product__price= price

// Неэкранированный
.product
    .product__title!= title
    .product__description!= description
    .product__price!= price
```

# Вывод переменных в тексте

При необходимости вывести переменную в тексте следует воспользоваться конструкцией `#{}` (для экранированного вывода)
или `!{}` (для неэкранированного вывода):

```jade
.product
    .product__title
        | Название товара: #{title}
    .product__description
        | Описание: #{description}
    .product__price
        | Цена: !{price}р.
```

# Вывод элементов в тексте

Элементы в тексте записываются с помощью конструкции `#[]`.

**Неправильно:**

```jade
.product
    .product__title
        | <b>Название товара:</b><br>
        | <a href="/product/1">#{title}</a>
    .product__description
        | <b>Описание:</b><br>
        | #{description}
    .product__price
        | <b>Цена:</b><br>
        | !{price}р.
```

```jade
.product
    .product__title
        b Название товара:
        br
        a(href="/product/1") #{title}
    .product__description
        b Описание:
        br
        | #{description}
    .product__price
        b Цена:
        br
        | !{price}р.
```

**Правильно:**

```jade
.product
    .product__title
        | #[b Название товара:]#[br]
        | #[a(href="/product/1") #{title}]
    .product__description
        | #[b Описание:]#[br]
        | #{description}
    .product__price
        | #[b Цена:]#[br]
        | !{price}р.
```

После `#[br]` следует ставить перенос строки.

# Вывод кода

При необходимости записать `<script>` или `<style>` непосредственно в Pug, то можно воспользоваться следующей конструкцией:

```jade
script.
    (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
    (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
    m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
    })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

    ga('create', 'UA-123456789-00', 'auto');
    ga('send', 'pageview');

style.
    img[href*="tns-counter"] {
        position: absolute;
        left: -9999px;
    }
```

Но настоятельно рекомендуется выносить такой код в отдельные файлы и подключать через `include`

# Управляющие конструкции

* `if` — используется для условий.

**Неправильно:**

```jade
- if (products.length) {
    .products
        // ...
- }
```

**Правильно:**

```jade
if products.length
    .products
        // ...
```

* `unless` — предназначена для замены условий c отрицанием `if !someVar`. Повышает читаемость

* `case` — предназначена для множественных условий. Практически не используется.

* `each` — предназначена для создания циклов.

**Неправильно:**

```jade
- for (var i = 0; i < products.length; i++) {
    - var product = products[i];
    .product
        .product__title= product.title
        .product__description= product.description
        .product__price= product.price
- }
```

**Правильно:**

```jade
each product in products
    .product
        .product__title= product.title
        .product__description= product.description
        .product__price= product.price
```

```jade
each i in Array.from(Array(10).keys())
    img(src=`images/frame-${i}.jpg` alt="")
```

* `while` — не используется.

# Подключение файлов

Если страница состоит из нескольких независимых блоков, то каждый следует вынести в отдельный файл или в миксин

**Неправильно:**

```jade
.header
    // ...
.banner
    // ...
.container
    .sidebar
        // ...
    .content
        .filter
            // ...
        .products
            // ...
        .pagination
            // ...
.footer
    // ...
```

**Правильно:**

```jade
+header()
+banner()
.container
    include pug/sidebar
    .content
        +filter()
        +products()
        +pagination()
```

При подключении Pug-файлов не нужно указывать расширение.

**Неправильно:**

```jade
include pug/header.pug
```

**Правильно:**

```jade
include pug/header
```

Подключать можно не только Pug, но и любые другие файлы. Например svg:

```jade
.header
    a.header__logo(href="/")
        include ../img/logo.svg
```
Если на странице используются какие-либо счетчики (Google Analytics, Яндекс Метрика и тому подобноее), то этот также следует выносить в отдельный файл js:

```jade
    include ../js/ya-counter.js
```


# Комментарии

Для комментариаев используется синтаксис `//` и `//-`:

```jade
// Однострочный комментарий, который попадет в html

//- Однострочный комментарий, который не попадет в html

//
    Многострочный комментарий,
    который попадет в html

//-
    Многострочный комментарий,
    который не попадет в html
```
