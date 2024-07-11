# Положение по работе с микроразметкой

Для того чтобы удовлетворять требованиям по SEO - наши проекты должны содержать в себе готовую микроразметку.

1. В проектах по умолчанию используем микроразметку [schema.org](https://schema.org/)
2. Информация размечаемая по-умолчанию:

*[Инофрмация об организации](http://schema.org/Organization)
```html
<div itemscope itemtype="http://schema.org/Organization">
  <span itemprop="name">Яндекс</span>
  Контакты:
  <div itemprop="address" itemscope itemtype="http://schema.org/PostalAddress">
    Адрес:
    <span itemprop="streetAddress">Льва Толстого, 16</span>
    <span itemprop="postalCode">119021</span>
    <span itemprop="addressLocality">Москва</span>,
  </div>
  Телефон:<span itemprop="telephone">+7 495 739–70–00</span>,
  Факс:<span itemprop="faxNumber">+7 495 739–70–70</span>,
  Электронная почта: <span itemprop="email">pr@yandex-team.ru</span>
</div>
```
*[Хлебные крошки](https://schema.org/BreadcrumbList)
```html
<ol itemscope itemtype="https://schema.org/BreadcrumbList">
  <li itemprop="itemListElement" itemscope
      itemtype="https://schema.org/ListItem">
    <a itemprop="item" href="https://example.com/dresses">
    <span itemprop="name">Dresses</span></a>
    <meta itemprop="position" content="1" />
  </li>
  <li itemprop="itemListElement" itemscope
      itemtype="https://schema.org/ListItem">
    <a itemprop="item" href="https://example.com/dresses/real">
    <span itemprop="name">Real Dresses</span></a>
    <meta itemprop="position" content="2" />
  </li>
</ol>
```

*[Товар](http://schema.org/Product)

*[Торговое предложение](http://schema.org/Offer)
```html
<div itemscope itemtype="http://schema.org/Product">
  <div itemprop="name"><h1>Кровать Мелисса с мягкой спинкой</h1></div>
  <a itemprop="image" href=​"products_pictures/large_krovat-mellisa-smyagkoispink.jpg">
    <img src=​"products_pictures/medium_krovat-mellisa-smyagkoispink.jpg" title="Кровать Мелисса с мягкой спинкой">
  </a>
  <div itemprop="offers" itemscope itemtype="http://schema.org/Offer">
    <meta itemprop="price" content="7150.00">
    <meta itemprop="priceCurrency" content="RUB">
    <div>В наличии</div>
    <link itemprop="availability" href="http://schema.org/InStock">
  </div>
  <div itemprop="description">Цена указана за кровать Мелисса с мягкой спинкой; размером спального места 900х2000 мм. Подушки у спинки кровати изготовляются из искусственной кожи. В комплектацию входит ортопедическое основание на ножках.</div>
</div>
``` 
3. Корректность разметки можно проверять в [Валидаторе](https://validator.schema.org/)
