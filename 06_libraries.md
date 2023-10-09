# Подключение сторонних библиотек

Библиотеки подключаются с помощью npm.
При установке следует указывать ключ `--save` или `--save-dev`.

Пример:

```bash
npm install --save jquery
npm install --save-dev gulp
```

`--save` указывается для библиотек, код которых попадает в итоговую сборку (папку `build`) и будет использоваться на сайте.

`--save-dev` указывается для библиотек, которые используются только для сборки.

После установки необходимо подключить нужные файлы библиотеки:

* скрипты — в `src/js/assets.js` или `src/js/modules/[modul_name].js`
* стили — в `src/scss/styles.scss` и при необходимости дополнить файлом `src/scss/vendors/[lib_name].scss`
* изображения — в `src/img`

Полный пример, описывающий установку библиотеки fancybox:

1. Установка:

   ```bash
   npm install --save @fancyapps/ui
   ```

2. Подключение скриптов в файл `src/js/modules/[modulname].js`:

   ```js
   import { Fancybox } from "@fancyapps/ui"
   ```

3. Подключение стилей в файл `src/scss/_vendor.scss`:

   ```scss
   $fancybox-image-url: "../img";

   @import "../../node_modules/@fancyapps/ui/dist/fancybox/fancybox";
   @import "vendors/fancybox-override";
   ```

4. Копирование изображений в `src/img`:

   ```text
   cedro-template
   └── src
       ├── img
       │   ├── blank.gif
       │   ├── fancybox_loading.gif
       │   ├── fancybox_loading@2x.gif
       │   ├── fancybox_overlay.png
       │   ├── fancybox_sprite.png
       │   ├── fancybox_sprite@2x.png
       │   └── ...
       └── ...
   ```

Если библиотека отсутствует в npm, либо её нужно модифицировать, то файлы следует скачать и закинуть в папки `src/js/vendors` и `src/scss/vendors`.
