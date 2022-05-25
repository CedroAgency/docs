## Проверка на соответствие макету

Результат верстки должен соответствовать макету.

Проверка осуществляется с помощью расширения [PerfectPixel](https://chrome.google.com/webstore/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi?hl=ru), в браузере Chrome под ОС Windows, Linux или Mac.

Допустимы незначительные отличия, связанные с:
- различием в рендеринге шрифтов
- ошибками в макете (различные отступы или размеры у однотипных элементов, погрешности в цветах)
- заменой контента (текст, изображения, видео)

Иные отличия недопустимы.

Если верстка по тем или иным причинам расходится с макетом, то об этом следует сообщить менеджеру проекта.

## Проверка кода линтером
*В планах
## Проверка кода валидатором

Следует проверять код [валидатором](https://validator.w3.org/unicorn/).

## Проверка фавиконки

На сайте должна быть фавиконка.

При отсутствии фавиконки следует запросить ее у менеджера проекта.

## Шрифты

На сайте должны использоваться корректные шрифты.

Обязательный формат - `woff`.
Опциональный формат - `woff2`.

Недопустимо использовать `woff2`, без использования `woff`.

Допустимо использовать только `woff`.

Крайне желательно использовать и `woff` и `woff2`.

В используемом шрифте не должно быть битых символов.

## Проверка на типографирование

Текст на сайте должен быть типографирован, т.е. прогнан через [Типограф](https://www.artlebedev.ru/typograf/). Если в тексте присутствуют лишние и битые символы, от них необходимо избавиться.

## Проверка выделения текста

Содержимое текстовых блоков должно корректно выделяться.

## Проверка иконок и изображений

Иконки на сайте должны быть сделаны с помощью SVG, либо PNG + @2x PNG (если иконка имеет сложные растровые эффекты, SVG отсутствует или невозможно экспортировать иконку в формате SVG).

Для контентных изображений должна быть указана @2x-версия.

SVG-иконки должны иметь внутренние отступы, чтобы избежать обрезанных краев в разных браузерах.

## Проверка интерактивных элементов

Следует проверять корректность работы интерактивных элементов:

* Слайдеры
* Всплывающие окна
* Аудио и видеоплееры
* Табы
* Тесты и опросы
* Элементы форм
* Валидация полей
* Отправка форм
* Прочие элементы, обладающие сложной логикой и неуказанные в данном списке

## Проверка свайпа и drag'n'drop

Если в каком либо блоке сайта допустимо и логично реагировать на свайп или drag'n'drop, и это поведение не реализовано, то об этом следует сообщить менеджеру проекта и разработчику.

Свайп можно использоват в мобильной и планшетной версии для перехода между слайдами или для постраничной навигации (если таковая имеется).

Drag'n'drop можно использовать в слайдерах и элементах, поведение которых предполагает (или допускает) перетаскивание.

## Проверка навигации по сайту с помощью клавиатуры

На сайте должна корректно работать навигация с помощью клавиатуры. В частности следует проверять работу следующих клавиш (и комбинаций клавиш):

* Стрелки влево, вправо, вверх и вниз
* Tab
* Shift + Tab
* Enter
* Esc
* Пробел
* Shift + Пробел
* Page Up
* Page Down
* Home
* End

## Проверка кнопок

Кнопки, клик по которым не ведет на другую страницу, а лишь выполняет какое-либо действие, должны быть сделаны тегом `<button>`.

У тега `<button>` должен быть указан атрибут `type`.

## Проверка ссылок

Ссылки - интерактивные элементы, при клике на которые происходит переход на другую страницу или внешний ресурс.

Ссылки-якоря - интерактивные элементы, при клике на которые происходит скролл к нужному месту страницы.

Все ссылки должны быть сделаны тегом `<a>`.

У всех ссылок должен быть указан атрибут `href`.

У внутренних ссылок атрибут `href` должен начинаться с `/`.

У внешних ссылок должен быть указан атрибут `target="_blank"`.

У ссылок-якорей в атрибуте `href` должен быть указан хеш.

Ссылки должны быть корректными и вести на соответствующие страницы.

## Проверка кликабельной области элементов

Если у кнопки или отдельностоящей ссылки нет явно ограниченной кликабельной области, то за такую следует принять размер элемента плюс поля 5-15px.

Кликабельная область должна иметь размер минимум 20-30px по высоте и ширине (если нет явной границы).

Содержимое кнопки или ссылки должно быть по центру кликабельной области.

Для ссылок в тексте размер кликабельной области не контролируется.

## Проверка анимаций

Любая анимация на сайте (переходы, смена слайдов, ховеры) должна работать плавно, без рывков и мерцаний.

Не должно быть зависаний или долгих пауз во время анимации.

Анимация однотипных элементов должна быть одинаковой на всех блоках и страницах.

На всех интерактивных элементах должен быть плавный ховер.

## Проверка верстки стресстестом

**TODO**

## Проверка сайта с включенным блокировщиком рекламы

Сайт должен проверяться с включенным блокировщиком рекламы.

Элементы сайта не должны блокироваться.

## Проверка переходов на страницы по прямой ссылке

Следует проверять корректность загрузки всех страниц сайта.

Также следует проверять корректность загрузки страницы с дополнительными GET-параметрами и хешем.
Заданные GET-параметры и хеш при этом не должны пропадать.

## Проверка переходов между страницами

Следует проверять корректность перехода между всеми страницами сайта.

Например, если на сайте несколько страниц:

* `/a`
* `/b`
* `/c`

То следует проверять переходы:

* `/a` => `/a`
* `/a` => `/b`
* `/a` => `/c`
* `/b` => `/a`
* `/b` => `/b`
* `/b` => `/c`
* `/c` => `/a`
* `/c` => `/b`
* `/c` => `/c`

Если какой-либо переход невозможен, то его следует игнорировать.

Также следует проверять корректность перехода по несуществующему адресу.
На сайте должна быть предусмотрена страница с 404 ошибкой, либо должен срабатывать редирект на главную.

## Проверка навигации с помощью истории браузера

На сайте должны корректно работать переходы между страницами с помощью истории браузера (стрелки влево и вправо рядом с адресной строкой).

## Кроссбраузерность и кроссплатформенность

На проектах поддерживаются последние версии браузеров (если не указано иного).

Сайт следует проверять в следующих системах:

* Windows
    * Chrome
    * Firefox
    * Edge
    * IE 11
    * Yandex (русскоязычный сегмент)
    * Opera (русскоязычный сегмент)
* macOS
    * Safari
    * Chrome
* Android
    * Chrome
* iOS
    * Safari
    * Chrome

## Проверка адаптивности (десктоп)

Основные размеры мониторов:

* 2560x1440
* 2560x1080
* 1920x1200
* 1920x1080
* 1650x1050
* 1600x900
* 1440x900
* 1366x768
* 1280x1024
* 1280x720

При проверке адаптивности следует проверять не только указанные размеры, но также и промежуточные.
Причина в том, что размер окна сайта не равен разрешению монитора (за исключением полноэкранного режима).
Часть пространства занимает системная панель, часть - верхняя панель браузера.
К тому же иногда пользователи открывают окно браузера не на весь экран.

Проверка осуществляется в панели разработчика в режиме `Responsive` и начинается с наибольшего экрана (2560x1440).

Минимальные размеры до которых стоит проверять адаптивность десктопной версии - 1025px по ширине, и 550px по высоте.

Проверка адаптивности проходит по следующему алгоритму:

1. Задается размер окна 2560x1440.
2. Путем перетаскивания и постепенного уменьшения высоты (до минимальной - 550px) проверяется корректность отображения сайта.
3. Далее ширина окна немного уменьшается (на 25-50px).
4. Пункты 2 и 3 повторяются до тех пор, пока ширина окна не достигнет минимальной - 1025px.

## Проверка адаптивности (планшеты и мобильные устройства)

Для начала сайт нужно проверить в мобильном эмуляторе браузера.

Как и в случае с десктопной версией проверяются не только размеры, соответствующие разрешению экрана, но также и промежуточные.

Минимальная ширина экрана до которой следует проверять адаптивность - 320px.

Проверять следует как портретную, так и альбомную ориентацию.

В альбомной ориентации размер элементов не должен сильно отличаться от портретной.
Не должно быть такого, что в альбомной ориентации элементы слишком мелкие или большие.

Обязательно проверять сайт на реальных устройствах (либо в [BrowserStack](https://www.browserstack.com/)):

* Android
    * Любое мобильное устройство и планшет с актуальной версией системы (6+)
        * Chrome
* iOS
    * iPhone SE/7/8/X и iPad Mini/Air/Pro
        * Safari
        * Chrome

При проверке сайта на реальных устройствах страница должна корректно отображаться и скроллиться.

## Проверка метатегов

На сайте должны быть указаны метатеги (`title`, `description`, `image`).

Если сайт многостраничный, то метатеги должны быть указаны на каждой странице.

Если сайт одностраничный и использует `share.php` для шаринга, то метатеги должны быть указаны и в `share.php` и в Pug (HTML).

## Проверка шеринга

На сайте должен работать шеринг (при наличии).

Если сайт многостраничный, то должна шариться ссылка на страницу с основными параметрами (при наличии таковых).

Если сайт многостраничный, то должна шариться ссылка на `share.php` с требуемыми параметрами.

При шаринге в ссылку не должны попасть лишние параметры (например, UTM-метки). 

Проверка и отладка шаринга осуществляется с помощью следующих инструментов:

* https://developers.facebook.com/tools/debug/
* https://cards-dev.twitter.com/validator
* https://vk.com/dev/pages.clearCache
* https://search.google.com/structured-data/testing-tool
* https://telegram.me/webpagebot

При шаринге сайта в соц. сети должны корректно отобразиться:

* Заголовок (соответствующий заданному метатегу, необрезанный, без искажений кодировки и битых символов)
* Описание (соответствующее заданному метатегу, необрезанное, без искажений кодировки и битых символов)
* Изображение (соответствующее заданному метатегу)

Ссылка шаринга должна вести на ту же страницу, которую шарили, либо на страницу, соответствующую заданной логике.
В случае использования `share.php` ссылка должна перенаправлять на нужную страницу.

Если расшариваемая страница недоступна по прямой ссылке (т.е. переход на нее происходит по внутренней логике сайта), то следует шарить главную страницу.

## Проверка аналитики

Для проверки аналитики используется расширение [Google Analytics Debugger](https://chrome.google.com/webstore/detail/google-analytics-debugger/jnkmfdileelhofjcijamephohjechhna).

После установки в панели расширений появится иконка GA Debug (в виде письма).

На проверяемом сайте следует открыть панель разработчика и включить GA Debug. На иконке появится надпись `ON`.

После чего страница перезагрузится и в консоли появится множество сообщений от расширения.

Избавиться от лишних сообщений можно, если вписать в поле `Filter` консоли значение `Running command` (все сообщения от данного расширения помещается данным префиксом).
При фильтрации сообщений консоли следует быть внимательным, так как фильтруются абсолютно все сообщения, в том числе ошибки и собственные вызовы `console.log`.

После этого следует поочередно проверить указанные в ТЗ события.

## Проверка контента

На сайте должен быть актуальный контент:

* Текст
* Ссылки
* Изображения
* Видео
* Аудио

Запросить актуальный контент можно у менеджера проекта.

При наличии ошибок в тексте (орфографических, пунктуационных, логических) следует сообщить об этом менеджеру проекта.

При наличии недоступных ресурсов (недоступные изображения, видео или аудио, 404 ошибки) следует сообщить об этом менеджеру проекта.

При выявлении несоответствия контента (перепутан текст, изображение, видео или аудио) следует сообщить об этом менеджеру проекта.

## Проверка размера загружаемых ресурсов

На сайте не должно быть чрезмерно больших файлов.

Размер изображений должен соответствовать размеру на сайте (например, для элемента размером 300x300 не должно использоваться изображение размером 2000x2000).

Не должно быть мегабайтных JPG. Такие файлы следует оптимизировать вручную с ограничением максимального качества.

Размер видео не должен быть больше 100 мегабайт (за исключением продолжительных видео и адаптивного стриминга).

## Проверка производительности сайта

**TODO**