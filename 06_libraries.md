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

* скрипты — в `assets/js/vendor.js` или `assets/js/main.js`.
* стили — в `assets/scss/_vendor.scss`.
* изображения — в `assets/images`.
* любые другие файлы — в `assets/resources`.

Полный пример, описывающий установку библиотеки fancybox:

1. Установка:

   ```bash
   npm install --save fancybox
   ```

2. Подключение скриптов в файл `assets/js/vendor.js`:

   ```js
   import 'fancybox';
   ```

3. Подключение стилей в файл `assets/scss/_vendor.scss`:

   ```scss
   $fancybox-image-url: "../images";

   @import "../../node_modules/fancybox/dist/scss/jquery.fancybox";
   ```

4. Копирование изображений в `assets/images`:

   ```text
   cedro-template
   └── assets
       ├── images
       │   ├── blank.gif
       │   ├── fancybox_loading.gif
       │   ├── fancybox_loading@2x.gif
       │   ├── fancybox_overlay.png
       │   ├── fancybox_sprite.png
       │   ├── fancybox_sprite@2x.png
       │   └── ...
       └── ...
   ```

Если библиотека отсутствует в npm, либо её нужно модифицировать, то файлы следует скачать и закинуть в папки `assets/js/vendor` и `assets/scss/vendor`.
