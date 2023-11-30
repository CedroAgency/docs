# Синтаксис и форматирование

* Для отступов используется 2 пробела
* Не должно быть пробелов и непечатаемых символов в конце строк и между строками
* Максимальная длина строки — 120 символов.
* Максимальное количество строк в одном файле — 350
* В конце файла обязательна пустая строка

### Не ставим расширение при импорте модуля
**Неправильно:**

```js
import initSwiper from './modules/init-swiper.js'
import initMap from './modules/init-map.js'
```

**Правильно:**

```js
import initSwiper from './modules/sliders/init-swiper'
import initMap from './modules/init-map-contact'
```

### Не ставим `;` в конце выражений
**Неправильно:**

```js
$('form').on('submit', (event) => {
    let $form = $(event.currentTarget);

    event.preventDefault();
});
```

**Правильно:**

```js
$('form').on('submit', (e) => {
    let $form = $(e.currentTarget)

    e.preventDefault()
})
```

### Используем строгое сравнение `===` и `!==` (вместо `==` и `!=`).

**Неправильно:**

```js
if (test.currentQuestionIndex == test.questions.length - 1) {
    test.finish();
}
```

**Правильно:**

```js
if (test.currentQuestionIndex === test.questions.length - 1) {
    test.finish();
}
```

### Не должно быть неиспользуемых переменных.

**Неправильно:**

```js
let dx = event.clientX - start.clientX;
let dy = event.clientY - start.clientY;

$slider.css({
    '-webkit-transform': `translate(${dx}px, 0)`,
    'transform': `translate(${dx}px, 0)`,
});
```

**Правильно:**

```js
let dx = event.clientX - start.clientX;

$slider.css({
    '-webkit-transform': `translate(${dx}px, 0)`,
    'transform': `translate(${dx}px, 0)`,
});
```

### Переменные объявляются на отдельных строках

**Неправильно:**

```js
function showPage($page) {
    let $currentPage = $('.js-page--current'), $header = $('.js-header'), $footer = $('.js-footer');
}
```

**Правильно:**

```js
function showPage($page) {
    let $currentPage = $('.js-page--current')
    let $header = $('.js-header')
    let $footer = $('.js-footer')
}
```

### Не следует сокращать названия переменных и функций.

**Неправильно:**

```js
$('.js-scroll').on('click', (e) => {
    let $l = $(e.currentTarget);
    let h = $l.attr('href');
    let t = $(h).offset().top;

    $('html, body').animate({
        scrollTop: t,
    }, 500);
});
```

**Правильно:**

```js
$('.js-scroll').on('click', (e) => {
    let $link = $(e.currentTarget)
    let href = $link.attr('href')
    let top = $(href).offset().top

    $('html, body').animate({
        scrollTop: top,
    }, 500)
})
```

### После определения переменных следует оставлять пустую строку.

**Неправильно:**

```js
$('form').on('submit', (event) => {
    let $form = $(event.currentTarget);
    let $button = $form.find('submit');
    event.preventDefault();
    $button.prop('disabled', true);
    submitForm($form);
});
```

**Правильно:**

```js
$('form').on('submit', (e) => {
    let $form = $(e.currentTarget)
    let $button = $form.find('submit')

    e.preventDefault()
    $button.prop('disabled', true)
    submitForm($form)
})
```

### Операторы в выражениях отделяются одним пробелом.

**Неправильно:**

```js
function sum(a, b) {
    return a+b;
}
```

**Правильно:**

```js
function sum(a, b) {
    return a + b
}
```

### Перед `return` следует оставлять пустую строку.

**Неправильно:**

```js
function getQueryParam(key) {
    let params = location.search.slice(1).split('&');

    for (let param of params) {
        param = param.split('&');

        if (param[0] === key) {
            return param[1];
        }
    }
    return null;
}
```

**Правильно:**

