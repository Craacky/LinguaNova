# 🛠️ LinguaNova - Гайд по настройке окружения разработки

## 📋 Содержание

1. [Требования к системе](#требования-к-системе)
2. [Установка необходимого ПО](#установка-необходимого-по)
3. [Настройка проекта](#настройка-проекта)
4. [Docker окружение](#docker-окружение)
5. [Локальная разработка](#локальная-разработка)
6. [Полезные команды](#полезные-команды)
7. [Troubleshooting](#troubleshooting)

---

## 🖥️ Требования к системе

### Минимальные требования
- **OS:** Linux (Ubuntu 22.04+), macOS 12+, Windows 10/11 (с WSL2)
- **RAM:** 8GB (рекомендуется 16GB)
- **Disk:** 20GB свободного места
- **CPU:** 2 cores (рекомендуется 4 cores)

---

## 📦 Установка необходимого ПО

### 1. Git

#### Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install git -y
git --version
```

#### macOS
```bash
# Установка через Homebrew
brew install git
git --version
```

#### Windows (WSL2)
```bash
sudo apt update
sudo apt install git -y
git --version
```

### 2. Docker & Docker Compose

#### Linux (Ubuntu/Debian)
```bash
# Удаление старых версий
sudo apt remove docker docker-engine docker.io containerd runc

# Установка зависимостей
sudo apt update
sudo apt install ca-certificates curl gnupg lsb-release -y

# Добавление официального GPG ключа Docker
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Добавление репозитория Docker
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Установка Docker Engine
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# Добавление пользователя в группу docker (чтобы не использовать sudo)
sudo usermod -aG docker $USER

# Перезагрузка сессии (или перелогиниться)
newgrp docker

# Проверка установки
docker --version
docker compose version
```

#### macOS
```bash
# Скачать Docker Desktop с официального сайта
# https://www.docker.com/products/docker-desktop/

# Или через Homebrew
brew install --cask docker

# Запустить Docker Desktop
open /Applications/Docker.app

# Проверка
docker --version
docker compose version
```

#### Windows (WSL2)
```bash
# 1. Установить WSL2
# Открыть PowerShell от имени администратора:
wsl --install

# 2. Скачать и установить Docker Desktop для Windows
# https://www.docker.com/products/docker-desktop/

# 3. В настройках Docker Desktop включить WSL2 integration

# 4. В WSL2 терминале проверить:
docker --version
docker compose version
```

### 3. Python 3.11+

#### Linux (Ubuntu/Debian)
```bash
# Установка Python 3.11
sudo apt update
sudo apt install software-properties-common -y
sudo add-apt-repository ppa:deadsnakes/ppa -y
sudo apt update
sudo apt install python3.11 python3.11-venv python3.11-dev -y

# Установка pip
sudo apt install python3-pip -y

# Проверка
python3.11 --version
pip3 --version
```

#### macOS
```bash
# Через Homebrew
brew install python@3.11

# Проверка
python3.11 --version
pip3 --version
```

#### Windows (WSL2)
```bash
# То же что и для Linux
sudo apt update
sudo apt install software-properties-common -y
sudo add-apt-repository ppa:deadsnakes/ppa -y
sudo apt update
sudo apt install python3.11 python3.11-venv python3.11-dev -y
```

### 4. Node.js 18+ & npm

#### Linux (Ubuntu/Debian)
```bash
# Установка через NodeSource
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install nodejs -y

# Проверка
node --version
npm --version
```

#### macOS
```bash
# Через Homebrew
brew install node@18

# Проверка
node --version
npm --version
```

#### Windows (WSL2)
```bash
# То же что и для Linux
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install nodejs -y
```

### 5. PostgreSQL Client (опционально, для локальной работы)

#### Linux (Ubuntu/Debian)
```bash
sudo apt install postgresql-client -y
psql --version
```

#### macOS
```bash
brew install postgresql@15
psql --version
```

### 6. Redis Client (опционально)

#### Linux (Ubuntu/Debian)
```bash
sudo apt install redis-tools -y
redis-cli --version
```

#### macOS
```bash
brew install redis
redis-cli --version
```

### 7. IDE / Редактор кода

Рекомендуемые варианты:

#### VS Code (рекомендуется)
```bash
# Linux
sudo snap install code --classic

# macOS
brew install --cask visual-studio-code

# Windows
# Скачать с https://code.visualstudio.com/
```

**Рекомендуемые расширения для VS Code:**
- Python (ms-python.python)
- Pylance (ms-python.vscode-pylance)
- Docker (ms-azuretools.vscode-docker)
- ESLint (dbaeumer.vscode-eslint)
- Prettier (esbenp.prettier-vscode)
- Tailwind CSS IntelliSense (bradlc.vscode-tailwindcss)
- GitLens (eamodio.gitlens)

#### PyCharm Professional (альтернатива)
```bash
# Скачать с https://www.jetbrains.com/pycharm/
```

---

## 🚀 Настройка проекта

### 1. Клонирование репозитория

```bash
# Перейти в директорию для проектов
cd ~/Projects

# Клонировать репозиторий (если уже создан на GitHub)
git clone https://github.com/yourusername/linguanova.git
cd linguanova

# Или если репозиторий еще не создан, инициализировать локально
cd LinguaNova
git init
```

### 2. Создание структуры проекта

```bash
# Создание директорий для backend
mkdir -p backend/app/{api/endpoints,core,models,schemas,services,utils}
mkdir -p backend/alembic/versions
mkdir -p backend/tests

# Создание директорий для frontend
mkdir -p frontend/{app,components,lib,store,types}

# Создание директорий для Docker и Nginx
mkdir -p nginx/conf.d
mkdir -p docker/postgres
mkdir -p docker/redis

# Создание директорий для документации
mkdir -p docs

# Проверка структуры
tree -L 2 -d
```

### 3. Создание .env файлов

#### Backend .env
```bash
# Создать файл backend/.env
cat > backend/.env << 'EOF'
# Database
DATABASE_URL=postgresql://linguanova:linguanova_password@postgres:5432/linguanova_db
POSTGRES_USER=linguanova
POSTGRES_PASSWORD=linguanova_password
POSTGRES_DB=linguanova_db

# Redis
REDIS_URL=redis://redis:6379/0

# JWT
JWT_SECRET_KEY=your-super-secret-jwt-key-change-this-in-production
JWT_ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
REFRESH_TOKEN_EXPIRE_DAYS=7

# OAuth (Google)
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
GOOGLE_REDIRECT_URI=http://localhost:8000/api/auth/google/callback

# OpenRouter AI
OPENROUTER_API_KEY=your-openrouter-api-key

# Cloudflare R2
CLOUDFLARE_R2_ACCESS_KEY=your-r2-access-key
CLOUDFLARE_R2_SECRET_KEY=your-r2-secret-key
CLOUDFLARE_R2_BUCKET_NAME=linguanova-storage
CLOUDFLARE_R2_ENDPOINT=https://your-account-id.r2.cloudflarestorage.com

# Sentry
SENTRY_DSN=your-sentry-dsn

# Environment
ENVIRONMENT=development
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1
CORS_ORIGINS=http://localhost:3000,http://127.0.0.1:3000
EOF
```

#### Frontend .env
```bash
# Создать файл frontend/.env.local
cat > frontend/.env.local << 'EOF'
# API
NEXT_PUBLIC_API_URL=http://localhost:8000
NEXT_PUBLIC_API_TIMEOUT=30000

# Environment
NEXT_PUBLIC_ENVIRONMENT=development

# Google OAuth (для frontend)
NEXT_PUBLIC_GOOGLE_CLIENT_ID=your-google-client-id
EOF
```

#### Docker .env (корневой)
```bash
# Создать файл .env в корне проекта
cat > .env << 'EOF'
# PostgreSQL
POSTGRES_USER=linguanova
POSTGRES_PASSWORD=linguanova_password
POSTGRES_DB=linguanova_db

# Ports
BACKEND_PORT=8000
FRONTEND_PORT=3000
POSTGRES_PORT=5432
REDIS_PORT=6379
EOF
```

### 4. Создание .env.example файлов

```bash
# Backend
cp backend/.env backend/.env.example

# Frontend
cp frontend/.env.local frontend/.env.example

# Root
cp .env .env.example

# Очистить секретные данные в .example файлах (вручную)
```

---

## 🐳 Docker окружение

### 1. Создание docker-compose.yml

```bash
cat > docker-compose.yml << 'EOF'
version: '3.9'

services:
  # PostgreSQL Database
  postgres:
    image: postgres:15-alpine
    container_name: linguanova_postgres
    restart: unless-stopped
    environment:
      POSTGRES_USER: ${POSTGRES_USER}
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}
      POSTGRES_DB: ${POSTGRES_DB}
    ports:
      - "${POSTGRES_PORT:-5432}:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./docker/postgres/init.sql:/docker-entrypoint-initdb.d/init.sql
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U ${POSTGRES_USER}"]
      interval: 10s
      timeout: 5s
      retries: 5
    networks:
      - linguanova_network

  # Redis Cache
  redis:
    image: redis:7-alpine
    container_name: linguanova_redis
    restart: unless-stopped
    ports:
      - "${REDIS_PORT:-6379}:6379"
    volumes:
      - redis_data:/data
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 10s
      timeout: 5s
      retries: 5
    networks:
      - linguanova_network

  # Backend (FastAPI)
  backend:
    build:
      context: ./backend
      dockerfile: Dockerfile
    container_name: linguanova_backend
    restart: unless-stopped
    environment:
      - DATABASE_URL=postgresql://${POSTGRES_USER}:${POSTGRES_PASSWORD}@postgres:5432/${POSTGRES_DB}
      - REDIS_URL=redis://redis:6379/0
    ports:
      - "${BACKEND_PORT:-8000}:8000"
    volumes:
      - ./backend:/app
      - backend_cache:/app/__pycache__
    depends_on:
      postgres:
        condition: service_healthy
      redis:
        condition: service_healthy
    command: uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
    networks:
      - linguanova_network

  # Frontend (Next.js)
  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile
    container_name: linguanova_frontend
    restart: unless-stopped
    environment:
      - NEXT_PUBLIC_API_URL=http://localhost:${BACKEND_PORT:-8000}
    ports:
      - "${FRONTEND_PORT:-3000}:3000"
    volumes:
      - ./frontend:/app
      - /app/node_modules
      - /app/.next
    depends_on:
      - backend
    command: npm run dev
    networks:
      - linguanova_network

  # Celery Worker (Background tasks)
  celery_worker:
    build:
      context: ./backend
      dockerfile: Dockerfile
    container_name: linguanova_celery_worker
    restart: unless-stopped
    environment:
      - DATABASE_URL=postgresql://${POSTGRES_USER}:${POSTGRES_PASSWORD}@postgres:5432/${POSTGRES_DB}
      - REDIS_URL=redis://redis:6379/0
    volumes:
      - ./backend:/app
    depends_on:
      postgres:
        condition: service_healthy
      redis:
        condition: service_healthy
    command: celery -A app.core.celery worker --loglevel=info
    networks:
      - linguanova_network

volumes:
  postgres_data:
  redis_data:
  backend_cache:

networks:
  linguanova_network:
    driver: bridge
EOF
```

### 2. Создание Dockerfile для Backend

```bash
cat > backend/Dockerfile << 'EOF'
FROM python:3.11-slim

# Установка системных зависимостей
RUN apt-get update && apt-get install -y \
    gcc \
    postgresql-client \
    && rm -rf /var/lib/apt/lists/*

# Рабочая директория
WORKDIR /app

# Копирование requirements
COPY requirements.txt .

# Установка Python зависимостей
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt

# Копирование кода приложения
COPY . .

# Expose порт
EXPOSE 8000

# Команда запуска (будет переопределена в docker-compose)
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
EOF
```

### 3. Создание Dockerfile для Frontend

```bash
cat > frontend/Dockerfile << 'EOF'
FROM node:18-alpine

# Рабочая директория
WORKDIR /app

# Копирование package.json и package-lock.json
COPY package*.json ./

# Установка зависимостей
RUN npm ci

# Копирование кода приложения
COPY . .

# Expose порт
EXPOSE 3000

# Команда запуска (будет переопределена в docker-compose)
CMD ["npm", "run", "dev"]
EOF
```

### 4. Создание .dockerignore файлов

#### Backend .dockerignore
```bash
cat > backend/.dockerignore << 'EOF'
__pycache__
*.pyc
*.pyo
*.pyd
.Python
env/
venv/
.venv
.env
.env.local
*.log
.pytest_cache
.coverage
htmlcov/
.tox/
*.egg-info/
dist/
build/
.git
.gitignore
README.md
.vscode
.idea
EOF
```

#### Frontend .dockerignore
```bash
cat > frontend/.dockerignore << 'EOF'
node_modules
.next
out
.env
.env.local
.env.production
.env.development
npm-debug.log*
yarn-debug.log*
yarn-error.log*
.git
.gitignore
README.md
.vscode
.idea
EOF
```

### 5. Запуск Docker окружения

```bash
# Сборка образов
docker compose build

# Запуск всех сервисов
docker compose up -d

# Просмотр логов
docker compose logs -f

# Просмотр логов конкретного сервиса
docker compose logs -f backend

# Проверка статуса
docker compose ps

# Остановка всех сервисов
docker compose down

# Остановка с удалением volumes (БД будет очищена!)
docker compose down -v
```

---

## 💻 Локальная разработка

### Backend (без Docker)

#### 1. Создание виртуального окружения

```bash
cd backend

# Создание venv
python3.11 -m venv venv

# Активация venv
# Linux/macOS:
source venv/bin/activate

# Windows (WSL2):
source venv/bin/activate

# Проверка
which python
python --version
```

#### 2. Установка зависимостей

```bash
# Создать requirements.txt (базовый)
cat > requirements.txt << 'EOF'
# FastAPI
fastapi==0.109.0
uvicorn[standard]==0.27.0
python-multipart==0.0.6

# Database
sqlalchemy==2.0.25
alembic==1.13.1
psycopg2-binary==2.9.9

# Validation
pydantic==2.5.3
pydantic-settings==2.1.0
email-validator==2.1.0

# Authentication
python-jose[cryptography]==3.3.0
passlib[bcrypt]==1.7.4
python-multipart==0.0.6

# OAuth
authlib==1.3.0
httpx==0.26.0

# Background tasks
celery==5.3.6
redis==5.0.1

# Web scraping
beautifulsoup4==4.12.3
scrapy==2.11.0

# Storage
boto3==1.34.34

# Monitoring
sentry-sdk[fastapi]==1.40.0

# Development
pytest==7.4.4
pytest-asyncio==0.23.3
black==24.1.1
flake8==7.0.0
mypy==1.8.0
EOF

# Установка
pip install -r requirements.txt
```

#### 3. Настройка локальной БД

```bash
# Запустить только PostgreSQL через Docker
docker compose up -d postgres

# Или установить PostgreSQL локально
# Linux:
sudo apt install postgresql postgresql-contrib -y
sudo systemctl start postgresql
sudo -u postgres createuser linguanova
sudo -u postgres createdb linguanova_db
sudo -u postgres psql -c "ALTER USER linguanova WITH PASSWORD 'linguanova_password';"

# Обновить DATABASE_URL в .env для локальной БД
# DATABASE_URL=postgresql://linguanova:linguanova_password@localhost:5432/linguanova_db
```

#### 4. Запуск backend локально

```bash
# Активировать venv
source venv/bin/activate

# Запуск с hot-reload
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000

# Или через make (если создан Makefile)
make run
```

### Frontend (без Docker)

#### 1. Установка зависимостей

```bash
cd frontend

# Инициализация Next.js проекта (если еще не создан)
npx create-next-app@latest . --typescript --tailwind --app --no-src-dir

# Или установка зависимостей существующего проекта
npm install

# Установка дополнительных пакетов
npm install axios zustand @tanstack/react-query
npm install react-hook-form zod @hookform/resolvers
npm install recharts howler
npm install -D @types/howler

# Установка shadcn/ui
npx shadcn-ui@latest init
```

#### 2. Запуск frontend локально

```bash
# Development сервер
npm run dev

# Или через yarn
yarn dev

# Или через pnpm
pnpm dev
```

---

## 🔧 Полезные команды

### Docker команды

```bash
# Пересборка конкретного сервиса
docker compose build backend

# Перезапуск конкретного сервиса
docker compose restart backend

# Просмотр логов с tail
docker compose logs -f --tail=100 backend

# Вход в контейнер
docker compose exec backend bash
docker compose exec postgres psql -U linguanova -d linguanova_db

# Очистка неиспользуемых образов и volumes
docker system prune -a
docker volume prune

# Просмотр использования ресурсов
docker stats
```

### Backend команды

```bash
# Активация venv
source backend/venv/bin/activate

# Создание миграции
cd backend
alembic revision --autogenerate -m "Initial migration"

# Применение миграций
alembic upgrade head

# Откат миграции
alembic downgrade -1

# Запуск тестов
pytest

# Форматирование кода
black .

# Проверка линтером
flake8 .

# Type checking
mypy .
```

### Frontend команды

```bash
cd frontend

# Установка новых пакетов
npm install package-name

# Обновление зависимостей
npm update

# Проверка устаревших пакетов
npm outdated

# Линтинг
npm run lint

# Сборка production
npm run build

# Запуск production сборки
npm run start

# Добавление shadcn компонента
npx shadcn-ui@latest add button
```

### Git команды

```bash
# Инициализация репозитория
git init

# Добавление remote
git remote add origin https://github.com/yourusername/linguanova.git

# Первый коммит
git add .
git commit -m "Initial commit: project setup"
git branch -M main
git push -u origin main

# Создание ветки для разработки
git checkout -b develop
git push -u origin develop

# Создание feature ветки
git checkout -b feature/user-authentication
```

---

## 🐛 Troubleshooting

### Проблема: Docker контейнеры не запускаются

```bash
# Проверить логи
docker compose logs

# Проверить статус
docker compose ps

# Пересоздать контейнеры
docker compose down
docker compose up -d --force-recreate

# Очистить volumes и пересоздать
docker compose down -v
docker compose up -d
```

### Проблема: Порты заняты

```bash
# Проверить какой процесс использует порт
sudo lsof -i :8000
sudo lsof -i :3000

# Убить процесс
kill -9 <PID>

# Или изменить порты в .env файле
```

### Проблема: Permission denied для Docker

```bash
# Добавить пользователя в группу docker
sudo usermod -aG docker $USER

# Перелогиниться или выполнить
newgrp docker

# Проверить
docker ps
```

### Проблема: Backend не подключается к БД

```bash
# Проверить что PostgreSQL запущен
docker compose ps postgres

# Проверить логи PostgreSQL
docker compose logs postgres

# Проверить подключение вручную
docker compose exec postgres psql -U linguanova -d linguanova_db

# Проверить DATABASE_URL в .env
cat backend/.env | grep DATABASE_URL
```

### Проблема: Frontend не может подключиться к Backend

```bash
# Проверить что backend запущен
curl http://localhost:8000/docs

# Проверить CORS настройки в backend
# Убедиться что http://localhost:3000 в CORS_ORIGINS

# Проверить NEXT_PUBLIC_API_URL в frontend/.env.local
cat frontend/.env.local | grep API_URL
```

### Проблема: Миграции Alembic не применяются

```bash
# Войти в backend контейнер
docker compose exec backend bash

# Проверить текущую версию БД
alembic current

# Применить миграции
alembic upgrade head

# Если ошибка, откатить и применить заново
alembic downgrade base
alembic upgrade head
```

### Проблема: Node modules не устанавливаются

```bash
# Очистить кэш npm
npm cache clean --force

# Удалить node_modules и package-lock.json
rm -rf node_modules package-lock.json

# Переустановить
npm install

# Или использовать другой package manager
npm install -g pnpm
pnpm install
```

---

## ✅ Проверка готовности окружения

### Чеклист

```bash
# 1. Проверка установленного ПО
docker --version
docker compose version
python3.11 --version
node --version
npm --version
git --version

# 2. Проверка Docker сервисов
docker compose ps
# Все сервисы должны быть в статусе "Up"

# 3. Проверка Backend
curl http://localhost:8000/docs
# Должна открыться Swagger документация

# 4. Проверка Frontend
curl http://localhost:3000
# Должна вернуться HTML страница

# 5. Проверка PostgreSQL
docker compose exec postgres psql -U linguanova -d linguanova_db -c "SELECT version();"

# 6. Проверка Redis
docker compose exec redis redis-cli ping
# Должно вернуть "PONG"
```

---

## 📚 Дополнительные ресурсы

- [Docker Documentation](https://docs.docker.com/)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Next.js Documentation](https://nextjs.org/docs)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Alembic Documentation](https://alembic.sqlalchemy.org/)

---

**Дата создания:** 2026-04-01  
**Версия:** 1.0  
**Статус:** Готово к использованию
