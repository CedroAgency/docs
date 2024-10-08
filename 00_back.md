# Общие требования к разработке

1. Избегаем инлайновых стилей и скриптов. Везде где это возможно. Чтобы это избежать может помочь:
```
<?$APPLICATION->ShowViewContent('wrapp_class');?>
<?$this->SetViewTarget('wrapp_class');?>
contact-container
<?$this->EndViewTarget();?> 
```
Таким способом можно вставлять классы, куски кода, компоненты

2. Не вызываем компоненты в компонентах. Сайт должен корректно отображаться при включенном кэшировании
3. НЕ ИСПОЛЬЗУЕМ jquery. Ну правда, хватит уже дёргать старичка
4. Используем catalog.item. Он сложен и запутанный, но зато сделав его 1 раз во всех компонентах типа catalog.section у вас будет красота автоматически.
5. Стараемся вырезать битрикс по минимуму, чтобы при необходимости можно было быстро вывести доп.свойства (и это мог сделать клиент сам), добавить торговые предложения, отображение скидок и т.д.
6. Используем инфо- и highload-блоки везде, где есть однотипный контент - слайдеры, новости, повторяющиеся преимущества. В дальнейшем это ускорит наполнение и поддержку сайта.
7. Используем включаемые области во всех остальных случаях. Желательно для одного и то же номера телефона использовать одну и ту же область на всем сайте. Во включаемых областях email и телефоном не должно быть ссылок. Используем конструкции:
```php
    Для телефона:
    <a href="tel:<?echo preg_replace('/[^+0-9]/', '', $APPLICATION->GetFileContent($_SERVER['DOCUMENT_ROOT'].'/local/include_areas/template/phone.php')); ?>">
        <?$APPLICATION->IncludeFile($APPLICATION->GetTemplatePath('/local/include_areas/template/phone.php'),Array(),Array('MODE'=>'html'));?>
    </a>
    
    Для email:
    <a href="mailto:<?$APPLICATION->GetFileContent($_SERVER['DOCUMENT_ROOT'].'/local/include_areas/email.php')?>">
        <?$APPLICATION->IncludeFile($APPLICATION->GetTemplatePath('/local/include_areas/email.php'), [], ['MODE' => 'html']); ?>
    </a>
```
8. Подключение стилей и js производим с помощью функций битры
```php
$APPLICATION->AddHeadScript(SITE_TEMPLATE_PATH."/js/file.js" );
$APPLICATION->SetAdditionalCSS(SITE_TEMPLATE_PATH."/js/file.css", true);

Подключение мета тегов или сторонних файлов
$APPLICATION->AddHeadString("name='<meta name='yandex-verification' content='62be9ea1' />'");

В шаблоне
$this->addExternalCss("/bitrix/css/main/bootstrap.css");
$this->addExternalJS("/bitrix/js/main/bootstrap.js");
```
9. Если bootstrap не нужен, не забудь вырезать его из шаблонов каталога, корзины, поиска

10. Для инфоблоков необходимо использовать предварительное seo наполнение для title и description: 
```
Для каталога интернет магазина
Название сайта || Название товара купить в Название города

Для блога
Название сайта || Новости ||
```

11. Не изспользуйте слова reklama, ad и их синонимы для названия файлов / разделов сайта / методов js - их не любит adBlock

# Компоненты битрикс

1. Как было уже сказано выше, используем инфоблоки где есть однотипный контент
2. Должен быть доступен режим правки на страницах. Он может "ломать" страницу, когда включен, но должно быть можно выбрать и отредактировать элементы, проскроллить страницу до конца, а после отключения режима правки всё должно вернуться на круги своя
3. Подумайте, нужно ли обернуть код в самописный компонент. Компонент может быть без параметров, но, возможно, так будет удобнее и безопаснее для редактирования
4. При открытии страницы в визуальном редакторе и сохранении её, она не должна ломаться. Для этого:
   * a. Все данные из инфоблоков оборачиваем в компоненты, подходят стандартные, например news.list
   * Шаблон компонента содержит не только foreach со списком, но и всю "обёртку", чтобы на странице при редактировании было минимум html кода
   * Стараемся сохранить <?=$this->GetEditAreaId($arItem['ID']);?>
   * Не забываем проверять на пустоту поля инфоблоков
   * Если страница вся состоит из  html кода (например форма лк), а создавать компонент нет времени - лучше  вынести форму во включаемую область и подключить просто через require. В этом случае клиенту сложнее сломать что-то через редактор, а даже если сломает, то сам файл с формой останется в безопасности. Такие включаемые области лучше хранить в шаблоне или в отдельном папке в include_areas

```
Бэкер, всегда помни - клиент полезет везде, куда ему будет открыт доступ и обязательно все сломает. 
А виноват и переделывать будешь ты. Поэтому защиту от дурака надо внедрять по максимуму
```
