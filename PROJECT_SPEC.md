# LinguaNova - Платформа для изучения английского языка

## 📋 Описание проекта

LinguaNova - это веб-платформа для изучения английского языка с нуля (A1) до продвинутого уровня (C2). Платформа использует современные методики обучения, AI для персонализации и автоматизации, и предоставляет полный цикл обучения: теория, практика, тестирование, аудирование и пополнение словарного запаса.

---

## 🎯 Основные цели

1. Поднять уровень английского с A1 до C2
2. Использовать передовые практики изучения языков
3. Интегрировать AI для современности и эффективности
4. Предоставить полный цикл обучения (теория → практика → тестирование)
5. Использовать качественные источники контента из интернета

---

## 🏗️ Архитектура проекта

### Технологический стек

#### Backend
- **Framework:** Python + FastAPI
- **ORM:** SQLAlchemy
- **Migrations:** Alembic
- **Validation:** Pydantic
- **Authentication:** JWT + OAuth (Google)
- **Password hashing:** passlib
- **Background tasks:** Celery + Redis
- **Web scraping:** httpx + BeautifulSoup4/Scrapy
- **AI Integration:** OpenRouter (бесплатные модели)
- **Storage:** boto3 (для S3)

#### Frontend
- **Framework:** Next.js (App Router, SSR)
- **Language:** TypeScript
- **Styling:** Tailwind CSS + shadcn/ui
- **State Management:** Zustand
- **Data Fetching:** TanStack Query
- **HTTP Client:** Axios
- **Forms:** React Hook Form + Zod
- **Charts:** Recharts
- **Audio Player:** Howler.js

#### Database
- **СУБД:** PostgreSQL
- **Особенности:** индексы, партиционирование таблиц

#### Storage & CDN
- **File Storage:** Cloudflare R2 (S3-compatible)
- **CDN:** Cloudflare CDN (для быстрой доставки аудио)

#### Infrastructure
- **Containerization:** Docker + Docker Compose
- **CI/CD:** GitHub Actions
- **Hosting:** VPS (собственный сервер)
- **Reverse Proxy:** Nginx + Let's Encrypt (SSL)
- **Domain:** DuckDNS (бесплатный домен)
- **Cache:** Redis

#### Monitoring & Logging
- **Error Tracking:** Sentry
- **Uptime Monitoring:** UptimeRobot
- **Logs:** Docker logs + Papertrail/Loki

---

## 📚 Структура контента

### Иерархия обучения

```
Level (A1, A2, B1, B2, C1, C2)
  └─ Module (Grammar, Vocabulary, Listening, Writing)
      └─ Topic (Present Simple, Past Tense, etc.)
          ├─ Theory (конспект с полным объяснением)
          ├─ Exercises (тренажер - упражнения из задачников)
          └─ Tests (проверка знаний по теме)
```

### Источники контента

#### Теория
- BBC Learning English
- British Council
- EnglishClub
- Wikipedia

#### Тесты и задачники
- Cambridge English
- IELTS Practice
- exam-english.com
- Murphy's Grammar in Use
- Oxford Practice Grammar

#### Метод получения контента
- **Web scraping** (ручной запуск через админку)
- **Fair use** подход к авторским правам
- **Валидация:** Pydantic схемы + ручная проверка в админке + AI проверка качества

#### Аудирование
- Ручная загрузка ресурсов администратором
- AI рекомендации по уровню и теме

---

## 🎓 Функциональность платформы

### 1. Система обучения

#### Выбор уровня и прогресс
- Пользователь выбирает свой уровень (A1-C2)
- Получает последовательность тем для изучения
- Темы проходятся строго по порядку (линейное прохождение)
- Адаптивные рекомендации "что изучать дальше"

#### Структура изучения темы
1. **Theory (Теория)** - полный конспект с объяснениями
2. **Exercises (Упражнения)** - тренажер с задачами из задачников
3. **Tests (Тесты)** - проверка знаний по теме

#### Типы упражнений
- Multiple choice (множественный выбор)
- Fill in the blanks (заполнение пропусков)
- Matching (сопоставление: слово-определение, начало-конец предложения)
- True/False (правда/ложь)
- Ordering (составить предложение из слов)
- Writing (свободный ответ с AI проверкой)
- Listening comprehension (вопросы по аудио)

#### AI функции
- **Объяснение ошибок:** AI генерирует детальное объяснение почему ответ неверный
- **Рекомендации аудирования:** AI предлагает материалы по теме и уровню
- **Модерация комментариев:** автоматическая фильтрация по blacklist слов
- **Будущее:** генерация дополнительных упражнений

### 2. Vocabulary (Словарный запас)

