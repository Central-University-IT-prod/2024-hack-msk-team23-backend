# Let's Split

Сервис для разделения счетов между друзьями с возможностью сканирования чеков.

## Технологии

- Python 3.12
- FastAPI
- PostgreSQL
- Docker
- JWT для аутентификации
- Интеграция с сервисом проверки чеков

## Требования

- Docker и Docker Compose
- Python 3.12+ (для локальной разработки)

## Установка и запуск

1. Клонируйте репозиторий:
```bash
git clone <https://{{sensitive_data}}/prod-team-23/backend>
cd backend
```

2. Создайте файл с переменными окружения:
```bash
cp .env.dist .env
```

3. Отредактируйте `.env` файл, установив необходимые значения:
```env
ENV=prod  # Окружение (dev/prod)
PROJECT_NAME="Let's split"  # Название проекта

BACKEND_PORT=8000  # Порт для FastAPI приложения

# Настройки PostgreSQL
POSTGRES_PORT=5432
POSTGRES_USER={{sensitive_data}}
POSTGRES_PASSWORD={{sensitive_data}}
POSTGRES_DB=PROD

# API ключи
PROVERKACHEKA_TOKEN=your_token  # Токен для сервиса проверки чеков
GEMINI_API_KEY=your_key  # API ключ Gemini (опционально)

# Настройки JWT
JWT_SECRET=your_secret  # Секретный ключ для JWT
JWT_ALGORITHM=HS256
JWT_EXPIRES_MINUTES=10080  # Время жизни токена (7 дней)
```

4. Запустите приложение с помощью Docker:
```bash
docker compose up --build
```

Приложение будет доступно по адресу: `http://localhost:8000`

## API Документация

После запуска приложения, документация API доступна по следующим адресам:
- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

## Основные эндпоинты

- `/api/v1/auth/*` - Аутентификация и регистрация
- `/api/v1/users/*` - Управление пользователями
- `/api/v1/events/*` - Управление событиями
- `/api/v1/bills/*` - Управление счетами
- `/api/v1/items/*` - Управление позициями в счетах
- `/api/v1/receipts/*` - Обработка чеков
- `/api/v1/invites/*` - Управление приглашениями

## Разработка

1. Создайте виртуальное окружение:
```bash
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate  # Windows
```

2. Установите зависимости:
```bash
pip install -r requirements.txt
```

3. Запустите сервер для разработки:
```bash
uvicorn app:create_app --factory --reload --port 8000
```

