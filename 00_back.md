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
6. Используем инфоблоки везде, где есть однотипный контент - слайдеры, новости, повторяющиеся преимущества. В дальнейшем это ускорит наполнение и поддержку сайта.
7. Используем включаемые области во всех остальных случаях. Желательно для одного и то же номера телефона использовать одну и ту же область на всем сайте. Во включаемых областях email и телефоном не должно быть ссылок. Используем конструкции:
```
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
```
$APPLICATION->AddHeadScript(SITE_TEMPLATE_PATH."/js/file.js" );
$APPLICATION->SetAdditionalCSS(SITE_TEMPLATE_PATH."/js/file.css", true);

Подключение мета тегов или сторонних файлов
$APPLICATION->AddHeadString("name='<meta name='yandex-verification' content='62be9ea1' />'");

В шаблоне
$this->addExternalCss("/bitrix/css/main/bootstrap.css");
$this->addExternalJS("/bitrix/js/main/bootstrap.js");
```
9. Если bootstrap не нужен, не забудь вырезать его из шаблонов каталога, корзины, поиска
