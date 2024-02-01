# Общие требования к React

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
