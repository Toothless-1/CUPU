# Credit Risk Prediction Service 
Этот сервис предоставляет систему анализа кредитного риска с использованием машинного обучения. Архитектура реализована через микросервисы с использованием Docker Compose 
🔧 Основные возможности 

    Клиент-сервесная архитектура  (Angular + Django + FastAPI + PostgreSQL)
    JWT-аутентификация  с refresh-токенами в HttpOnly cookies
    Реализация предсказания риска  через ML-модель
    История заявок  с фильтрацией по пользователям
    Горизонтальное масштабирование  через Docker Compose
     

📦 Требования 

    Docker 20.10+
    Docker Compose v2+
    Node.js 18+ и npm 9+

# Структура проекта

1. ├── angular/        # Angular 19 frontend
2. ├── django/         # Django backend с JWT
3. ├── fastapi/        # ML-сервис на FastAPI
4. └── docker-compose.yml # Оркестрация сервисов

# Сборка и запуск контейнеров
docker-compose up -d --build

# Применение миграций
docker-compose exec django python manage.py migrate

# Создание суперпользователя
docker-compose exec django python manage.py createsuperuser
 
 
🧪 Использование 

Доступ к сервисам:  

    Angular: http://localhost:4200
    Django Admin: http://localhost:8000/admin
    FastAPI Docs: http://localhost:5000/docs
     
# Django
DJANGO_SECRET_KEY=your_secret_key
DJANGO_DEBUG=True

# База данных
POSTGRES_DB=credit_db
POSTGRES_USER=admin
POSTGRES_PASSWORD=admin_pass

# Angular
API_URL=http://localhost:8000/api
 
 
📡 API Endpoints 

POST /login          # Получение JWT и refresh-токена
POST /predict        # Анализ кредитного риска
GET /latest-prediction # Последний результат
 
 
🛠 Команды Docker 

# Остановка и удаление контейнеров
docker-compose down

# Просмотр логов
docker-compose logs -f

# Запуск тестов
docker-compose exec django pytest
 
 
🛡 Безопасность 

    Refresh-токены хранятся в HttpOnly cookies
    Все межсервисные запросы проходят через JWT-валидацию
    CORS-заголовки ограничивают доступ
     

🧰 Траблшутинг 

"Token is invalid"    
# Проверьте срок действия токена
docker-compose exec django python manage.py shell
>>> from datetime import datetime
>>> from jwt import decode
>>> decode(token, options={"verify_signature": False})

"Database connection failed" 
Проверьте настройки POSTGRES_* в .env и пересоздайте контейнеры: 
docker-compose down -v
docker-compose up -d
"Connection refused" между сервисами 
Убедитесь, что все сервисы находятся в одной сети Docker: 

# docker-compose.yml
networks:
  app-network:
    driver: bridge
     

Создано с использованием Docker Compose для удобного управления микросервисами
