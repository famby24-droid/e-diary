# 📓 Электронный Дневник

Система электронного журнала для учеников, учителей и администраторов школы.

**Автор:** Аманбек Санжар  
**Стек:** React 18 + Node.js + MongoDB

---

## 🚀 Быстрый старт

### Требования
- Node.js 18+
- MongoDB Atlas аккаунт (или локальный MongoDB)

### 1. Клонирование репозитория
```bash
git clone https://github.com/your-username/electronic-diary.git
cd electronic-diary
```

### 2. Настройка бэкенда
```bash
cd server
npm install
cp .env.example .env
# Заполните .env своими данными
npm run dev
```

### 3. Настройка фронтенда
```bash
cd client
npm install
npm run dev
```

Приложение доступно на `http://localhost:5173`

---

## ⚙️ Переменные окружения (server/.env)

| Переменная | Описание | Пример |
|-----------|----------|--------|
| `PORT` | Порт сервера | `5000` |
| `MONGO_URI` | Строка подключения MongoDB | `mongodb+srv://...` |
| `JWT_SECRET` | Секрет для JWT токенов | `supersecretkey` |
| `CLIENT_URL` | URL фронтенда | `http://localhost:5173` |

---

## 🛠️ Технологический стек

### Frontend
| Технология | Назначение |
|-----------|-----------|
| React 18 | UI фреймворк |
| Vite | Сборщик с HMR |
| React Router v6 | Маршрутизация |
| Axios | HTTP запросы |
| React Hook Form | Валидация форм |
| React Hot Toast | Уведомления |
| Recharts | Графики оценок |

### Backend
| Технология | Назначение |
|-----------|-----------|
| Node.js + Express | Сервер |
| Mongoose | ODM для MongoDB |
| JWT | Аутентификация |
| bcryptjs | Хеширование паролей |
| Multer | Загрузка файлов |
| Helmet | Защита HTTP заголовков |
| CORS | Кросс-доменные запросы |

---

## 📋 Функциональность

### Роли пользователей
| Роль | Возможности |
|------|------------|
| **Ученик** | Просмотр своих оценок, расписания, заданий, профиль |
| **Учитель** | Всё выше + управление оценками и домашними заданиями |
| **Администратор** | Всё выше + управление расписанием и пользователями |

### Основные модули
- **Авторизация** — регистрация, вход, JWT токены, хеширование паролей
- **Оценки** — CRUD, фильтрация, график распределения
- **Расписание** — разбивка по дням недели, управление уроками
- **Домашние задания** — создание с вложениями, сроки, статус
- **Профиль** — загрузка аватара, редактирование данных
- **Панель администратора** — управление всеми пользователями

---

## 🔌 API Документация

### Аутентификация
| Метод | URL | Описание |
|-------|-----|----------|
| POST | `/api/auth/register` | Регистрация нового пользователя |
| POST | `/api/auth/login` | Вход в систему |
| GET | `/api/auth/me` | Текущий авторизованный пользователь |
| PUT | `/api/auth/profile` | Обновление профиля |
| POST | `/api/auth/avatar` | Загрузка аватара |

### Оценки
| Метод | URL | Описание | Роль |
|-------|-----|----------|------|
| GET | `/api/grades` | Список оценок | Все |
| POST | `/api/grades` | Создать оценку | Teacher, Admin |
| PUT | `/api/grades/:id` | Изменить оценку | Teacher, Admin |
| DELETE | `/api/grades/:id` | Удалить оценку | Teacher, Admin |

### Расписание
| Метод | URL | Описание | Роль |
|-------|-----|----------|------|
| GET | `/api/schedule` | Расписание | Все |
| POST | `/api/schedule` | Добавить урок | Admin |
| PUT | `/api/schedule/:id` | Изменить урок | Admin |
| DELETE | `/api/schedule/:id` | Удалить урок | Admin |

### Домашние задания
| Метод | URL | Описание | Роль |
|-------|-----|----------|------|
| GET | `/api/homework` | Список заданий | Все |
| POST | `/api/homework` | Создать задание | Teacher, Admin |
| PUT | `/api/homework/:id` | Изменить задание | Teacher, Admin |
| DELETE | `/api/homework/:id` | Удалить задание | Teacher, Admin |

### Пользователи
| Метод | URL | Описание | Роль |
|-------|-----|----------|------|
| GET | `/api/users` | Список пользователей | Admin, Teacher |
| PUT | `/api/users/:id` | Изменить пользователя | Admin |
| DELETE | `/api/users/:id` | Удалить пользователя | Admin |

**Все защищённые маршруты требуют заголовок:**
```
Authorization: Bearer <JWT_TOKEN>
```

---

## 🚢 Деплой

### Бэкенд → Render.com
1. Создайте аккаунт на [render.com](https://render.com)
2. New → Web Service → подключите GitHub репозиторий
3. Root Directory: `server`
4. Build Command: `npm install`
5. Start Command: `node server.js`
6. Добавьте переменные окружения

### Фронтенд → Vercel
1. Создайте аккаунт на [vercel.com](https://vercel.com)
2. Import Git Repository
3. Root Directory: `client`
4. Build Command: `npm run build`
5. Output Directory: `dist`

---

## 🧪 Тестирование

### Ручное тестирование
Тестирование проведено в браузерах: Chrome, Firefox.

### API тестирование (Postman)
Импортируйте коллекцию и проверьте все эндпоинты:
1. `POST /api/auth/register` — регистрация
2. `POST /api/auth/login` — вход (сохраните токен)
3. `GET /api/grades` — оценки (с Bearer токеном)
4. `POST /api/grades` — создание оценки

### Тестовые аккаунты
После запуска создайте пользователей вручную через форму регистрации.

---

## 📁 Структура проекта

```
electronic-diary/
├── client/          # React фронтенд
│   └── src/
│       ├── components/   # Переиспользуемые компоненты
│       ├── pages/        # Страницы
│       ├── context/      # React Context (Auth)
│       └── utils/        # Утилиты (axios)
└── server/          # Node.js бэкенд
    ├── config/      # Подключение БД
    ├── middleware/  # Auth, Upload middleware
    ├── models/      # Mongoose схемы
    └── routes/      # Express маршруты
```
