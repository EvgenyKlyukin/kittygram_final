# Kittygram

## Project Description
![Static Badge](https://img.shields.io/badge/EvgenyKlyukin-kittygram_final-kittygram_final)
![GitHub top language](https://img.shields.io/github/languages/top/EvgenyKlyukin/kittygram_final)
![GitHub Repo stars](https://img.shields.io/github/stars/EvgenyKlyukin/kittygram_final)
![GitHub issues](https://img.shields.io/github/issues/EvgenyKlyukin/kittygram_final)
![Build Status](https://github.com/EvgenyKlyukin/kittygram_final/actions/workflows/main.yml/badge.svg)

Kittygram - это социальная сеть для обмена фотографиями котиков. Проект включает:
- Бэкенд на Django (REST API)
- Фронтенд на React
- Базу данных PostgreSQL
- Nginx в качестве reverse proxy

## Project status
Данный проект является заключительным в рамках 17 спринт (Yandex Практикум). Проект находится в активной разработке.

## Table of contents
- [Tech stack](#tech-stack)
- [Installation](#installation)
- [Using](#using)
    - [Configuration](#configuration)
    - [Data](#data)
    - [API](#api)
- [Tests](#tests)
- [Authors](#authors)
- [Links](#links)
- [License](#license)

## Tech stack
- **Backend**: Django, Django REST Framework
- **Frontend**: React, JavaScript
- **Database**: PostgreSQL
- **Web server**: Nginx
- **Containerization**: Docker, Docker Compose
- **CI/CD**: GitHub Actions

## Installation
1. Клонируйте репозиторий:
```bash
git clone https://github.com/EvgenyKlyukin/kittygram_final.git
cd kittygram_final
```
2. Создайте файл .env в корне проекта на основе .env.example:
```bash
cp .env.example .env
```
3. Запустите проект с помощью Docker Compose:
```bash
docker-compose up -d --build
```
4. Примените миграции:
```bash
docker-compose exec backend python manage.py migrate
```
5. Соберите статику:
```bash
docker-compose exec backend python manage.py collectstatic
```

## Using

### Configuration
Для настройки проекта создайте файл .env со следующими переменными:
```ini
POSTGRES_DB=postgres_db
POSTGRES_USER=postgres_user
POSTGRES_PASSWORD=postgres_password
DB_NAME=db_name
DB_HOST=db_host
DB_PORT=db_port
SECRET_KEY=secret_key # Django secret key
DEBUG=True
ALLOWED_HOSTS=00.000.00.01,exemple.exp # ip, domain
USE_SQLITE=False
```

### Data
Проект поддерживает работу с двумя типами СУБД:
- **PostgreSQL** (рекомендуется для production)
- **SQLite3** (удобен для локальной разработки)

Тип используемой СУБД определяется переменной USE_SQLITE в файле .env:
```ini
# Для использования SQLite (значение 'True')
USE_SQLITE=True

# Для использования PostgreSQL (значение 'False' или отсутствие переменной)
USE_SQLITE=False
```
При USE_SQLITE=True проект будет использовать встроенную SQLite3 БД. Файл базы данных db.sqlite3 будет создан автоматически в директории backend.

После первого запуска выполните:
```bash
docker-compose exec backend python manage.py migrate
```

### API
API доступно по адресу /api/.

## Tests
Для запуска тестов:
```bash
docker-compose exec backend python manage.py test
docker-compose exec frontend npm test
```

## Authors
- [Evgeny Klyukin](https://github.com/EvgenyKlyukin) — основной разработчик.

## Links
- [Исходный проект на GitHub](https://github.com/yandex-praktikum/kittygram_final)
- [Документация Django](https://docs.djangoproject.com/en/5.2/)