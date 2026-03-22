# Dostaffkin

Веб-приложение для оформления и отслеживания доставки посылок.

## Что делает приложение
- Показывает лендинг с быстрыми переходами к оформлению и трекингу.
- Оформляет доставку: выбор адресов, размера посылки, скорости, расчёт стоимости и срока.
- Отслеживает посылку по номеру отправления.

## Ключевой функционал
- Роуты:
  - `/` — главная страница.
  - `/order` — оформление доставки.
  - `/track` — отслеживание посылки.
- Расчёт доставки на странице `/order`:
  - Построение маршрута через Yandex Maps (`ymaps.multiRouter.MultiRoute`).
  - Тарифы по размеру из `order.config.ts` (`DELIVERY_SIZES`).
  - Скорости доставки: `regular`, `fast` (`DELIVERY_SPEEDS`).
  - Формула: стоимость зависит от километража, тарифа и минимальной цены; для `fast` применяется наценка.
- Работа с API (`src/app/services/delivery-api.ts`):
  - `POST https://testologia.ru/delivery/create` — создание заявки.
  - `GET https://testologia.ru/delivery/info?id=<number>` — получение статуса отправления.
- UI-уведомления об успехах и ошибках через `ngx-toastr`.

## Технологии
- Язык: TypeScript.
- Фреймворк: Angular 21 (standalone components, Angular Router, Forms/Reactive Forms, HttpClient).
- Библиотеки: RxJS, ngx-toastr.
- Внешние сервисы: Yandex Maps JS API, backend API `testologia.ru`.
- Инструменты: Angular CLI, Vitest, jsdom, Prettier.

## Запуск
Требования: Node.js и npm.

```bash
npm install
npm start
```

Приложение запустится в режиме разработки через Angular CLI (`ng serve`).

## Скрипты
```bash
npm start   # запуск dev-сервера
npm run build  # production-сборка
npm run watch  # сборка в watch-режиме (development)
npm test    # запуск тестов
```