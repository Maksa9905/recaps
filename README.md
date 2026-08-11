# Авито "Лаборатория кода" – Гайворонский Максим (Frontend)

## Движок для создания рекапов
[![Recap Engine Documentation Site](https://img.shields.io/badge/Recap%20Engine-View%20Documentation-3ECC5F?logo=Docusaurus&v=1)](https://recaps.hakolr.dev/docs)
[![@recap-engine/core NPM version](https://img.shields.io/npm/v/@recap-engine/core?style=flat-square&label=@recap-engine/core&color=CB3837&logo=npm&v=1)](https://www.npmjs.com/package/@recap-engine/core)
[![@recap-engine/react NPM version](https://img.shields.io/npm/v/@recap-engine/core?style=flat-square&label=@recap-engine/react&color=CB3837&logo=npm&v=1)](https://www.npmjs.com/package/@recap-engine/react)

В рамках хакатона мною была разработана npm-библиотека `recap-engine`, библиотека состоит из 2 пакетов:
- [@recap-engine/core](https://www.npmjs.com/package/@recap-engine/core) – коровая логика, Player, интерфейсы, утилитарные функции
- [@recap-engine/react](https://www.npmjs.com/package/@recap-engine/react) – UI-компоненты со сценами, Layouts, компонент `<Recap />`
- _`@recap-engine/vue` `@recap-engine/angular` (в перспективе, библиотека может легко масштабироваться для других фреймворков и переиспользовать логику из `@recap-engine/core`)_

Философия решения:
- **Не хардкодить**. Хотелось сделать полноценный движок с удобным и понятным API, который можно будет использовать как в "Авито Товары", так в "Авито Авто", "Авито Недвижимость" и др. А при необходимости и в других сервисах (VK, Telegram, YouTube) – это можно с легкостью сделать, поскольку движок позволяет кастомизировать сцены под дизайн систему вашего сервиса.

- **Быстрый старт с возможностью усложнять**. Из под капота библиотека даёт пользователю [7 базовых сцен](https://recaps.hakolr.dev/docs/core/scene-types) – этого вполне достаточно для того, чтобы можно было создать базовый рекап. Хотите усложнять? Тогда регистрируйте [кастомные сцены](https://recaps.hakolr.dev/docs/react/custom-scenes) и используйте их в своих рекапах. Так можно создавать более богатые и интересные визуалы в своих рекапах.

- **2 типа API**. Рекапы могут строиться на клиентской стороне или на бэкенде.
  - На клиентской стороне мы заранее знаем список отображаемых сцен, тогда [объявляем сцены](http://recaps.hakolr.dev/docs/core/scenes#definescenes) через `defineScenes()`.
  - Когда экраны приходят с бэкенда используем `prepareRecap()` – он преобразует ответ бэка ([RecapPayload](https://recaps.hakolr.dev/docs/core/recap-payload)) в формат, который принимает виджет 