#### Система изучения слов
- **Spaced Repetition:** алгоритм FSRS (современная версия Anki)
- **Отдельный раздел:** "Vocabulary Practice"
- **Карточки:** слово → перевод → примеры использования
- **Уровни сложности:** карточки поднимаются по сложности по мере изучения
- **Отслеживание:** количество изученных слов, прогресс

#### Логика работы
- Пользователь помечает слово как "знаю"
- Алгоритм FSRS определяет когда показать слово снова
- Интервалы повторения увеличиваются при правильных ответах

### 3. Аудирование (Listening)

#### Функционал аудиоплеера
- Регулируемая скорость воспроизведения (0.75x, 1x, 1.25x)
- Перемотка и выбор любой секунды
- Интерактивные транскрипты (клик на слово = перевод)
- Вопросы после прослушивания

#### Источники аудио
- Ручная загрузка администратором
- AI рекомендации материалов по теме/уровню

### 4. Тест на определение уровня

#### Характеристики
- Доступен при регистрации (обязательный)
- Доступен всегда в личном кабинете
- Полное покрытие навыков (grammar, vocabulary, listening, writing)
- Пул вопросов (каждый раз разные вопросы)
- Неограниченные пересдачи
- Симуляция официального теста (Cambridge/IELTS)

### 5. Социальные функции

#### Комментарии
- Под каждой темой
- Автоматическая модерация (blacklist слов)

#### Study Buddy (поиск партнера)
- Пользователь оставляет заявку
- Указывает уровень и контакты для связи
- Другие пользователи могут связаться
- Без встроенного чата (только контакты)

#### Профили
- Публичные профили пользователей
- Отображение прогресса, достижений, streak

#### Sharing (Делиться прогрессом)
- Достижения
- Streak (дни подряд)
- Текущий уровень
- Формат: ссылка на профиль

#### Рейтинг (Leaderboard)
- Глобальный рейтинг
- Формула: `Score = (completed_topics * 10) + (test_scores_sum) + (streak_days * 5)`
- Основан на: пройденных темах, баллах тестов, streak

### 6. Личный кабинет (Dashboard)

#### Метрики и статистика
- **Прогресс по уровням** (% завершения)
- **Время обучения** (daily/weekly/total)
- **Streak** (дни подряд занятий)
- **Сильные/слабые стороны** (grammar vs vocabulary vs listening)
- **История тестов** (динамика баллов)
- **Vocabulary size** (количество изученных слов)
- **Heatmap активности** (календарь как на GitHub)
- **Прогноз достижения следующего уровня**
- **Сравнение с другими пользователями** (percentile)
- **Radar chart навыков** (детализация по навыкам)
- **Рекомендации** ("на что обратить внимание")
- **Тест на уровень** (всегда доступен)

#### Адаптивные рекомендации
- Анализ слабых мест (низкие баллы в тестах)
- Предложение повторить темы
- Рекомендация следующей темы на основе прогресса
- AI генерация персональных советов

### 7. Admin Panel (Админка)

#### Функционал
- **CMS для управления контентом:**
  - Создание/редактирование уровней, модулей, тем
  - Добавление теории, упражнений, тестов
  - Загрузка аудио файлов
  - Управление vocabulary
- **Web scraping:**
  - Ручной запуск парсинга
  - Выбор источника
  - Предпросмотр и валидация данных
  - Публикация контента
- **Модерация комментариев:**
  - Автоматическая фильтрация
  - Ручная модерация при необходимости
  - Управление blacklist слов
- **Управление пользователями:**
  - Просмотр профилей
  - Статистика использования
- **Аналитика:**
  - Популярные темы
  - Проблемные упражнения
  - Общая статистика платформы

---

## 🔐 Аутентификация

### Методы входа
- **Email + Password** (JWT токены)
- **Google OAuth**

