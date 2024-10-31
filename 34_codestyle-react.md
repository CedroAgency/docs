# Общие требования к React

### Не импортируем React, это делается автоматически

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

### Для импорта CSS модулей, используем сокращение `s`

**Неправильно:**
```js
import styles from './Main.module.scss'

..
<div className={styles.main} />
```

**Правильно:**
```js
import s from './Main.module.scss'

..
<div className={s.main} />
```

### Названия интерфейсов начинаем с заглавной "I"

**Неправильно:**
```js
interface props {
  className?: string
}
```

**Правильно:**
```js
interface IProps {
  className?: string
}
```
