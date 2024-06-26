## Короткий чеклист

1. Соответствие макету.
2. Проверка кода линтерами.
3. Проверка всех страниц сайта HTML-валидатором (https://html5.validator.nu/).
4. Имеется фавиконка.
5. Корректные шрифты (woff + woff2).
6. Типографированный текст. Отсутствуют битые символы.
7. Текст на сайте корректно выделяется.
8. Корректные svg-иконки.
9. Интерактивные элементы работают корректно (слайдеры, всплывающие окна, аудио и видеоплееры, табы, тесты, опросы, формы, выпадающие списки и прочее).
10. В формах реализована валидация полей.
11. Если на сайте присутствует кастомный скролл, то навигация с помощью клавиатуры должна работать корректно (Space, Shift + Space, Page Up, Page Down, Home, End, стрелки)
12. Кликабельные элементы, не ведущие на другие страницы, сделаны кнопками (`<button type="button">`).
13. Кликабельные элементы, ведущие на другие страницы (за исключением кнопок для отправки форм), сделаны ссылками с корректным href (`<a>`).
14. У всех кликабельных элементов достаточная кликабельная область.
15. Анимации на сайте работают корректно, плавно, без задержек и подвисаний.
16. На всех интерактивных элементах должен быть ховер.
17. Стресстест верстки (в местах с динамическим контентом прописать много текста с очень длинными словами и проверить не ломается ли верстка, также проверить не ломается ли при малом количестве контента).
18. Сайт не ломается блокировщиком рекламы.
19. Страницы открываются по прямой ссылке (для SPA).
20. Переходы между страницами работают корректно (для SPA).
21. Навигация с помощью истории браузера работает корректно (для SPA).
22. Проверка сайта в Windows + Chrome.
23. Проверка сайта в Windows + Firefox.
24. Проверка сайта в Windows + Edge.
25. Проверка сайта в Windows + IE 11 (опционально).
26. Проверка сайта в Windows + Yandex. (русскоязычный сегмент)
27. Проверка сайта в Windows + Opera. (русскоязычный сегмент)
28. Проверка сайта в macOS + Chrome.
29. Проверка сайта в macOS + Safari.
30. Проверка сайта в Android + Chrome (планшет).
31. Проверка сайта в iOS + Safari (планшет).
32. Проверка сайта в Android + Chrome (мобильное устройство).
33. Проверка сайта в iOS + Safari (мобильное устройство).
34. Сайт корректно адаптируется в десктопной версии (от 1025x550 до 2560x1440).
35. Сайт корректно адаптируется в мобильной и планшетной версии (от 375 до 1024).
36. Сайт корректно отображается в альбомной ориентации (мобильная и планшетная версия).
37. Указаны метатеги title, description и image (при наличии).
38. Корректная работа шеринга. Сброс кэша (если нужно):
- https://developers.facebook.com/tools/debug/
- https://cards-dev.twitter.com/validator
- https://vk.com/dev/pages.clearCache
- https://search.google.com/structured-data/testing-tool
- https://telegram.me/webpagebot
39. Корректная работа аналитики.
40. Актуальный контент (текста, ссылки, картинки, видео, аудио).
41. Формы корректно работают при автозаполнении (валидируются, отправляются)
