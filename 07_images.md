# Работа с изображениями

Изображения следует хранить в папке `src/img`.
При запуске задачи `img` файлы из папки `src/img` копируются в `build/img`.

```text
cedro-template
├── build
│   └── img
└── src
    └── img
```

Для оптимизации изображений можно использовать задачу `imagesMin`.


## Работа с SVG-спрайтами

Принцип работы с SVG-спрайтами:

1. Получаем векторные иконки в формате `.svg` (либо заранее подготовленные, либо экспортируем с помощью редактора).
   Сохраняем в папку `src/img/sprite`:

   ```text
   cedro-template
   └── src
       └── img
           └── sprite
               └── phone.svg
   ```

2. Запускаем задачу `sprite` (если уже запущен `gulp watch` или `gulp`, то данный шаг можно пропустить):

   ```bash
   gulp sprite
   ```

3. Генератор оптимизирует и объединяет иконки в один спрайт:

   ```text
   cedro-template
   └── build
       └── img
           └── sprite.svg
   ```

   В сборке содержится Pug-миксин для подключения SVG-спрайтов.<br>
   `src\pug\components\utils\icn.pug`:

   ```jade
    mixin icn(name, width, height)
       svg.icn(
            width=width
            height=height
            aria-hidden="true"
            role="img"
        )&attributes(attributes)
            use(href="#" + name)
   ```

4. Подключаем иконку в Pug:

   ```jade
       a,phone(href="tel:+71234567890")
           +icn('icn-phone')
           | +7 (123) 456-78-90
   ```

   При необходимости иконку можно стилизовать:

   ```scss
   .phone {
        svg {
            width: 30px;
            height: 30px;
            fill: $color-black;
        }
   }
   ```

   Если цвет заливки или обводки не удается изменить с помощью CSS, то необходимо открыть SVG-файл иконки в редакторе и удалить соответствующие атрибуты (`fill`, `stroke`) из кода.

## Избавляемся от обрезанных краев SVG-иконок

1. Общий пример:

    Шаг 1: исходная иконка без полей
    ```html
    <svg xmlns="http://www.w3.org/2000/svg" width="{width}" height="{height}" viewBox="0 0 {width} {height}">
        <path d="..."/>
        <path d="..."/>
        <path d="..."/>
    </svg>
    ```

    Шаг 2: добавляем поле размером {padding}
    ```html
    <svg xmlns="http://www.w3.org/2000/svg" width="{width + 2 * padding}" height="{height + 2 * padding}" viewBox="0 0 {width + 2 * padding} {height + 2 * padding}">
        <g transform="translate({padding} {padding})">
            <path d="..."/>
            <path d="..."/>
            <path d="..."/>
        </g>
    </svg>
    ```

    Шаг 3: запускаем optimize:svg и получаем иконку без лишних трансформаций
    ```html
    <svg xmlns="http://www.w3.org/2000/svg" width="{width + 2 * padding}" height="{height + 2 * padding}" viewBox="0 0 {width + 2 * padding} {height + 2 * padding}">
        <path d="..."/>
        <path d="..."/>
        <path d="..."/>
    </svg>
    ```

2. Конкретный пример:

    Шаг 1: исходная иконка без полей
    ```html
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="30" viewBox="0 0 20 30">
        <path d="..."/>
        <path d="..."/>
        <path d="..."/>
    </svg>
    ```

    Шаг 2: добавляем поле размером 1px
    ```html
    <svg xmlns="http://www.w3.org/2000/svg" width="22" height="32" viewBox="0 0 22 32">
        <g transform="translate(1 1)">
            <path d="..."/>
            <path d="..."/>
            <path d="..."/>
        </g>
    </svg>
    ```

    Шаг 3: запускаем optimize:svg и получаем иконку без лишних трансформаций
    ```html
    <svg xmlns="http://www.w3.org/2000/svg" width="22" height="32" viewBox="0 0 22 32">
        <path d="..."/>
        <path d="..."/>
        <path d="..."/>
    </svg>
    ```
