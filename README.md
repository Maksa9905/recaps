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

Почитать про библиотеку [здесь](https://recaps.hakolr.dev/docs) – подробная документация с примерами, собрана мною на [Docusaurus](https://docusaurus.io/).

### Под капотом:

- Настроена автопубликацию npm-библиотек через интрумент `changeset`
- Настроены и написаны unit-тесты (покрытие 97%)
<img width="717" height="83" alt="image" src="https://github.com/user-attachments/assets/fd865927-521d-405d-a205-53be436f541c" />

- Настроен линтер `biomeJS`
- Проверки на чистоту кода и unit-тесты добавлены в CI/CD и husky-прекоммиты
- Деплой сайта с документацией на VPS через CI/CD

## Демо сайт
[![Recap Engine Documentation Site](https://img.shields.io/badge/Recaps%20Engine-View%20Demo-3ECC5F&v=1)](https://recaps.hakolr.dev)

<img width="1470" height="796" alt="image" src="https://github.com/user-attachments/assets/73c5ccb1-0574-4cda-a462-665ef692af52" />
<img width="1470" height="795" alt="image" src="https://github.com/user-attachments/assets/76a1e497-34d9-4847-865f-fd9b6ffe9717" />

Для демонстрации работы библиотеке мною был написан небольшой демо-сайт с примером использования виджета.

- Разработана страница с каталогом товаров (отображаются моковые данные из сервиса [DummyJSON](https://dummyjson.com/docs/products))
  - React + TypeScript
  - Vite
  - Tanstack Query
  - Tanstack Router
  - MantineUI
  - nuqs (для квери параметров)
- Настроены и написаны unit-тесты (покрытие 42%)
<img width="573" height="80" alt="image" src="https://github.com/user-attachments/assets/675f00ee-fa30-41d9-9886-433c26d5417a" />

- Настроен линтер `biomeJS`
- Проверки на чистоту кода и unit-тесты добавлены в CI/CD и husky-прекоммиты

## Админ панель
[![Recap Engine Admin Panel](https://img.shields.io/badge/Recaps%20Engine-Admin%20Panel-3ECC5F&v=1)](https://recaps.hakolr.dev/admin)

Также мною была реализована админ-панель для настройки виджета рекапов:
- Разработаны 4 страницы (метрики, бейджи, сцены, рекомендации)
  - React + TypeScript
  - Vite
  - Tanstack Query
  - Tanstack Router
  - MantineUI
  - nuqs (для квери параметров)
- Настроены и написаны unit-тесты
- Настроен линтер `biomeJS`
- Проверки на чистоту кода и unit-тесты добавлены в CI/CD и husky-прекоммиты
- Добавлена страница preview с возможностью выбирать версию виджета из API npm, скачивать ее и рендерить напрямую на странице "Превью" для того, чтобы on-the-fly посмотреть, как будет работать библотека

## Деплой в продакшен 

Я настроил деплой в продакшен при пуше в main. Для этого созданы 2 джобы – первая детектит, в каких сервисах были изменения, вторая – подключается к VPS и пересобирает образы сервисов, которые поменял разработчик. Прикрутил к нашему сервису [домен](https://hakolr.dev) и добавил SSL-сертификаты для https-соединения. 
