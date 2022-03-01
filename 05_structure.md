# Структура папок и файлов

```text
cedro-template
├── assets
│   ├── images
│   │   └── sprites
│   │       ├── png
│   │       │   └── .keep
│   │       └── svg
│   │           └── .keep
│   ├── js
│   │   ├── vendor
│   │   │   └── .keep
│   │   ├── main.js
│   │   └── vendor.js
│   ├── pug
│   │   ├── mixins
│   │   │   └── svg.pug
│   │   ├── base.pug
│   │   └── mixins.pug
│   ├── resources
│   │   └── fonts
│   │       └── .keep
│   ├── scss
│   │   ├── functions
│   │   │   └── _sprites.scss
│   │   ├── mixins
│   │   │   ├── _clearfix.scss
│   │   │   ├── _retina.scss
│   │   │   ├── _sprites.scss
│   │   │   ├── _triangle.scss
│   │   │   └── _visually-hidden.scss
│   │   ├── vendor
│   │   │   └── .keep
│   │   ├── _base.scss
│   │   ├── _fonts.scss
│   │   ├── _functions.scss
│   │   ├── _mixins.scss
│   │   ├── _sprites.hbs
│   │   ├── _sprites.scss
│   │   ├── _variables.scss
│   │   ├── _vendor.scss
│   │   └── main.scss
│   └── index.pug
├── .babelrc
├── .editorconfig
├── .eslintignore
├── .eslintrc
├── .gitignore
├── .npmrc
├── .pug-lintrc.json
├── .stylelintignore
├── .stylelintrc
├── gulpfile.js
├── package.json
├── README.md
└── webpack.config.js
```

## `assets`

В папке `assets` хранятся исходные файлы проекта.

## `assets/images`

Папка `images` предназначена для хранения изображений.
При сборке файлы из данной папки попадают в `build/images`.

## `assets/images/sprites`

Папка `assets/images/sprites` предназначена для хранения векторных (SVG) и растровых (PNG) иконок.

## `assets/images/sprites/png`

Папка `assets/images/sprites/png` предназначена для хранения растровых иконок.
При сборке файлы из данной папки объединяются в два спрайта: `build/images/sprites.png` и `build/images/sprites@2x.png`.

## `assets/images/sprites/svg`

Папка `assets/images/sprites/svg` предназначена для хранения векторных иконок.
При сборке файлы из данной папки объединяются в один спрайт: `build/images/sprites.svg`.

## `assets/js`

Папка `assets/js` предназначена для хранения скриптов.

## `assets/js/vendor`

Папка `assets/js/vendor` предназначена для хранения скриптов сторонних библиотек, которых нет в репозитории npm.

## `assets/js/main.js`

Файл `assets/js/main.js` предназначен для хранения основной логики сайта.
При сборке данный файл попадает в `build/js`.

## `assets/js/vendor.js`

Файл `assets/js/vendor.js` предназначен для подключения сторонних библиотек.

При сборке данный файл попадет в `build/js`.

## `assets/pug`

Папка `assets/pug` предназначена для хранения шаблонов.

## `assets/pug/mixins`

Папка `assets/pug/mixins` предназначена для хранения Pug-миксин.

## `assets/pug/base.pug`

В файле `assets/pug/base.pug` хранится базовый шаблон страниц сайта.

## `assets/pug/mixins.pug`

Файл `assets/pug/mixins.pug` предназначен для подключения Pug-миксин из папки `assets/pug/mixins`.

## `assets/resources`

Папка `assets/resources` предназначена для хранения различных файлов проекта.
При сборке файлы из данной папки попадают в `build`.

## `assets/resources/fonts`

Папка `assets/resources/fonts` предназначена для хранения шрифтов.
При сборке файлы из данной папки попадают в `build/fonts`.

## `assets/scss`

Папка `assets/scss` предназначена для хранения стилей.

## `assets/scss/functions`

Папка `assets/scss/functions` предназначена для хранения SCSS-функций.

## `assets/scss/mixins`

Папка `assets/scss/mixins` предназначена для хранения SCSS-миксин.

## `assets/scss/vendor`

Папка `assets/scss/vendor` предназначена для хранения стилей сторонних библиотек, которых нет в репозитории npm.

## `assets/scss/_base.scss`

Файл `assets/scss/_base.scss` предназначен для хранения базовых стилей.

## `assets/scss/_fonts.scss`

Файл `assets/scss/_fonts.scss` предназначен для подключения шрифтов.

## `assets/scss/_functions.scss`

Файл `assets/scss/_functions.scss` предназначен для подключения функций из папки `assets/scss/functions`.

## `assets/scss/_mixins.scss`

Файл `assets/scss/_mixins.scss` предназначен для подключения миксин из папки `assets/scss/mixins`.

## `assets/scss/_sprites.hbs`

`assets/scss/_sprites.hbs` — шаблон, на основе которого генерируется содержимое файла `assets/scss/_sprites.scss`.

## `assets/scss/_sprites.scss`

Файл `assets/scss/_sprites.scss` предназначен для работы с PNG-спрайтами.
Содержимое данного файла автоматически генерируется на основе шаблона `assets/scss/_sprites.hbs` и иконок из папки `assets/images/sprites/png`.

## `assets/scss/_variables.scss`

Файл `assets/scss/_variables.scss` предназначен для хранения SCSS-переменных.

## `assets/scss/_vendor.scss`

Файл `assets/scss/_vendor.scss` предназначен для подключения стилей сторонних библиотек.

## `assets/scss/main.scss`

Файл `assets/scss/main.scss` предназначен для хранения основных стилей сайта.
При сборке данный файл преобразуется в CSS и сохраняется в `build/css` вместе с файлом `main.css.map`.

## `assets/index.pug`

`assets/index.pug` — шаблон главной страницы.
При сборке все Pug-файлы из папки `assets` преобразуются в HTML и сохраняются в `build`.

## `.babelrc`

`.babelrc` — файл настроек JavaScript-транспайлера Babel.

## `.editorconfig`

`.editorconfig` — файл настроек редактора.

## `.eslintignore`

`.eslintignore` — файл настроек ESLint для игнорирования файлов.

## `.eslintrc`

`.eslintrc` — файл настроек ESLint.

## `.gitignore`

`.gitignore` — файл настроек Git для игнорирования файлов.

## `.npmrc`

`.npmrc` — файл настроек npm.

## `.pug-lintrc.json`

`.pug-lintrc.json` — файл настроек pug-lint.

## `.stylelintignore`

`.stylelintignore` — файл настроек stylelint для игнорирования файлов.

## `.stylelintrc`

`.stylelintrc` — файл настроек stylelint.

## `gulpfile.js`

`gulpfile.js` — основной файл сборки, содержащий Gulp-задачи.

## `package.json`

`package.json` — файл, содержащий базовую информацию о проекте и список требуемых библиотек.

## `README.md`

`README.md` — описание проекта.

## `webpack.config.js`

`webpack.config.js` — файл настроек webpack.
