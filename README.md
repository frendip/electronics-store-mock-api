# Electronics Store — Mock API

Демонстрационный REST API с каталогом товаров для [electronics-store](https://github.com/frendip/electronics-store). Сервер на json-server отдаёт данные из JSON-файла и поддерживает получение товаров, поиск, фильтрацию, сортировку и пагинацию. Это mock-сервис для разработки интерфейса: в нём нет авторизации, оплаты и обработки заказов.

**Стек:** Node.js, json-server 0.17, JSON.

## Требования

- Node.js 22.x, npm 10.x и Git.
- Свободный порт 3001.
- Отдельная база данных, ключи и файл `.env` не нужны.

## Локальный запуск

```bash
git clone https://github.com/frendip/electronics-store-mock-api.git
cd electronics-store-mock-api
npm ci
npm start
```

Запускайте команду из корня репозитория: сервер читает относительный путь `src/db.json`.

Каталог доступен по адресу [http://localhost:3001/products](http://localhost:3001/products).

Примеры запросов:

- `GET /products` — весь каталог.
- `GET /products/1` — товар с ID 1.
- `GET /products?_page=1&_limit=8` — страница каталога; общее количество передаётся в заголовке `X-Total-Count`.
- `GET /products?title_like=iphone&_sort=price&_order=asc` — поиск по названию и сортировка по цене.

Данные находятся в `src/db.json`. Стандартные операции записи json-server изменяют этот файл. Порт задан в `src/server.js`; если поменяете его, обновите адрес API в клиентском приложении.

## Сборка

Сборка не требуется: `npm start` запускает JavaScript-сервер напрямую.

## Связанный репозиторий

[electronics-store](https://github.com/frendip/electronics-store) — клиентский интерфейс магазина.

Установка и ответ `GET /products` проверены на Node.js 22.22.3 и npm 10.9.8.