```js
function getQueryParam(key) {
    let params = location.search.slice(1).split('&')

    for (let param of params) {
        param = param.split('&')

        if (param[0] === key) {
            return param[1]
        }
    }

    return null
}
```

### Многострочные конструкции и выражения отделяются пустой строкой.

**Неправильно:**

```js
function f() {
    console.log('f');
}
function g() {
    console.log('g');
}
let timer = {
    start() {
        this.stop();
        this.intervalId = setInterval(() => {
            console.log('Tick');
        }, 1000);
    },
    stop() {
        clearInterval(this.intervalId);
    },
};
if (x > 5) {
    x = 0;
}
if (!items.length) {
    items.push(42);
}
```

**Правильно:**

```js
function f() {
    console.log('f')
}

function g() {
    console.log('g')
}

let timer = {
    start() {
        this.stop()

        this.intervalId = setInterval(() => {
            console.log('Tick')
        }, 1000)
    },

    stop() {
        clearInterval(this.intervalId)
    }
}

if (x > 5) {
    x = 0
}

if (!items.length) {
    items.push(42)
}
```

### Не следует использовать однострочную запись `if` без фигурных скобок.

**Неправильно:**

```js
    if (!items.length) return;
```

**Правильно:**

```js
    if (!items.length) {
        return
    }
```

### Для строк используются одинарные кавычки.

**Неправильно:**

```js
let name = "John Doe"
```

**Правильно:**

```js
let name = 'John Doe'
```

# ES6 возможности

* Используются шаблонные строки вместо конкатенации.

**Неправильно:**

```js
function getDateTime() {
    let now = new Date();
    let year = now.getFullYear().toString().padStart(2, '0');
    let month = (now.getMonth() + 1).toString().padStart(2, '0');
    let day = now.getDate().toString().padStart(2, '0');
    let hours = now.getHours().toString().padStart(2, '0');
    let minutes = now.getMinutes().toString().padStart(2, '0');

    return year + '.' + month + '.' + day + ' ' + hours + ':' + minutes;
}
```

**Правильно:**

```js
function getDateTime() {
    let now = new Date();
    let year = now.getFullYear().toString().padStart(2, '0')
    let month = (now.getMonth() + 1).toString().padStart(2, '0')
    let day = now.getDate().toString().padStart(2, '0')
    let hours = now.getHours().toString().padStart(2, '0')
    let minutes = now.getMinutes().toString().padStart(2, '0')

    return `${year}.${month}.${day} ${hours}:${minutes}`
}
```

### Используется `let` вместо `var`.

**Неправильно:**

```js
var name = 'John';
var surname = 'Doe';
var fullname = `${name} ${surname}`;
```

**Правильно:**

```js
let name = 'John'
let surname = 'Doe'
let fullname = `${name} ${surname}`
```


### Используются стрелочные функции вместо анонимных.

**Неправильно:**

```js
$('form').on('submit', function (event) {
    event.preventDefault();
    submitForm(this);
});
```

**Правильно:**

```js
$('form').on('submit', (e) => {
    e.preventDefault()
    submitForm(e.currentTarget)
})
```

### Следует использовать сокращенную запись ключей объекта.

**Неправильно:**

```js
function getObjectPosition(object) {
    let $offset = $(object).offset();
    let x = $offset.top;
    let y = $offset.left;

    return {
        x: x,
        y: y,
    };
}
```

**Правильно:**

```js
function getObjectPosition(object) {
    let $offset = $(object).offset()
    let x = $offset.top
    let y = $offset.left

    return {
        x,
        y
    }
}
```

### Следует использовать сокращенную запись методов объекта.

**Неправильно:**

```js
TweenMax.from($element, 1, {
    opacity: 0,
    clearProps: 'all',
    onStart: () => {
        $element.removeClass('is-hidden');
    },
});
```

**Правильно:**

```js
TweenMax.from($element, 1, {
    opacity: 0,
    clearProps: 'all',
    onStart() {
        $element.removeClass('is-hidden')
    }
})
```
