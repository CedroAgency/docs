# Работа с изображениями

Изображения следует хранить в папке `src/images`.
При запуске задачи `images` файлы из папки `src/images` копируются в `build/images`.

```text
cedro-template
├── build
│   └── images
└── src
    └── images
```

Для оптимизации изображений можно использовать задачу `optimize:images`.

> `optimize:images` оптимизирует только исходные файлы из папки `src/images`!

Предварительно оптимизированные изображения рекомендуется хранить в папке `src/assets/images`.
В таком случае при запуске задачи `optimize:images` данные файлы не будут затронуты.

```text
cedro-template
└── src
    └── assets
        └── images
```

## Работа с SVG-спрайтами

Принцип работы с SVG-спрайтами:

1. Получаем векторные иконки в формате `.svg` (либо заранее подготовленные, либо экспортируем с помощью редактора).
   Сохраняем в папку `src/images/sprites/svg`:

   ```text
   cedro-template
   └── src
       └── images
           └── sprites
               └── svg
                   └── phone.svg
   ```

2. Запускаем задачу `sprites:svg` (если уже запущен `gulp watch` или `gulp`, то данный шаг можно пропустить):

   ```bash
   gulp sprites:svg
   ```

3. Генератор оптимизирует и объединяет иконки в один спрайт:

   ```text
   cedro-template
   └── build
       └── images
           └── sprites.svg
   ```

   В сборке содержится Pug-миксин для подключения SVG-спрайтов.<br>
   `src/pug/mixins/svg.pug`:

   ```jade
    mixin svg(name)
       svg&attributes(attributes)
           use(xlink:href=`${baseDir}images/sprites.svg#${name}`)
   ```

4. Подключаем иконку в Pug:

   ```jade
   footer
       a(href="tel:+71234567890")
           +svg("phone")
           | +7 (123) 456-78-90
   ```

   При необходимости иконку можно стилизовать:

   ```scss
   footer {
       a {
           svg {
               display: inline-block;
               vertical-align: middle;
               width: 30px;
               height: 30px;
               fill: $color-black;
           }
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
