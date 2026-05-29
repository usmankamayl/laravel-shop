# 🛒 Интернет-магазин на Laravel

Полнофункциональный интернет-магазин, разработанный на Laravel с поддержкой каталога товаров, корзины, заказов и панели администратора.

---

## 📋 Требования

- PHP >= 8.2
- Composer >= 2.x
- Node.js >= 18.x & NPM
- MySQL >= 8.0 / PostgreSQL >= 14
- Redis (опционально, для кэширования и очередей)

---

## 🚀 Установка

### 1. Клонировать репозиторий

```bash
git clone https://github.com/your-username/your-shop.git
cd your-shop
```

### 2. Установить зависимости

```bash
composer install
npm install
```

### 3. Настроить окружение

```bash
cp .env.example .env
php artisan key:generate
```

Отредактируйте `.env` файл:

```env
APP_NAME="Мой Магазин"
APP_URL=http://localhost

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=shop
DB_USERNAME=root
DB_PASSWORD=secret

MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025

# Опционально — Redis
CACHE_STORE=redis
QUEUE_CONNECTION=redis
REDIS_HOST=127.0.0.1
```

### 4. Запустить миграции и сиды

```bash
php artisan migrate --seed
```

### 5. Собрать фронтенд

```bash
npm run build
# или для разработки:
npm run dev
```

### 6. Запустить сервер

```bash
php artisan serve
```

Приложение доступно по адресу: [http://localhost:8000](http://localhost:8000)

---

## 🗂 Структура проекта

```
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Admin/          # Контроллеры панели администратора
│   │   │   ├── CartController.php
│   │   │   ├── OrderController.php
│   │   │   └── ProductController.php
│   │   └── Middleware/
│   ├── Models/
│   │   ├── Category.php
│   │   ├── Order.php
│   │   ├── Product.php
│   │   └── User.php
│   └── Services/
│       ├── CartService.php
│       └── OrderService.php
├── database/
│   ├── migrations/
│   └── seeders/
├── resources/
│   ├── js/
│   └── views/
│       ├── admin/
│       ├── cart/
│       ├── orders/
│       └── products/
└── routes/
    ├── web.php
    └── api.php
```

---

## ✨ Функциональность

### Покупатель
- 📦 Каталог товаров с фильтрацией и поиском
- 🛒 Корзина (добавление, удаление, изменение количества)
- 💳 Оформление заказа
- 📧 Email-уведомления о статусе заказа
- 👤 Личный кабинет и история заказов

### Администратор (`/admin`)
- 📊 Дашборд со статистикой
- 🛍 Управление товарами (CRUD, изображения, остатки)
- 🗂 Управление категориями
- 📋 Управление заказами и изменение статусов
- 👥 Управление пользователями

---

## 🔑 Учётные данные по умолчанию (после сидинга)

| Роль          | Email                  | Пароль     |
|---------------|------------------------|------------|
| Администратор | admin@example.com      | password   |
| Пользователь  | user@example.com       | password   |

> ⚠️ Смените пароли перед деплоем на продакшн.

---

## 🧪 Тесты

```bash
php artisan test
# или с покрытием:
php artisan test --coverage
```

---

## 🔧 Команды Artisan

```bash
# Очистить весь кэш
php artisan optimize:clear

# Запустить очереди (для email и уведомлений)
php artisan queue:work

# Импорт товаров из CSV
php artisan shop:import-products storage/import/products.csv
```

---

## 📦 Деплой

```bash
composer install --optimize-autoloader --no-dev
npm run build
php artisan config:cache
php artisan route:cache
php artisan view:cache
php artisan migrate --force
```

---

## 📄 Лицензия

MIT — свободное использование в коммерческих и личных проектах.
