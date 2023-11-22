# Работа со скриптами

> При работе со скриптами **важно** придерживаться установленных [правил по оформлению кода](18_codestyle-javascript.md).

Скрипты размещаются в папке `src/js`:

```text
cedro-template
└── src
    └── js
        ├── libs
        │   └── .keep
        ├── assets.js
        └── main.js
```

За сборку и преобразование JS отвечает задача:

```bash
gulp scripts
```

После выполнения команды в папке `build/js` появятся файлы `main.js` и `assets.js`:

```text
cedro-template
└── build
    └── js
        ├── assets.js
        └── main.js
```

## Правила написания кода

### Короткие именна переменных

Не следует сокращать имена переменных.

**Неправильно:**

```js
const s = '13px'
let blockW = '40px'
```

**Правильно:**

```js
const fontSize = '13px'
let blockWidth = '40px'
```

Исключением являются устоявщиеся и общепонятные сокращения. Такие как `i` - для index, `e` для event, `el` для element и т.п.



## Использование линтера

В сборку интегрирован линтер [ESLint](http://eslint.org/).
Файл настроек — `.eslintrc`.
Данный линтер позволяет поддерживать JavaScript-код в соответствии с заданным регламентом.

Проверка осуществляется с помощью задачи `lint:js`:

```bash
npm run lint:js
```

Пример использования:

```js
var $form = $('.js-form')
$form.on("submit", function () {
  $.post('ajax.php', function (data) {
    $(".result").html(data);
  })
})
```

Результаты проверки:

```text
  1:1   error    Expected blank line after variable declarations    newline-after-var
  1:1   error    Unexpected var, use let or const instead           no-var
  1:23  error    Missing semicolon                                  semi
  2:10  error    Strings must use singlequote                       quotes
  2:20  error    Unexpected function expression                     prefer-arrow-callback
  2:20  warning  Unexpected unnamed function                        func-names
  3:1   error    Expected indentation of 1 tab but found 2 spaces   indent
  3:22  warning  Unexpected unnamed function                        func-names
  3:22  error    Unexpected function expression                     prefer-arrow-callback
  4:1   error    Expected indentation of 2 tabs but found 4 spaces  indent
  4:7   error    Strings must use singlequote                       quotes
  5:1   error    Expected indentation of 1 tab but found 2 spaces   indent
  5:5   error    Missing semicolon                                  semi
  6:3   error    Missing semicolon                                  semi

✖ 14 problems (12 errors, 2 warnings)
  12 errors, 0 warnings potentially fixable with the `--fix` option.
```

ESlint сообщает о 14 найденных ошибках, причем большая часть из них может быть исправлена автоматически.
За это отвечает ключ `--fix`, который можно указать при запуске задачи `lint:js`:

```bash
nmp run lint:js --fix
```
