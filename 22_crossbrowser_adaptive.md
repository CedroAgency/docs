# Кроссбраузерность

Исходя из нашей статистики, основная часть сайтов должна поддерживаться в последних версиях таких браузеров, как:

## Десктоп

* Chrome
* Safari
* Firefox
* Internet Explorer 11(опционально)
* Edge
* Yandex Browser (русскоязычный сегмент)

## Мобильные устройства и планшеты

* Chrome
* Safari

В определенных случаях данный список может меняться.

# Адаптивность

Для основной части сайтов используются два базовых брейкпоинта (в SCSS созданы для этого миксины mobile и desktop):

* с 360 до 1024 (мобильные устройства и планшеты)
* с 1025 и выше (десктоп)

Остальные брейкпоинты добавляются по мере надобности, либо в зависимости от предоставленных макетов.

Сайт должен быть полностю адаптирован по ширине начиная от 360 и по высоте начиная от 550 пикселей.
