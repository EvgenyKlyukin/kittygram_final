# Kittygram

## Project Description
![Static Badge](https://img.shields.io/badge/EvgenyKlyukin-kittygram_final-kittygram_final)
![GitHub top language](https://img.shields.io/github/languages/top/EvgenyKlyukin/kittygram_final)
![GitHub Repo stars](https://img.shields.io/github/stars/EvgenyKlyukin/kittygram_final)
![GitHub issues](https://img.shields.io/github/issues/EvgenyKlyukin/kittygram_final)
![Build Status](https://github.com/EvgenyKlyukin/kittygram_final/actions/workflows/main.yml/badge.svg)

Kittygram is a social network for sharing cat pictures. The project includes:
- Backend on Django (REST API)
- Frontend on React
- PostgreSQL database
- Nginx as a reverse proxy

## Project status
This project was the final assignment in Sprint 17 of Yandex Practicum. The project was completed in May 2025.

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
1. Clone the repository:
```bash
git clone https://github.com/EvgenyKlyukin/kittygram_final.git
cd kittygram_final
```
2. Create a .env file in the project root based on .env.example:
```bash
cp .env.example .env
```
3. Run the project using Docker Compose:
```bash
docker-compose up -d --build
```
4. Apply migrations:
```bash
docker-compose exec backend python manage.py migrate
```
5. Collect static files:
```bash
docker-compose exec backend python manage.py collectstatic
```

## Using

### Configuration
To configure the project, create a .env file with the following variables:
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
The project supports two database management systems:
- **PostgreSQL** (recommended for production)
- **SQLite3** (convenient for local development)

The database type is determined by the USE_SQLITE variable in the .env file:
```ini
# For SQLite usage (set to 'True')
USE_SQLITE=True

# For PostgreSQL usage (set to 'False' or omit the variable)
USE_SQLITE=False
```
When USE_SQLITE=True, the project will use the built-in SQLite3 database. The database file db.sqlite3 will be automatically created in the backend directory.

After the first launch, execute:
```bash
docker-compose exec backend python manage.py migrate
```

### API
The API is available at: /api/

## Tests
To run tests:
```bash
docker-compose exec backend python manage.py test
docker-compose exec frontend npm test
```

## Authors
- [Evgeny Klyukin](https://github.com/EvgenyKlyukin) — lead developer.