# Общие требования к React

* Для отступов используется 2 пробела
* Не должно быть пробелов в конце строк или между строками
* Максимальная длина строки — 120 символов.
* Максимальное количество строк в одном файле — 350


### Не импортируем React в каждом файле

```js
import React from 'react'
```

### Не ставим `;` в конце выражений

**Неправильно:**
```js
import { AppRoutes } from './app/Routes';

const App = () => {
  return <AppRoutes />
};

export default App;
```

**Правильно:**
```js
import { AppRoutes } from './app/Routes'

const App = () => {
  return <AppRoutes />
}

export default App
```

### Используем абсолютные импорты и алиасы

**Неправильно:**
```js
import { Main } from '../../pages/Main/Main'
```

**Правильно:**
```js
import { Main } from 'pages/Main/Main'
import { Main, Contacts } from '@pages'
```