# Composer и Bitrix Framework #

С версии 18.0.5 composer используется внутри фреймворка (Bitrix) в режиме разработки. Поэтому крайне рекомендуется произвести интеграцию (мердж) с конфигурацией зависимостей разработчиков Bitrix (это понадобится при использовании, аннотации ORM классов и в целом интерфейс командной строки CLI). Данный раздел документации описывает как осуществить эту интеграцию, с учетом структуры файлов в проекте на Bitrix, принятой в команде разработки.

## Загрузка composer.json ##
Готовый файл включен в стартовый набор файлов для проектов на Bitrix, скачать можно по [ссылке](https://github.com/CedroAgency/backend_bx_starter_pack). Файл разместить по адресу
/local/composer.json.
```json
{
  "require": {
    // Будет загружен пакет с плагином для мерджа с имеющейся конфигурацией
    "wikimedia/composer-merge-plugin": "dev-master"
  },
  "require-dev": {
    /* 
        Для dev-окружения будет загружен пакет, который предотвращает установку зависимостей с известными 
        и серьезными уязвимостями
    */
    "roave/security-advisories": "dev-latest"
  },
  "config": {
    // Название и расположение папки для зависимостей
    "vendor-dir": "vendor",
    // На момент создания данного руководства этот параметр был нужен для установки плагина для мерджа
    "allow-plugins": {
      "wikimedia/composer-merge-plugin": true
    }
  },
  "extra": {
    // Файл с которым мерджимся
    "merge-plugin": {
      "require": [
        "../bitrix/composer-bx.json"
      ]
    }
  },
  "autoload": {
    // Автозагрузка классов с корневым namespace Cedro из папки /local/lib/Classes/Cedro/
    "psr-4": {
      "Cedro\\": "lib/Classes/Cedro/"
    }
  }
}
```
## Изменение .settings.php ##
По умолчанию система ожидает увидеть composer.json в папке bitrix, поэтому нужно указать путь до файла в .settings.php, чтобы его конфигурация могла быть использована в продукте.
Аккуратно редактируем файл /bitrix/.settings.php - в конец возвращаемого массива нужно добавить ключ 'composer':
```php
<?php
return array (
  // другие ключи    
  'composer' => 
  array (
    'value' => 
    array (
      'config_path' => '/local/composer.json'
    )
  ),
);
```
## Подключение автозагрузки от Composer'a в init.php ##
Подключаем сгенерированный Composer'ом скрипт для автозагрузки в /local/php_interface/init.php
```php
<?
if (file_exists("$_SERVER[DOCUMENT_ROOT]/local/vendor/autoload.php")) {
    require_once("$_SERVER[DOCUMENT_ROOT]/local/vendor/autoload.php");
}
```
## Установка Composer'а ##
В случае, если Composer установлен на сервере или хостинге глобально (можно проверить при помощи команды `composer about` в консоли), то команды можно выполнять в сокращенном виде, например, `composer install`. В случае, если `composer about` не срабатывает и нет возможности/желания/необходимости устанавливать его глобально, то загружаем phar архив по [ссылке](https://getcomposer.org/download/latest-stable/composer.phar). Размещаем файл в \local\composer.phar или \local\bin\composer.phar, в консоли делаем рабочей директорию local при помощи команды `cd` (**рабочей необходимо сделать именно ту директорию, где располагается composer.json, а не composer.phar**) и выполняем установку при помощи команды `install`:
```
php bin/composer.phar install
```
К архиву должен быть указан полный путь, как в примере. Команда выполнит генерацию автозагрузки, установку пакетов и другие действия, согласно файлу конфигурации composer.json.  
Можно изначально прописать пакеты для загрузки в файл composer.json:
```json
{
  "require": {
    "wikimedia/composer-merge-plugin": "dev-master",
    "kint-php/kint": "^4.0",
    "bcncommerce/json-stream": "^0.4.2"
  }
}
```
Если вы изменяете файл composer.json уже после команды composer install, то после каждого изменения файла нужно выполнять команду `update`:
```
php bin/composer.phar update
```
### Важно ###
После установки в папке с composer.json будет сгенерирован файл composer.lock, **не удаляйте его**, он фиксирует зависимости (и их версии) для установленных пакетов.
## Загрузка пакетов ##
Проводится командой `require`:
```
php bin/composer.phar require bcncommerce/json-stream
```
Название пакета состоит из двух частей разделённых косой чертой: названия поставщика (vendor name) и названия библиотеки. Можно найти на packagist.org, в корне репозиториев на GitHub часто лежит файл composer.json в котором есть параметр "name" с названием пакета.
## Автозагрузка своих классов и файлов ##
При помощи Composer'а можно очень удобно обставить автозагрузку своих классов и файлов, в init.php, в таком случае, останется лишь подключение /local/vendor/autoload.php
Пример блока автозагрузки:
```json
{
  "autoload": {
    "classmap": [
        "src/", 
        "lib/"
    ],
    "psr-4": {
        "Cedro\\": "lib/Classes/Cedro/",
        "Monolog\\": ["src/", "lib/"],
        "Vendor\\Namespace\\": ""
    },
    "files": [
        "lib/consts.php",
        "lib/funs.php",
        "lib/events.php"
    ]
  }
}
```
classmap - отвечает за описание классов, именование которых не соответствует стандарту PSR-4. Карта создается путем сканирования классов во всех файлах .php и .inc в указанных каталогах / файлах.
files - позволяет автозагружать файлы, которые не являются классами.
psr-4 - для подключения классов отвечающих PSR-4. Произведет сопоставление пространств имен с путями, в примере строка "Cedro\\": "lib/Classes/Cedro/" подключит классы с корневым namespace Cedro из папки /local/lib/Classes/Cedro/. Можно указать для сканирования несколько путей в массиве, как в строчке примера "Monolog\\": ["src/", "lib/"], либо более детализированное пространство как в строчке "Vendor\\Namespace\\": "".

### Важно ###
После изменения блока autoload выполните команду `dump-autoload`, она обновит только автозагрузку (update, помимо прочего, установит и обновит пакеты).
```
php bin/composer.phar dump-autoload --optimize
```
## Безопасность ##
В стартовом наборе файлов файл /local/composer.json от прямого доступа из браузера защищает /local/.htaccess c следующими директивами:
```
<Files "composer.json">
Order Allow,Deny
Deny from all
</Files>
```
Это необходимо для того, чтобы злоумышленник не мог просмотреть установленные пакеты и их версии.
Аналогично, в целях безопасности, следует закрыть папку /local/vendor/ (например, положить в неё .htaccess с директивой `Deny from all`) и файл composer.phar, если Composer будет использоваться локально и данный архив будет сохраняться на сервере после установки зависимостей.