### Безопасность
- Password hashing (passlib + bcrypt)
- JWT токены (access + refresh)
- HTTPS (Let's Encrypt)

---

## 🎮 Геймификация

### Элементы
- **Streak** (дни подряд)
- **XP/Points** (за выполнение упражнений)
- **Achievements** (достижения)
- **Leaderboard** (рейтинг)
- **Progress bars** (визуализация прогресса)

---

## 💰 Монетизация

### Текущий этап (MVP)
- Полностью бесплатная платформа
- Без ограничений функционала

### Будущее
- Подписка (premium features)
- Детали будут определены после запуска MVP

---

## 🗄️ Структура базы данных

### Основные таблицы

#### users
- id (PK)
- email (unique)
- password_hash
- name
- current_level_id (FK)
- created_at
- last_login
- streak_count
- total_xp

#### levels
- id (PK)
- code (A1, A2, B1, B2, C1, C2)
- name
- order
- description

#### modules
- id (PK)
- level_id (FK)
- name (Grammar, Vocabulary, Listening, Writing)
- order
- description

#### topics
- id (PK)
- module_id (FK)
- name
- order
- theory_content (text/markdown)
- estimated_time

#### exercises
- id (PK)
- topic_id (FK)
- type (multiple_choice, fill_blank, matching, etc.)
- content (JSON)
- correct_answer (JSON)
- difficulty
- order

#### user_progress
- id (PK)
- user_id (FK)
- topic_id (FK)
- completed (boolean)
- score (int)
- attempts (int)
- completed_at

#### vocabulary
- id (PK)
- word
- translation
- level_id (FK)
- examples (JSON)
- audio_url
- image_url

#### user_vocabulary
- id (PK)
- user_id (FK)
- word_id (FK)
- next_review (timestamp)
- interval (int, FSRS)
- ease_factor (float, FSRS)
- repetitions (int)
- last_reviewed

#### audio_resources
- id (PK)
- topic_id (FK, nullable)
- level_id (FK)
- title
- url (S3)
- transcript (text)
- duration (seconds)
- difficulty

#### comments
- id (PK)
- user_id (FK)
- topic_id (FK)
- content
- created_at
- updated_at
- is_moderated

#### study_buddy_requests
- id (PK)
- user_id (FK)
- level_id (FK)
- contact_info
- message
- created_at
- is_active

#### level_tests
- id (PK)
- level_id (FK)
- name
- description
- duration (minutes)

#### level_test_questions
- id (PK)
- test_id (FK)
- type
- content (JSON)
- correct_answer (JSON)
- skill (grammar, vocabulary, listening, writing)

#### user_test_attempts
- id (PK)
- user_id (FK)
- test_id (FK)
- score
- max_score
- answers (JSON)
- started_at
- completed_at

#### achievements
- id (PK)
- name
- description
- icon
- condition (JSON)

#### user_achievements
- id (PK)
- user_id (FK)
- achievement_id (FK)
- unlocked_at

### Индексы
- users: email, current_level_id
- user_progress: user_id, topic_id, completed
- user_vocabulary: user_id, next_review
- comments: topic_id, created_at
- user_test_attempts: user_id, test_id, completed_at

### Партиционирование
- user_progress: по user_id (если много пользователей)
- comments: по created_at (по месяцам/годам)
- user_test_attempts: по created_at

---

## 🚀 Deployment (Деплой)

### VPS конфигурация

#### Минимальные требования
- 4GB RAM
- 2 CPU cores
- 50GB storage
- Ubuntu 22.04 LTS

#### Docker Compose структура
```yaml
services:
  nginx:        # Reverse proxy + SSL
  frontend:     # Next.js SSR
  backend:      # FastAPI
  postgres:     # PostgreSQL
  redis:        # Cache + Celery broker
  celery:       # Background tasks
```

#### CI/CD Pipeline (GitHub Actions)
1. Trigger: push to main branch
2. Build Docker images (frontend + backend)
3. Run tests
4. Push images to GitHub Container Registry
5. SSH to VPS
6. Pull new images
7. Run `docker-compose up -d`
8. Health check

#### Secrets (GitHub Secrets)
- VPS_SSH_KEY
- VPS_HOST
- DATABASE_URL
- OPENROUTER_API_KEY
- GOOGLE_OAUTH_CLIENT_ID
- GOOGLE_OAUTH_CLIENT_SECRET
- CLOUDFLARE_R2_ACCESS_KEY
- CLOUDFLARE_R2_SECRET_KEY
- JWT_SECRET_KEY
- SENTRY_DSN

#### Nginx конфигурация
- Reverse proxy для frontend (port 3000)
- Reverse proxy для backend (port 8000)
- SSL через Let's Encrypt (Certbot)
- HTTPS редирект
- Gzip compression
- Static files caching

#### Backup стратегия
- PostgreSQL: pg_dump ежедневно → Cloudflare R2
- Docker volumes: rsync еженедельно
- Автоматизация через Celery periodic tasks

---

## 🎯 Onboarding Flow (Первый вход)

1. **Регистрация** (email + password или Google OAuth)
2. **Email подтверждение** (если email/password)
3. **Тест на определение уровня** (обязательный)
4. **Результаты теста** (определение уровня A1-C2)
5. **Туториал по платформе** (интерактивный walkthrough)
6. **Выбор первой темы** (на основе определенного уровня)
7. **Начало обучения**

---

## 📅 План разработки (Timeline)

### Этап 1: Backend API + Database
- Настройка проекта (FastAPI + SQLAlchemy)
- Модели базы данных
- Alembic миграции
- Базовые CRUD endpoints

### Этап 2: Frontend базовый
- Настройка Next.js (App Router)
- Tailwind + shadcn/ui
- Базовая структура страниц
- Zustand store

### Этап 3: Authentication
- JWT токены
- Email/Password регистрация и вход
- Google OAuth
- Middleware для защиты роутов

### Этап 4: Контент (Scraping + Admin)
- Web scraping скрипты
- Admin panel (CMS)
- Загрузка контента в БД
- Валидация данных

### Этап 5: Обучение (Теория + Упражнения)
- Страницы тем (theory)
- Компоненты упражнений (все типы)
- Проверка ответов
- Сохранение прогресса

### Этап 6: Vocabulary + Spaced Repetition
- FSRS алгоритм
- Карточки (flashcards)
- Раздел Vocabulary Practice
- Отслеживание прогресса

### Этап 7: Аудирование
- Аудиоплеер (Howler.js)
- Интерактивные транскрипты
- Вопросы после прослушивания
- Загрузка аудио в Cloudflare R2

### Этап 8: Тесты на уровень
- Создание тестов (пул вопросов)
- Страница прохождения теста
- Подсчет результатов
- Определение уровня

### Этап 9: Социальные функции
- Комментарии под темами
- Study buddy (заявки)
- Публичные профили
- Sharing прогресса

### Этап 10: Личный кабинет + Метрики
- Dashboard с метриками
- Графики (Recharts)
- Heatmap активности
- Рекомендации

### Этап 11: AI интеграция
- OpenRouter API
- Объяснение ошибок
- Рекомендации аудирования
- Модерация комментариев

### Этап 12: Deployment
- Docker + Docker Compose
- GitHub Actions CI/CD
- Настройка VPS
- Nginx + SSL
- Мониторинг (Sentry, UptimeRobot)

---

## 📝 Правила взаимодействия при разработке

# ═══════════════════════════════════════════════════════════════════
# ⚠️⚠️⚠️ КРИТИЧЕСКИ ВАЖНО - ЧИТАТЬ ОБЯЗАТЕЛЬНО ⚠️⚠️⚠️
# ═══════════════════════════════════════════════════════════════════

## 🚨 ГЛАВНОЕ ПРАВИЛО 🚨

**НИЧЕГО НЕ ДЕЛАЙ БЕЗ РАЗРЕШЕНИЯ!**

**ТЫ НЕ МОЖЕШЬ:**
- ❌ Создавать файлы без явной просьбы
- ❌ Редактировать файлы без явной просьбы
- ❌ Писать код без явной просьбы
- ❌ Делать несколько шагов подряд
- ❌ Принимать решения самостоятельно

**ТЫ МОЖЕШЬ ТОЛЬКО:**
- ✅ Ждать команды от пользователя
- ✅ Когда получил команду - сделать ОДИН шаг
- ✅ Показать код с ПОЛНЫМ объяснением
- ✅ Спросить "Всё понятно? Продолжаем?"
- ✅ Ждать следующей команды

**ЗАПРЕЩЕНО ПИСАТЬ КОД БЕЗ ОБЪЯСНЕНИЯ!**

Каждый раз когда ты пишешь код, ты ОБЯЗАН:
1. Сказать ЧТО ты делаешь
2. Показать КОД
3. Дать ДЕТАЛЬНОЕ ОБЪЯСНЕНИЕ
4. ОСТАНОВИТЬСЯ и ждать подтверждения

**НЕ ПИШИ НЕСКОЛЬКО ФАЙЛОВ ПОДРЯД БЕЗ ОБЪЯСНЕНИЙ!**
**ОДИН ШАГ = ОДИН ФАЙЛ/КОМПОНЕНТ + ПОЛНОЕ ОБЪЯСНЕНИЕ + ОЖИДАНИЕ**

# ═══════════════════════════════════════════════════════════════════

### ⚠️ ВАЖНО: Стандарт общения

#### Формат работы
1. **Поэтапная разработка:** движемся строго по плану, шаг за шагом
2. **Код + Объяснение:** каждый блок кода сопровождается детальным объяснением
3. **Обучающий подход:** все объяснения максимально подробные (для обучения)
4. **ОДИН ШАГ ЗА РАЗ:** не делай несколько шагов подряд без объяснений
5. **Best Practices:** всегда используй лучшие практики индустрии и объясняй почему выбрано именно это решение

#### Структура ответа (СТРОГО СЛЕДОВАТЬ!)
```
1. Что делаем на этом шаге (краткое описание)
2. Код (полный, готовый к использованию)
3. Детальное объяснение:
   - Что делает этот код
   - Для чего нужен каждый компонент
   - Как это работает
   - Почему выбран именно такой подход (Best Practice)
   - Какие альтернативы существуют и почему они НЕ выбраны
   - Связь с другими частями проекта
4. Вопрос: "Всё понятно? Готов двигаться дальше?"
```

#### Что НЕЛЬЗЯ делать (СТРОГО ЗАПРЕЩЕНО!)
- ❌ Редактировать код без явной просьбы
- ❌ Пропускать объяснения
- ❌ Давать краткие ответы без деталей
- ❌ Предлагать альтернативы без запроса
- ❌ Менять архитектурные решения самостоятельно
- ❌❌❌ **СОЗДАВАТЬ НЕСКОЛЬКО ФАЙЛОВ ПОДРЯД БЕЗ ОБЪЯСНЕНИЙ** ❌❌❌
- ❌❌❌ **ПИСАТЬ КОД И СРАЗУ ПЕРЕХОДИТЬ К СЛЕДУЮЩЕМУ ШАГУ** ❌❌❌

#### Что НУЖНО делать (ОБЯЗАТЕЛЬНО!)
- ✅ Выдавать готовый код
- ✅ Давать максимально подробные объяснения
- ✅ Объяснять "почему", "для чего", "как"
- ✅ Двигаться поэтапно
- ✅ Ждать подтверждения перед переходом к следующему шагу
- ✅✅✅ **ОДИН ШАГ = ОДИН ФАЙЛ + ОБЪЯСНЕНИЕ + ОЖИДАНИЕ** ✅✅✅
- ✅ **ИСПОЛЬЗОВАТЬ BEST PRACTICES:** всегда применять лучшие практики индустрии
- ✅ **ОБЪЯСНЯТЬ ВЫБОР:** почему выбрано именно это решение, а не альтернативное

#### Пример правильного ответа

**Шаг 1: Создание модели User**

```python
# backend/app/models/user.py
from sqlalchemy import Column, Integer, String, DateTime, Boolean
from sqlalchemy.sql import func
from app.core.database import Base

class User(Base):
    __tablename__ = "users"
    
    id = Column(Integer, primary_key=True, index=True)
    email = Column(String, unique=True, index=True, nullable=False)
    password_hash = Column(String, nullable=False)
    name = Column(String, nullable=True)
    is_active = Column(Boolean, default=True)
    created_at = Column(DateTime(timezone=True), server_default=func.now())
```

**Объяснение:**

**Что делает этот код:**
Создает модель User для SQLAlchemy, которая представляет таблицу users в PostgreSQL.

**Для чего нужен каждый компонент:**
- `Base` - базовый класс SQLAlchemy, от которого наследуются все модели
- `__tablename__` - имя таблицы в базе данных
- `Column` - определяет колонку таблицы
- `Integer, String, DateTime, Boolean` - типы данных колонок
- `primary_key=True` - делает id первичным ключом
- `index=True` - создает индекс для быстрого поиска
- `unique=True` - гарантирует уникальность email
- `nullable=False` - поле обязательно для заполнения
- `server_default=func.now()` - автоматически устанавливает текущее время при создании

**Как это работает:**
SQLAlchemy использует эту модель для генерации SQL запросов. Когда мы создаем пользователя через `User(email="...", password_hash="...")`, SQLAlchemy автоматически преобразует это в INSERT запрос в PostgreSQL.

**Почему выбран именно такой подход:**
- Индексы на email и id ускоряют поиск пользователей
- unique на email предотвращает дубликаты
- DateTime с timezone обеспечивает корректную работу с временными зонами
- server_default вместо default гарантирует, что время устанавливается на уровне БД

**Альтернативы и почему они НЕ выбраны:**
- `default=datetime.now()` - плохая практика, т.к. время устанавливается при импорте модуля, а не при создании записи
- Хранение времени без timezone - может привести к проблемам при работе с пользователями из разных часовых поясов
- Отсутствие индексов - замедлит поиск пользователей при росте базы данных

**Связь с другими частями:**
Эта модель будет использоваться в:
- Authentication (проверка email/password)
- User endpoints (CRUD операции)
- Relationships с другими таблицами (user_progress, comments, etc.)

---

### Процесс разработки

#### Начало работы
1. **Проверить TODO список** (в конце документа) - определить текущий этап
2. Определяем текущий этап из Timeline
3. Разбиваем этап на подзадачи
4. Выполняем подзадачи последовательно
5. **Отмечаем выполненные задачи** в TODO списке

#### Продолжение работы
- **ВСЕГДА** сначала смотри TODO список в конце документа
- Определи какие задачи уже выполнены (✅)
- Определи текущую задачу (🔄)
- Продолжай с текущей задачи или переходи к следующей

#### Завершение шага
После каждого шага спрашиваю: "Готов двигаться дальше?"
Жду подтверждения перед следующим шагом.

#### Вопросы и уточнения
Если что-то непонятно - спрашивай сразу.
Если нужно изменить код - скажи явно что именно.

---

## 🎓 Обучающие материалы (для разработчика)

### Полезные ссылки

#### Backend
- FastAPI: https://fastapi.tiangolo.com/
- SQLAlchemy: https://docs.sqlalchemy.org/
- Pydantic: https://docs.pydantic.dev/
- Celery: https://docs.celeryq.dev/

#### Frontend
- Next.js: https://nextjs.org/docs
- React: https://react.dev/
- Tailwind CSS: https://tailwindcss.com/docs
- shadcn/ui: https://ui.shadcn.com/
- Zustand: https://zustand-demo.pmnd.rs/
- TanStack Query: https://tanstack.com/query/latest

#### Database
- PostgreSQL: https://www.postgresql.org/docs/

#### Deployment
- Docker: https://docs.docker.com/
- Nginx: https://nginx.org/en/docs/

#### AI
- OpenRouter: https://openrouter.ai/docs

---

## 📊 Метрики успеха (KPI)

### Для MVP
- Количество зарегистрированных пользователей
- Retention rate (возвращаемость)
- Среднее время на платформе
- Количество завершенных тем
- Количество пройденных тестов
- Streak (средний и максимальный)

### Для будущего
- Conversion rate (free → paid)
- Churn rate
- NPS (Net Promoter Score)
- Прогресс пользователей (A1 → A2 → ... → C2)

---

## 🔮 Будущие фичи (Post-MVP)

- Разговорная практика с AI (speech-to-text + text-to-speech)
- Мобильное приложение (React Native)
- Интеграция с внешними словарями (Cambridge, Oxford)
- Подкасты и видео материалы
- Групповые занятия (live sessions)
- Сертификаты по завершению уровней
- Marketplace для преподавателей (создание контента)
- Gamification 2.0 (badges, quests, tournaments)
- AI генерация персонализированных упражнений
- Интеграция с Anki (экспорт карточек)

---

## 📞 Контакты и поддержка

- GitHub: (будет добавлено)
- Email: (будет добавлено)
- Discord: (будет добавлено)

---

## 📄 Лицензия

(будет определено позже)

---

**Дата создания:** 2026-04-01
**Версия документа:** 1.0
**Статус проекта:** Planning → Development

---

## ✅ Чеклист готовности к разработке

- [x] Определены технологии
- [x] Спроектирована архитектура
- [x] Определен функционал
- [x] Создан план разработки
- [x] Установлены правила взаимодействия
- [ ] Настроено окружение разработки
- [ ] Создан репозиторий
- [ ] Начата разработка

---

**Следующий шаг:** Начало разработки - Этап 1 (Backend API + Database)

---

## 📋 TODO: Этапы разработки

### Легенда
- ⬜ Не начато
- 🔄 В процессе
- ✅ Завершено

---

### Этап 1: Backend API + Database ⬜
- ⬜ 1.1. Настройка структуры проекта (backend/)
  - ⬜ Создание директорий (app/, alembic/, tests/)
  - ⬜ Создание requirements.txt
  - ⬜ Настройка виртуального окружения
- ⬜ 1.2. Настройка FastAPI
  - ⬜ Создание app/main.py (точка входа)
  - ⬜ Настройка CORS
  - ⬜ Настройка middleware
- ⬜ 1.3. Настройка базы данных
  - ⬜ Создание app/core/database.py (подключение к PostgreSQL)
  - ⬜ Создание app/core/config.py (настройки из .env)
  - ⬜ Настройка Alembic для миграций
- ⬜ 1.4. Создание моделей базы данных
  - ⬜ app/models/user.py
  - ⬜ app/models/level.py
  - ⬜ app/models/module.py
  - ⬜ app/models/topic.py
  - ⬜ app/models/exercise.py
  - ⬜ app/models/user_progress.py
  - ⬜ app/models/vocabulary.py
  - ⬜ app/models/user_vocabulary.py
  - ⬜ app/models/audio_resource.py
  - ⬜ app/models/comment.py
  - ⬜ app/models/study_buddy_request.py
  - ⬜ app/models/level_test.py
  - ⬜ app/models/level_test_question.py
  - ⬜ app/models/user_test_attempt.py
  - ⬜ app/models/achievement.py
  - ⬜ app/models/user_achievement.py
- ⬜ 1.5. Создание Pydantic схем
  - ⬜ app/schemas/user.py
  - ⬜ app/schemas/level.py
  - ⬜ app/schemas/topic.py
  - ⬜ app/schemas/exercise.py
  - ⬜ (остальные схемы по аналогии)
- ⬜ 1.6. Создание первой миграции
  - ⬜ alembic revision --autogenerate
  - ⬜ alembic upgrade head
- ⬜ 1.7. Базовые CRUD endpoints
  - ⬜ app/api/endpoints/users.py
  - ⬜ app/api/endpoints/levels.py
  - ⬜ app/api/endpoints/topics.py

---

### Этап 2: Frontend базовый ⬜
- ⬜ 2.1. Настройка Next.js проекта
  - ⬜ npx create-next-app@latest
  - ⬜ Настройка TypeScript
  - ⬜ Настройка Tailwind CSS
- ⬜ 2.2. Установка shadcn/ui
  - ⬜ npx shadcn-ui@latest init
  - ⬜ Добавление базовых компонентов (Button, Card, Input)
- ⬜ 2.3. Настройка Zustand
  - ⬜ Создание store/authStore.ts
  - ⬜ Создание store/userStore.ts
- ⬜ 2.4. Настройка TanStack Query
  - ⬜ Создание lib/queryClient.ts
  - ⬜ Обертка провайдера в app/layout.tsx
- ⬜ 2.5. Настройка Axios
  - ⬜ Создание lib/axios.ts (базовая конфигурация)
  - ⬜ Настройка interceptors
- ⬜ 2.6. Базовая структура страниц
  - ⬜ app/page.tsx (главная)
  - ⬜ app/dashboard/page.tsx
  - ⬜ app/learn/page.tsx
  - ⬜ app/vocabulary/page.tsx
  - ⬜ app/listening/page.tsx

---

### Этап 3: Authentication ⬜
- ⬜ 3.1. Backend: JWT токены
  - ⬜ app/core/security.py (создание/проверка токенов)
  - ⬜ app/core/deps.py (dependency для защиты роутов)
- ⬜ 3.2. Backend: Email/Password
  - ⬜ app/api/endpoints/auth.py (register, login, refresh)
  - ⬜ Password hashing (passlib + bcrypt)
- ⬜ 3.3. Backend: Google OAuth
  - ⬜ Настройка OAuth клиента
  - ⬜ app/api/endpoints/oauth.py
- ⬜ 3.4. Frontend: Auth UI
  - ⬜ app/auth/login/page.tsx
  - ⬜ app/auth/register/page.tsx
  - ⬜ components/auth/LoginForm.tsx
  - ⬜ components/auth/RegisterForm.tsx
- ⬜ 3.5. Frontend: Auth логика
  - ⬜ Сохранение токенов в localStorage
  - ⬜ Middleware для защиты роутов
  - ⬜ Автоматический refresh токенов

---

### Этап 4: Контент (Scraping + Admin) ⬜
- ⬜ 4.1. Web scraping скрипты
  - ⬜ backend/scripts/scrapers/bbc_scraper.py
  - ⬜ backend/scripts/scrapers/british_council_scraper.py
  - ⬜ backend/scripts/scrapers/cambridge_scraper.py
- ⬜ 4.2. Валидация контента
  - ⬜ Pydantic схемы для scraped данных
  - ⬜ AI проверка качества (OpenRouter)
- ⬜ 4.3. Admin Panel Backend
  - ⬜ app/api/endpoints/admin/content.py
  - ⬜ app/api/endpoints/admin/scraping.py
  - ⬜ app/api/endpoints/admin/moderation.py
- ⬜ 4.4. Admin Panel Frontend
  - ⬜ app/admin/page.tsx
  - ⬜ app/admin/content/page.tsx
  - ⬜ app/admin/scraping/page.tsx
  - ⬜ components/admin/ContentEditor.tsx
  - ⬜ components/admin/ScrapingControl.tsx

---

### Этап 5: Обучение (Теория + Упражнения) ⬜
- ⬜ 5.1. Backend: Topics API
  - ⬜ GET /topics/{id} (получение темы с теорией)
  - ⬜ GET /topics/{id}/exercises (получение упражнений)
  - ⬜ POST /exercises/{id}/submit (проверка ответа)
- ⬜ 5.2. Frontend: Страница темы
  - ⬜ app/learn/[levelId]/[topicId]/page.tsx
  - ⬜ components/learn/TheoryView.tsx
  - ⬜ components/learn/ExerciseList.tsx
- ⬜ 5.3. Frontend: Компоненты упражнений
  - ⬜ components/exercises/MultipleChoice.tsx
  - ⬜ components/exercises/FillInBlanks.tsx
  - ⬜ components/exercises/Matching.tsx
  - ⬜ components/exercises/TrueFalse.tsx
  - ⬜ components/exercises/Ordering.tsx
  - ⬜ components/exercises/Writing.tsx
- ⬜ 5.4. Сохранение прогресса
  - ⬜ Backend: POST /progress (сохранение прогресса)
  - ⬜ Frontend: автоматическое сохранение

---

### Этап 6: Vocabulary + Spaced Repetition ⬜
- ⬜ 6.1. Backend: FSRS алгоритм
  - ⬜ app/services/fsrs.py (реализация алгоритма)
  - ⬜ app/api/endpoints/vocabulary.py
- ⬜ 6.2. Backend: Vocabulary API
  - ⬜ GET /vocabulary/due (слова для повторения)
  - ⬜ POST /vocabulary/{id}/review (отметка повторения)
- ⬜ 6.3. Frontend: Vocabulary страница
  - ⬜ app/vocabulary/page.tsx
  - ⬜ components/vocabulary/Flashcard.tsx
  - ⬜ components/vocabulary/ProgressStats.tsx

---

### Этап 7: Аудирование ⬜
- ⬜ 7.1. Backend: Audio API
  - ⬜ GET /audio (список аудио)
  - ⬜ GET /audio/{id} (детали аудио + транскрипт)
  - ⬜ POST /audio/{id}/answer (проверка ответов)
- ⬜ 7.2. Cloudflare R2 интеграция
  - ⬜ app/services/storage.py (загрузка/получение файлов)
- ⬜ 7.3. Frontend: Audio плеер
  - ⬜ app/listening/page.tsx
  - ⬜ components/listening/AudioPlayer.tsx (Howler.js)
  - ⬜ components/listening/InteractiveTranscript.tsx
  - ⬜ components/listening/ComprehensionQuestions.tsx

---

### Этап 8: Тесты на уровень ⬜
- ⬜ 8.1. Backend: Tests API
  - ⬜ GET /tests/level-assessment (получение теста)
  - ⬜ POST /tests/submit (отправка ответов)
  - ⬜ GET /tests/results/{id} (результаты)
- ⬜ 8.2. Frontend: Test UI
  - ⬜ app/test/level-assessment/page.tsx
  - ⬜ components/test/TestQuestion.tsx
  - ⬜ components/test/TestResults.tsx
  - ⬜ components/test/TestTimer.tsx

---

### Этап 9: Социальные функции ⬜
- ⬜ 9.1. Backend: Comments API
  - ⬜ GET /topics/{id}/comments
  - ⬜ POST /topics/{id}/comments
  - ⬜ Модерация (blacklist слов)
- ⬜ 9.2. Backend: Study Buddy API
  - ⬜ GET /study-buddy/requests
  - ⬜ POST /study-buddy/requests
- ⬜ 9.3. Backend: Profiles API
  - ⬜ GET /users/{id}/profile (публичный профиль)
  - ⬜ GET /leaderboard (рейтинг)
- ⬜ 9.4. Frontend: Social UI
  - ⬜ components/social/CommentSection.tsx
  - ⬜ app/study-buddy/page.tsx
  - ⬜ app/profile/[userId]/page.tsx
  - ⬜ app/leaderboard/page.tsx

---

### Этап 10: Личный кабинет + Метрики ⬜
- ⬜ 10.1. Backend: Analytics API
  - ⬜ GET /dashboard/stats (все метрики)
  - ⬜ GET /dashboard/heatmap (активность)
  - ⬜ GET /dashboard/recommendations (AI рекомендации)
- ⬜ 10.2. Frontend: Dashboard
  - ⬜ app/dashboard/page.tsx
  - ⬜ components/dashboard/ProgressChart.tsx (Recharts)
  - ⬜ components/dashboard/ActivityHeatmap.tsx
  - ⬜ components/dashboard/SkillRadar.tsx
  - ⬜ components/dashboard/StreakCounter.tsx
  - ⬜ components/dashboard/Recommendations.tsx

---

### Этап 11: AI интеграция ⬜
- ⬜ 11.1. OpenRouter настройка
  - ⬜ app/services/ai.py (клиент OpenRouter)
  - ⬜ Выбор бесплатных моделей
- ⬜ 11.2. AI функции
  - ⬜ Объяснение ошибок (POST /exercises/{id}/explain)
  - ⬜ Рекомендации аудирования (GET /audio/recommendations)
  - ⬜ Модерация комментариев (автоматическая)
  - ⬜ Проверка Writing упражнений

---

### Этап 12: Deployment ⬜
- ⬜ 12.1. Docker
  - ⬜ backend/Dockerfile
  - ⬜ frontend/Dockerfile
  - ⬜ docker-compose.yml (все сервисы)
- ⬜ 12.2. Nginx
  - ⬜ nginx/nginx.conf
  - ⬜ SSL сертификаты (Let's Encrypt)
- ⬜ 12.3. GitHub Actions CI/CD
  - ⬜ .github/workflows/deploy.yml
  - ⬜ Настройка secrets
- ⬜ 12.4. VPS настройка
  - ⬜ Установка Docker на VPS
  - ⬜ Настройка домена (DuckDNS)
  - ⬜ Первый деплой
- ⬜ 12.5. Мониторинг
  - ⬜ Настройка Sentry
  - ⬜ Настройка UptimeRobot
  - ⬜ Настройка логирования

---

**Текущий статус:** ⬜ Не начато
**Следующая задача:** Этап 1.1 - Настройка структуры проекта (backend/)
